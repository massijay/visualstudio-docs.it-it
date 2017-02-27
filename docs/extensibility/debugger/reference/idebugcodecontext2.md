---
title: "IDebugCodeContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2"
helpviewer_keywords: 
  - "Interfaccia IDebugCodeContext2"
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta la posizione iniziale di un'istruzione di codice.  Per la maggior parte delle architetture in fase di esecuzione corrente, un contesto di codice può essere considerato come un indirizzo in un flusso di esecuzione del programma.  
  
## Sintassi  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## Note per gli implementatori  
 Il motore di debug implementa questa interfaccia per collegare la posizione di un'istruzione di codice in un percorso del documento.  
  
## Note per i chiamanti  
 I metodi in molte interfacce restituiscono questa interfaccia, il più comune [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md).  Viene utilizzato ampiamente con [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) l'interfaccia nonché le informazioni di risoluzione del punto di interruzione.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) in un'interfaccia, l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)|Ottiene il contesto del documento che corrisponde al contesto di codice attivo.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ottiene le informazioni del linguaggio per questo contesto di codice.|  
  
## Note  
 La differenza principale tra un'interfaccia di `IDebugCodeContext2` e [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) un'interfaccia è che `IDebugCodeContext2` istruzione\-è allineato sempre.  Ciò significa che `IDebugCodeContext2` sta puntando sempre all'inizio di un'istruzione, mentre `IDebugMemoryContext2` possibile scegliere qualsiasi byte di memoria nell'architettura della fase di esecuzione.  `IDebugCodeContext2` viene incrementato in base alle istruzioni anziché dalla possibilità di memorizzazione di base \(in genere byte\).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../Topic/IDebugThread2::CanSetNextStatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)   
 [Successivo](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)