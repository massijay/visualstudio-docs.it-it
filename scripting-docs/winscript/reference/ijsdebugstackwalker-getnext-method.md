---
title: "Metodo IJsDebugStackWalker::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugStackWalker::GetNext
Ottiene il frame successivo.  
  
## Sintassi  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### Parametri  
 `ppFrame`  
 \[out\] Oggetto che rappresenta il frame dello stack.  
  
## Valore restituito  
  
## Note  
 Restituisce E\_JsDEBUG\_OUTSIDE\_OF\_VM quando non sono più presenti stack frame da enumerare  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugStackWalker](../../winscript/reference/ijsdebugstackwalker-interface.md)