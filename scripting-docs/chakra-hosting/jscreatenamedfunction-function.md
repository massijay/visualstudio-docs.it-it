---
title: "Funzione JsCreateNamedFunction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 72f40d06-ab82-4fed-a632-68af6b4126c2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione JsCreateNamedFunction
Crea una nuova funzione JavaScript con nome.  
  
## Sintassi  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateNamedFunction(  
   _In_ JsValueRef name,  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### Parametri  
 `name`  
 Nome di questa funzione che verrà usato per la diagnostica e la conversione in stringa.  
  
 `nativeFunction`  
 Metodo da chiamare quando viene richiamata la funzione.  
  
 `callbackState`  
 Stato fornito dall'utente che verrà passato al callback.  
  
 `function`  
 Nuovo oggetto funzione.  
  
## Valore restituito  
  
## Note  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)