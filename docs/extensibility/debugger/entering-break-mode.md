---
title: "Modalit&#224; di interruzione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modalità di interruzione"
  - "debug [Debugging SDK], modalità di interruzione"
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Modalit&#224; di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio seguente viene descritto il processo che si verifica quando un punto di interruzione viene raggiunto dopo aver eseguito una funzione, in esecuzione alla riga di codice sorgente che contiene il cursore in, o in esecuzione a un punto di interruzione.  
  
## Processo in modalità interruzione  
  
1.  Il motore \(DE\) di debug invia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), o qualsiasi altro evento bloccato per visualizzare l'ide a immettere la modalità di interruzione.  
  
2.  Lo SDM ottiene informazioni sullo stack di chiamate del thread, come segue:  
  
    -   [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2:: GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)  
  
    -   [IEnumDebugFrameInfo2:: dopo](../Topic/IEnumDebugFrameInfo2::Next.md)  
  
    -   [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere informazioni di codice sorgente  
  
    -   [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) per ottenere il nome file  
  
    -   [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) per ottenere l'intervallo dell'istruzione  
  
    -   [IDebugStackFrame2:: GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) per ottenere informazioni di memoria  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)