---
title: "IDebugDocumentText::GetLineOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetLineOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetLineOfPosition"
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetLineOfPosition
Restituisce il numero di riga e, facoltativamente, l'offset del carattere nella riga che corrisponde alla posizione del carattere specificata.  
  
## Sintassi  
  
```  
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### Parametri  
 `cCharacterPosition`  
 \[in\] posizione dell'intervallo di posizione del carattere.  
  
 `pcLineNumber`  
 \[out\] numero di riga dell'intervallo.  
  
 `pcCharacterOffsetInLine`  
 \[in, out\] l'offset di carattere dell'intervallo all'interno della riga `pcLineNumber`.  Se questo parametro è `NULL`, il metodo non restituisce un valore.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo restituisce il numero di riga e, facoltativamente, l'offset del carattere nella riga che corrisponde alla posizione del carattere specificata.  
  
## Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)