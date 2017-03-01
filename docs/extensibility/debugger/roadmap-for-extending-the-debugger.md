---
title: Guida di orientamento per l&quot;estensione del Debugger | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 16
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 49df627aa42cd6cc6ac1430e4e68694fa51a2fc1
ms.lasthandoff: 02/22/2017

---
# <a name="roadmap-for-extending-the-debugger"></a>Guida di orientamento per l'estensione del Debugger
Questa documentazione vengono fornite informazioni di Guida e di riferimento per l'estensione di [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] del debugger con il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debug documentazione include esempi e un riferimento completo rappresentativi scenari che illustrano le modalità per personalizzare il debugger.  
  
 Il compilatore e il relativo output determinare ciò che è necessario eseguire per implementare il debug del prodotto. Se il compilatore:  
  
-   Riguarda il sistema operativo nativo di Windows e scrive un. File PDB, eseguire il debug di programmi con il motore di debug di codice nativo (DE), integrata in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Non è necessario implementare un analizzatore DE o un'espressione. L'analizzatore di espressioni viene scritto per la sintassi del linguaggio di programmazione C++.  
  
-   Produce Microsoft intermediate language (MSIL) di output, è possibile eseguire il debug di programmi con il motore di debug di codice gestito, DE, che è anche integrato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pertanto, è necessario implementare solo un analizzatore di espressioni. Un analizzatore di espressioni di esempio viene fornito automaticamente. Per altre informazioni, vedere i seguenti argomenti:  
  
     [Valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [La valutazione delle espressioni](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Valutazione dell'espressione in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Scrittura di un analizzatore di espressioni di Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   È destinato a un proprietario o un altro ambiente di runtime del sistema operativo, è necessario scrivere il proprio DE. Viene fornita un'esercitazione che consente di creare un semplice DE utilizzando ATL COM. Per altre informazioni, vedere i seguenti argomenti:  
  
     [Creazione di un motore di Debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Esercitazione: Creazione di un motore di Debug tramite COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementazione di un fornitore di porta](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
