---
title: "Interfaccia IEnumJsStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Interfaccia IEnumJsStackFrames
Viene implementata dal debugger per fornire la rimozione dello stack in jscript9diag.dll per JavaScript.  
  
## Sintassi  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## Membri  
  
### Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Ottiene il numero specificato di frame.|  
|[Metodo IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Reimposta lo stack frame alla posizione prima del primo elemento.|  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Riferimenti interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)