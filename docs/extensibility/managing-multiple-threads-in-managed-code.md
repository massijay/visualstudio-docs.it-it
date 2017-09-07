---
title: "Procedura: gestione di più thread in codice gestito | Documenti Microsoft"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 21fcc9388b40baa9e003b4beb876ba2f0f23fbaf
ms.contentlocale: it-it
ms.lasthandoff: 09/06/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Procedura: gestione di più thread in codice gestito
Se si dispone di un'estensione di VSPackage gestita che chiama i metodi asincroni o operazioni eseguite su thread diverso dal thread dell'interfaccia utente di Visual Studio, è necessario seguire le linee guida seguenti. Consente di mantenere il thread dell'interfaccia utente reattiva perché non deve essere in attesa di lavoro su un altro thread di completamento. È possibile rendere il codice più efficiente, perché non si dispone di un thread aggiuntivo che occupano spazio dello stack e renderlo più affidabile e facile eseguire il debug per evitare i deadlock e blocchi.  
  
 In generale, è possibile passare dal thread dell'interfaccia utente a un altro thread, o viceversa. Quando il metodo restituisce, il thread corrente è il thread da cui è stata chiamata.  
  
> [!IMPORTANT]
>  Le linee guida seguenti usano le API nel <xref:Microsoft.VisualStudio.Threading> spazio dei nomi, in particolare, la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> classe. Le API in questo spazio dei nomi sono nuove in [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. È possibile ottenere un'istanza di un <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> dal <xref:Microsoft.VisualStudio.Shell.ThreadHelper> proprietà `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Passaggio dal Thread dell'interfaccia utente a un Thread in Background  
  
1.  Se si utilizza il thread dell'interfaccia utente e si desidera eseguire il lavoro asincrono in un thread in background, usare Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  Se si è nel thread UI e si desidera bloccare in modo sincrono durante l'esecuzione di lavoro in un thread in background, usare il <xref:System.Threading.Tasks.TaskScheduler> proprietà `TaskScheduler.Default` all'interno di <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Il passaggio da un Thread in Background nel thread UI  
  
1.  Se si è in un thread in background e si desidera eseguire un'operazione sul thread dell'interfaccia utente, utilizzare <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     È possibile utilizzare il <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> per passare al thread dell'interfaccia utente. Questo metodo invia un messaggio al thread dell'interfaccia utente con la continuazione del metodo asincrono corrente e anche comunica con il resto del framework threading per impostare la priorità corretta ed evitare i deadlock.  
  
     Se il metodo di thread in background non è asincrono e non è possibile apportare asincrona, è comunque possibile utilizzare il `await` sintassi per passare al thread dell'interfaccia utente eseguendo il wrapping del lavoro con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, come nel seguente esempio:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
