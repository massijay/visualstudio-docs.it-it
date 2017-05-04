---
title: "Typedef JsPromiseContinuationCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Typedef JsPromiseContinuationCallback
Callback di continuazione della promessa.  
  
## Sintassi  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Parametri  
 `task`  
  `callbackState`  
  
## Note  
 L'host può specificare un callback di continuazione della promessa in `JsSetPromiseContinuationCallback`. Se uno script crea un'attività da eseguire successivamente, con l'attività verrà chiamato il callback di continuazione della promessa e l'attività dovrà essere inserita in una coda FIFO in modo che venga eseguita al termine dell'esecuzione dello script corrente.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)