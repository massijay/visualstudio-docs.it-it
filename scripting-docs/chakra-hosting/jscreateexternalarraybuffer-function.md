---
title: "Funzione JsCreateExternalArrayBuffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione JsCreateExternalArrayBuffer
Crea un oggetto `ArrayBuffer` JavaScript per accedere alla memoria esterna.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### Parametri  
 `data`  
 Puntatore alla memoria esterna.  
  
 `byteLength`  
 Numero di byte nella memoria esterna.  
  
 `finalizeCallback`  
 Callback per quando l'oggetto viene completato. Può essere Null.  
  
 `callbackState`  
 Stato fornito dall'utente restituito per finalizzare il callback.  
  
 `result`  
 Nuovo oggetto `ArrayBuffer`.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)