---
title: "Interfaccia IDebugStackFrame | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugStackFrame"
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugStackFrame
Rappresenta uno stack frame logico nello stack di thread.  Chiamare il metodo `IDebugStackFrame::QueryInterface` per ottenere l'interfaccia `IDebugExpressionContext`, che consente la valutazione e finestre Espressioni di controllo dell'espressione.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugStackFrame` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Restituisce il contesto di codice corrente associato allo stack frame.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Restituisce una breve descrizione testuale o lunga lo stack frame.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Restituisce una breve descrizione testuale o lunga del linguaggio.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Restituisce il thread associato a questo stack frame.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Restituisce un Visualizzatore proprietà per il frame corrente.|