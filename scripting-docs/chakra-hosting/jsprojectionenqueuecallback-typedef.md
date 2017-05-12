---
title: "Typedef JsProjectionEnqueueCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Typedef JsProjectionEnqueueCallback
Callback dell'applicazione che viene chiamato da JsRT quando un'API di proiezione viene completata su un thread diverso rispetto a quello originale.  
  
## Sintassi  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Parametri  
 `jsCallback`  
 Callback da richiamare sul thread originale.  
  
 `jsContext`  
 Contesto dell'applicazione.  
  
 `callbackState`  
 Contesto JsRT che deve essere passato in `jsCallback`.  
  
## Note  
 Per ricevere i callback, è necessario chiamare JsSetProjectionEnqueueCallback.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)