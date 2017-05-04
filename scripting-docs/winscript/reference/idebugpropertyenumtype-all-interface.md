---
title: "Interfaccia IDebugPropertyEnumType_All | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugPropertyEnumType_All
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Interfaccia IDebugPropertyEnumType_All"
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugPropertyEnumType_All
Le interfacce `IDebugPropertyEnumType` sono definite in modo da poter passare ognuno degli IID come filtro a `IDebugProperty::EnumMembers` come richiedere l'enumeratore appropriato.  
  
## Sintassi  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugPropertyEnumType\_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Restituisce una stringa di testo che descrive il nome|  
  
 Le interfacce seguenti ereditano da `IDebugPropertyEnumType_All`e non dispongono di metodi aggiuntivi.  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## Vedere anche  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)