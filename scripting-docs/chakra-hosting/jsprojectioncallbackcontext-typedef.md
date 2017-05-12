---
title: "Typedef JsProjectionCallbackContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Typedef JsProjectionCallbackContext
Contesto passato nel callback dell'applicazione, JsProjectionEnqueueCallback, da JsRT e quindi passato nuovamente a JsRT nel callback specificato, `JsProjectionCallback`, dall'applicazione nel thread corretto.  
  
## Sintassi  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## Note  
 Per ricevere callback, è necessario chiamare `JsSetProjectionEnqueueCallback`.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)