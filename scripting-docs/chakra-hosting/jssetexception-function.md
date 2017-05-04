---
title: "Funzione JsSetException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetException"
helpviewer_keywords: 
  - "JsSetException (funzione)"
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsSetException
Imposta il runtime del contesto corrente su uno stato di eccezione.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### Parametri  
 `exception`  
 Eccezione JavaScript da impostare per il runtime del contesto corrente.  
  
## Valore restituito  
 `JsNoError` se il motore era impostato su uno stato di eccezione, in caso contrario un codice di errore.  
  
## Note  
 Se il runtime del contesto corrente si trova già in uno stato di eccezione, questa API restituirà `JsErrorInExceptionState`.  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)