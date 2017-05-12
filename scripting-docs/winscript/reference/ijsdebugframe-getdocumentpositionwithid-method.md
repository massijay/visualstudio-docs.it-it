---
title: "Metodo IJsDebugFrame::GetDocumentPositionWithId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithId
apilocation: jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugFrame::GetDocumentPositionWithId
Restituisce la posizione corrente dello stack frame nel documento a livello utente.  
  
## Sintassi  
  
```  
HRESULT GetDocumentPositionWithId(  
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
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)