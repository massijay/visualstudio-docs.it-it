---
title: "Metodo IJsDebugBreakPoint::IsEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugBreakPoint::IsEnabled
Determina se il punto di interruzione è abilitato.  
  
## Sintassi  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### Parametri  
 `pIsEnabled`  
 \[out\] Restituisce true se il punto di interruzione è abilitato. In caso contrario, restituisce false.  
  
## Valore restituito  
  
## Note  
 Restituisce E\_UNEXPECTED se chiamato su un punto di interruzione eliminato.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)