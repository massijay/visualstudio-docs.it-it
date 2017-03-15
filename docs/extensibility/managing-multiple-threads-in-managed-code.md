---
title: "Procedura: gestire più thread in codice gestito | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: 417dc6e5285859424dfa3b482a90f1a141cff163
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Procedura: gestire più thread in codice gestito
Se si dispone di un'estensione VSPackage gestita che chiama i metodi asincroni o di operazioni eseguite su thread diversi da thread dell'interfaccia utente di Visual Studio, è necessario seguire le linee guida indicate di seguito. È possibile mantenere reattivo il thread dell'interfaccia utente perché non deve essere in attesa di lavoro su un altro thread per il completamento. È possibile rendere il codice più efficiente, perché non si dispone di ulteriori thread che occupano spazio dello stack e renderlo più affidabile e facile eseguire il debug per evitare deadlock e blocchi.  
  
 In generale, è possibile passare dal thread dell'interfaccia utente a un altro thread, o viceversa. Quando il metodo termina, il thread corrente è il thread da cui è stato chiamato.  
  
> [!IMPORTANT]
>  Le linee guida seguenti utilizzano le API nello <xref:Microsoft.VisualStudio.Threading>spazio dei nomi, in particolare, la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>classe.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> </xref:Microsoft.VisualStudio.Threading> Le API in questo spazio dei nomi sono una novità in [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. È possibile ottenere un'istanza di un <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>dalla <xref:Microsoft.VisualStudio.Shell.ThreadHelper>proprietà `ThreadHelper.JoinableTaskFactory`.</xref:Microsoft.VisualStudio.Shell.ThreadHelper> </xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Il passaggio da Thread dell'interfaccia utente a un Thread in Background  
  
1.  Se si utilizza il thread dell'interfaccia utente e si desidera eseguire operazioni asincrone in un thread in background, utilizzare Task.Run():  
  
    ```c#  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  Se si utilizza il thread dell'interfaccia utente e si desidera bloccare in modo sincrono durante l'esecuzione di lavoro in un thread in background, utilizzare il <xref:System.Threading.Tasks.TaskScheduler>proprietà `TaskScheduler.Default` all'interno di <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> </xref:System.Threading.Tasks.TaskScheduler>  
  
    ```c#  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Il passaggio da un Thread in Background nel thread UI  
  
1.  Se si dispone di un thread in background e si desidera eseguire un'operazione sul thread dell'interfaccia utente, utilizzare <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>  
  
    ```c#  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     È possibile utilizzare il <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>per passare al thread UI.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Questo metodo invia un messaggio al thread UI con la continuazione del metodo asincrono corrente e inoltre comunica con il resto del framework threading per impostare la priorità corretta ed evitare i deadlock.  
  
     Se il metodo di thread in background non è asincrono e non sarà più possibile renderla asincrona, è comunque possibile utilizzare il `await` sintassi per passare al thread dell'interfaccia utente eseguendo il wrapping del lavoro con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, come nel seguente esempio:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>  
  
    ```c#  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
