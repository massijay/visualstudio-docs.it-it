---
title: "Typedef JsRef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Typedef JsRef
Un riferimento a un oggetto di proprietà del Garbage Collector di Chakra.  
  
## Sintassi  
  
```  
typedef void *JsRef;  
```  
  
## Note  
 Un runtime di Chakra rileverà automaticamente i riferimenti JsRef, purché siano archiviati all'interno di variabili locali o parametri \(ovvero  si trovino nello stack\).  Per archiviare un JsRef in una posizione diversa rispetto allo stack è necessario chiamare JsRef e JsRelease per gestire la durata dell'oggetto. In caso contrario il Garbage Collector potrebbe cancellare l'oggetto dalla memoria mentre è ancora in uso.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)