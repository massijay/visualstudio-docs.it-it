---
title: "Metodo IJsDebugBreakPoint::GetDocumentPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.GetDocumentPosition
apilocation: jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugBreakPoint::GetDocumentPosition
Restituisce la posizione dell'istruzione a cui il punto di interruzione è stato associato.  
  
## Sintassi  
  
```  
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### Parametri  
 `pDocumentId`  
 \[out\] ID univoco di un documento di origine \(puntatore a IDebugDocumentText\).  
  
 `pCharacterOffset`  
 \[out\] Offset del carattere in base zero dall'inizio dello script.  
  
 `pStatementCharCount`  
 \[out\] Lunghezza dell'istruzione corrente, che inizia a \*pCharacterOffset, in caratteri.  
  
## Valore restituito  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)