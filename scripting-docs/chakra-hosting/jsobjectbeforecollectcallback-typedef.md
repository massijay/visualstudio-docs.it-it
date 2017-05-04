---
title: "Typedef JsObjectBeforeCollectCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Typedef JsObjectBeforeCollectCallback
Callback chiamato prima della raccolta di un oggetto.  
  
## Sintassi  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Parametri  
 `ref`  
 Oggetto da raccogliere.  
  
 `callbackState`  
 Stato passato a `JsSetObjectBeforeCollectCallback`.  
  
## Note  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)