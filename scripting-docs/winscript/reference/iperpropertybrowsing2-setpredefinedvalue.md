---
title: "IPerPropertyBrowsing2::SetPredefinedValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.SetPredefinedValue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::SetPredefinedValue"
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::SetPredefinedValue
Imposta il valore della proprietà specificata da `dispID`.  Il valore predefinito è identificato da `dwCookie.`token  
  
## Sintassi  
  
```  
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### Parametri  
 `dispid`  
 \[in\] identificatore di invio di proprietà per il quale un valore predefinito viene impostato.  
  
 `dwCookie`  
 \[in\] token che identifica il valore da impostare.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  
  
## Vedere anche  
 [Interfaccia IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)