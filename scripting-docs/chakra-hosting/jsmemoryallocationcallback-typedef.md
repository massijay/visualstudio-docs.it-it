---
title: "Typedef JsMemoryAllocationCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Typedef JsMemoryAllocationCallback
Routine implementata dall'utente per eventi di allocazione della memoria.  
  
## Sintassi  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### Parametri  
 callbackState  
 Stato passato a JsSetRuntimeMemoryAllocationCallback.  
  
 allocationEvent  
 Tipo di evento di allocazione.  
  
 allocationSize  
 Dimensione dell'allocazione.  
  
## Valore proprietà\/Valore restituito  
 La restituzione di per l'evento JsMemoryAllocate true permette al runtime di procedere con l'allocazione.  La restituzione di false indica che la richiesta di allocazione è stata rifiutata.  Il valore restituito sarà ignorato per gli altri eventi di allocazione.  
  
## Note  
 Usare JsSetRuntimeMemoryAllocationCallback per registrare questo callback.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)