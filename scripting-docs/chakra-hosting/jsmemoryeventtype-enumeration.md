---
title: "Enumerazione JsMemoryEventType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsMemoryEventType"
helpviewer_keywords: 
  - "JsMemoryEventType (enumerazione)"
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Enumerazione JsMemoryEventType
Tipo di evento di callback di allocazione.  
  
## Sintassi  
  
```  
enum JsMemoryEventType;  
```  
  
## Membri  
  
### Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JsMemoryAllocate`|Indica una richiesta di allocazione di memoria.|  
|`JsMemoryFailure`|Indica un evento di allocazione non superato.|  
|`JsMemoryFree`|Indica un evento di liberazione di memoria.|  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)