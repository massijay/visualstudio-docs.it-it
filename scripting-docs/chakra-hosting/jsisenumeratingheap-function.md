---
title: "Funzione JsIsEnumeratingHeap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsEnumeratingHeap"
helpviewer_keywords: 
  - "JsIsEnumeratingHeap (funzione)"
ms.assetid: 5d14518e-3153-43f2-9a9c-068580cbd54f
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsIsEnumeratingHeap
Restituisce un valore che indica se l'heap del contesto corrente viene enumerato.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsIsEnumeratingHeap(  
   _Out_ bool *isEnumeratingHeap  
);  
```  
  
#### Parametri  
 `isEnumeratingHeap`  
 Se l'heap viene enumerato.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata nelle app desktop, ma non nelle app di Windows Store.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)