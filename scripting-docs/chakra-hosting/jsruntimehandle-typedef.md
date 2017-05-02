---
title: "Typedef JsRuntimeHandle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Typedef JsRuntimeHandle
Handle di un runtime Chakra.  
  
## Sintassi  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## Note  
 Ogni runtime Chakra dispone di un motore di esecuzione, di un compilatore JIT e di un heap sottoposto a Garbage Collection indipendenti.  Ogni runtime è quindi completamente isolato dagli altri.  
  
 I runtime possono essere usati su qualsiasi thread, ma in un runtime può essere chiamato un solo thread alla volta.  
  
> [!WARNING]
>  Diversamente dagli altri riferimenti a oggetti nell'API di hosting Chakra, un oggetto JsRuntimeHandle non è sottoposto a Garbage Collection dal momento che contiene già di per sé l'heap sottoposto a Garbage Collection.  Un runtime continuerà a esistere finché non viene chiamato JsDisposeRuntime.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)