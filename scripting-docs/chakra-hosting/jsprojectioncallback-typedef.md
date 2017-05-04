---
title: "Typedef JsProjectionCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Typedef JsProjectionCallback
Callback JsRT che deve essere chiamato con il contesto passato a `JsProjectionEnqueueCallback` nel thread corretto.  
  
## Sintassi  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### Parametri  
 `jsContext`  
 Per ricevere callback, è necessario chiamare `JsSetProjectionEnqueueCallback`.  
  
## Note  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)