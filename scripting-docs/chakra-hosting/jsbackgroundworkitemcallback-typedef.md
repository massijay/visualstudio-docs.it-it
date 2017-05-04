---
title: "Typedef JsBackgroundWorkItemCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Typedef JsBackgroundWorkItemCallback
Callback di un elemento di lavoro in background.  
  
## Sintassi  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### Parametri  
 callbackData  
 Argomento di dati passato al servizio thread.  
  
## Note  
 Questo argomento viene passato al servizio thread dell'host \(se fornito\) per consentire all'host di richiamare il callback dell'elemento di lavoro sul thread in background scelto.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)