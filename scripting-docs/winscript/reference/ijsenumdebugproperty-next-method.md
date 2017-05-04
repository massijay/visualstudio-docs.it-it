---
title: "Metodo IJsEnumDebugProperty::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsEnumDebugProperty.Next
apilocation: jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsEnumDebugProperty::Next
Legge le proprietà di questo oggetto.  
  
## Sintassi  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### Parametri  
 `count`  
 \[in\] Numero di proprietà da leggere.  
  
 `ppDebugProperty`  
 \[out\] Oggetto che rappresenta il browser delle proprietà.  
  
 `pActualCount`  
 \[out\] Numero effettivo delle proprietà dell'oggetto.  
  
## Valore restituito  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)