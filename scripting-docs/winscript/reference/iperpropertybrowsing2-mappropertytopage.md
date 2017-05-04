---
title: "IPerPropertyBrowsing2::MapPropertyToPage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.MapPropertyToPage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::MapPropertyToPage"
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::MapPropertyToPage
Restituisce il CLSID della pagina delle proprietà che può essere utilizzata per modificare questa proprietà.  
  
## Sintassi  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### Parametri  
 `dispid`  
 \[in\] inviare l'identificatore della proprietà di interesse.  
  
 `pClsidPropPage`  
 \[out\] puntatore al CLSID che identifica la pagina delle proprietà associata alla proprietà.  Se il metodo ha esito negativo, \*`pClsidPropPage` è impostato su CLSID\_NULL.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  
  
## Vedere anche  
 [Interfaccia IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)