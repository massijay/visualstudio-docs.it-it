---
title: "Valutazione dello Stack di chiamate | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "valutazione dello stack di chiamate [debug SDK], debug"
  - "stack di chiamate, valutazione"
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Valutazione dello Stack di chiamate
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Per visualizzare gli stack frame dello stack di chiamate in modalità di interruzione, è necessario implementare [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) il metodo.  
  
## metodi per la valutazione  
 Per un modulo di debug semplice \(DE\), potrebbe essere presente uno stack frame.  Per esaminare lo stack frame in modalità di interruzione, è necessario distribuire i seguenti metodi di [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|ottiene il contesto di codice per uno stack frame.  Il contesto di codice rappresenta il puntatore all'istruzione corrente in uno stack frame.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto del documento per uno stack frame.  Il contesto del documento rappresenta la posizione corrente nel codice sorgente per uno stack frame.  Obbligatorio per visualizzare il codice sorgente in caso di interruzione in un programma.|  
  
 Questi metodi richiedono l'implementazione di molte interfacce e metodi contesto\-correlati.  Pertanto, è necessario implementare [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) il metodo e i metodi seguenti di [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo dell'istruzione di un contesto del documento.|  
  
 Per enumerare i contesti di codice, è necessario implementare tutti i metodi di [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## Vedere anche  
 [Controllo dell'esecuzione e la valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)