---
title: "IDebugProperty::GetPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetPropertyInfo"
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetPropertyInfo
Ottiene il valore `IDebugProperty` che descrive un metodo o una proprietà indicizzata.  
  
## Sintassi  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGS dwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### Parametri  
 `dwFields`  
 \[in\] specifica le costanti `DBGPROP_INFO_FLAGS` che determinano i campi da compilare nella struttura `DebugPropertyInfo`.  
  
 `nRadix`  
 \[in\] base da utilizzare durante la formattazione delle informazioni numerica.  
  
 `pPropertyInfo`  
 \[out\] restituisce la struttura `DebugPropertyInfo` che descrive la proprietà.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  
  
## Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)