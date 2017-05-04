---
title: "Metodo IJsDebugBreakPoint::Disable | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.Disable
apilocation: jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugBreakPoint::Disable
Disabilita il Punto di interruzione  
  
## Sintassi  
  
```  
HRESULT Disable(void);  
```  
  
## Valore restituito  
  
## Note  
 Restituisce E\_UNEXPECTED se chiamato su un punto di interruzione eliminato.  Restituisce S\_FALSE se chiamato su un punto di interruzione già disabilitato.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)