---
title: "IDebugProperty::EnumMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::EnumMembers"
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::EnumMembers
Enumera i membri di una proprietà.  
  
## Sintassi  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGS dwFieldSpec,  
   UINT nRadix,  
   REFIID refiid,  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### Parametri  
 `dwFieldSpec`  
 \[in\] specifica le costanti `DBGPROP_INFO_FLAGS` che determinano quali campi nelle strutture enumerate le proprietà di debug devono essere riempiti.  
  
 `nRadix`  
 \[in\] base da utilizzare nell'interpretazione delle informazioni numerica.  
  
 `refiid`  
 \[in\] questo IID viene passato per filtrare enumeratore.  L'iid è una delle interfacce `IDebugPropertyEnumType` che ereditano da `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 \[out\] restituisce l'interfaccia `IEnumDebugPropertyInfo` che enumera le proprietà del membro.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  
  
## Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Interfaccia IDebugPropertyEnumType\_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Interfaccia IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)