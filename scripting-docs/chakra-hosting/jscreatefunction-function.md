---
title: "Funzione JsCreateFunction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateFunction"
helpviewer_keywords: 
  - "JsCreateFunction (funzione)"
ms.assetid: b298a96a-5ef7-4203-a8c8-55f9bfc6d2bb
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Funzione JsCreateFunction
Crea una nuova funzione JavaScript.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsCreateFunction(  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### Parametri  
 `nativeFunction`  
 Metodo da chiamare quando viene richiamata la funzione.  
  
 `callbackState`  
 Stato fornito dall'utente passato al callback.  
  
 `function`  
 Nuovo oggetto della funzione.  
  
## Valore restituito  
 Risultato della chiamata, se presente.  
  
## Note  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)