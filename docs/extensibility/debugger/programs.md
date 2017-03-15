---
title: I programmi | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 12
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
ms.openlocfilehash: 982d966208433905115e76a36d358c656005e3d3
ms.lasthandoff: 02/22/2017

---
# <a name="programs"></a>Programs
In termini di architettura debugger, un **programma**:  
  
-   È un contenitore per un set di thread e un set di moduli. Un programma non dispone di alcun singolo analogia nel sistema operativo Windows.  
  
     Un programma è un tipo di processo secondario. Ad esempio, quando si esegue il debug di un sito Web, uno script può essere considerato un programma. Sebbene uno script viene eseguito nel processo del motore di scripting, indipendente da altri script, dispone anche di un proprio set di thread. Un motore di debug (DE) viene associato a un programma e non a un processo o un thread.  
  
-   Consente di identificare se stesso e il processo è in esecuzione in e deve essere collegata a scollegati da e descrivere DE creato, se presente. Un programma può eseguire, arrestare, continuare e terminato.  
  
-   Possibile enumerare tutti i thread. Un programma può inoltre fornire il proprio flusso disassembly e possibile enumerare tutti i contesti di codice di una posizione di documento specificato.  
  
-   È rappresentato da un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaccia, creata prima il programma viene collegato o come parte del processo di collegamento, a seconda dell'implementazione. Quando una porta enumera i programmi di un processo, ogni programma è stato creato in base a un corrispondente [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia passata come argomento di [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Mentre i motori di debug anche creare `IDebugProgram2` interfacce per rappresentare i programmi, questi programmi non vengono create in base a un nodo di programma. Il `IDebugProgramNode2` interfacce create da un DE vengono utilizzate per il debug effettivo, mentre quelli creati da una porta sono utilizzati solo per individuare quali programmi sono in esecuzione in un processo.  
  
## <a name="see-also"></a>Vedere anche  
 [Processi](../../extensibility/debugger/processes.md)   
 [Nodi di programma](../../extensibility/debugger/program-nodes.md)   
 [Moduli](../../extensibility/debugger/modules.md)   
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Il motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Posizione documento](../../extensibility/debugger/document-position.md)   
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
