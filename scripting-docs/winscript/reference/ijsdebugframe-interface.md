---
title: "Interfaccia IJsDebugFrame | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Interfaccia IJsDebugFrame
Rappresenta uno stack frame.  
  
## Sintassi  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## Membri  
  
### Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugFrame::Evaluate](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Valutare un'espressione nel contesto di questo stack frame.|  
|[Metodo IJsDebugFrame::GetDebugProperty](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Restituisce un visualizzatore proprietà per questo stack frame.|  
|[Metodo IJsDebugFrame::GetDocumentPositionWithId](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Restituisce la posizione corrente dello stack frame nel documento a livello utente.|  
|[Metodo IJsDebugFrame::GetDocumentPositionWithName](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Restituisce la posizione corrente dello stack frame nel documento a livello utente.|  
|[Metodo IJsDebugFrame::GetName](../../winscript/reference/ijsdebugframe-getname-method.md)|Ottiene il nome descrittivo dell'utente dello stack frame.|  
|[Metodo IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Ottiene l'indirizzo di ritorno inserito "all'inizio" \(vedere GetStackRange\) del frame.|  
|[Metodo IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Restituisce l'intervallo di indirizzi assoluti dello stack frame JavaScript logico.|  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Riferimenti interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)