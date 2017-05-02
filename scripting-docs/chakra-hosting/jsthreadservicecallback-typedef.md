---
title: "Typedef JsThreadServiceCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Typedef JsThreadServiceCallback
Callback del servizio thread.  
  
## Sintassi  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### Parametri  
 callback  
 Callback per l'elemento di lavoro in background.  
  
 callbackData  
 Argomento di dati da passare al callback.  
  
## Note  
 L'host può specificare un servizio thread in background quando si chiama JsCreateRuntime.  Se specificato, gli elementi di lavoro in background verranno passati all'host con questo callback.  È previsto che l'host inizi immediatamente l'esecuzione dell'elemento di lavoro in background e che restituisca true o false. Il runtime gestirà l'elemento di lavoro nel thread.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)