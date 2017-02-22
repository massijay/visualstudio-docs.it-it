---
title: "IEnumDebugThreads2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2"
helpviewer_keywords: 
  - "IEnumDebugThreads2"
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo interfac enumera i thread in esecuzione nella sessione di debug corrente.  
  
## Sintassi  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per rappresentare un elenco di thread in un programma.  
  
## Note per i chiamanti  
 Chiamare [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i thread in tutti i programmi in esecuzione in un processo.  Chiamare [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) per ottenere questa interfaccia che rappresenta un elenco di thread in esecuzione in un programma.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IEnumDebugThreads2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../Topic/IEnumDebugThreads2::Next.md)|Recupera un numero di thread specificato nella sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignora un numero specificato dei thread in una sequenza di enumerazione.|  
|[Reimposta](../Topic/IEnumDebugThreads2::Reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clona](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crea un enumeratore che contiene lo stesso stato dell'enumerazione di quello corrente.|  
|[GetCount](../Topic/IEnumDebugThreads2::GetCount.md)|Ottiene il numero di thread in un enumeratore.|  
  
## Note  
 Visual Studio ottiene in genere questa interfaccia per aggiornare la finestra di **thread** nonché per ottenere il primo thread dell'elenco, per chiamare [Esegui](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md)e [Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Esegui](../../../extensibility/debugger/reference/idebugprocess3-execute.md)