---
title: "Interfaccia IJsDebugStackWalker | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Interfaccia IJsDebugStackWalker
Rappresenta un percorso di chiamate nello stack per un thread specificato.  
  
## Sintassi  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## Membri  
  
### Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Ottiene il frame successivo.|  
  
## Note  
 I percorsi di chiamate nello stack possono essere creati solo quando la destinazione viene interrotta e non sono validi una volta che il processo di destinazione riprende.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Riferimenti interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)