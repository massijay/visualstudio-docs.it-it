---
title: "Funzione JsSetRuntimeBeforeCollectCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeBeforeCollectCallback"
helpviewer_keywords: 
  - "JsSetRuntimeBeforeCollectCallback (funzione)"
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsSetRuntimeBeforeCollectCallback
Imposta una funzione di callback che viene chiamata dal runtime prima dell'operazione di Garbage Collection.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### Parametri  
 `runtime`  
 Runtime per il quale registrare il callback di allocazione.  
  
 `callbackState`  
 Stato fornito dall'utente che verrà passato al callback.  
  
 `beforeCollectCallback`  
 Funzione di callback impostata.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Il callback viene richiamato sul thread in esecuzione nel runtime corrente, quindi l'esecuzione viene bloccata fino al completamento della chiamata.  
  
 Il callback può essere usato dagli host per preparare per la procedura di Garbage Collection.  Ad esempio, rilasciando i riferimenti non necessari agli oggetti Chakra.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)