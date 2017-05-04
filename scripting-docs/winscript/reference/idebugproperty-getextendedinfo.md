---
title: "IDebugProperty::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetExtendedInfo"
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetExtendedInfo
Gets ha esteso le informazioni per la proprietà.  
  
## Sintassi  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### Parametri  
 `cInfos`  
 \[in\] numero di informazioni estese oggetti.  
  
 `rgguidExtendedInfo`  
 \[in\] matrice di oggetti `GUID`viene passata in modo da poter recuperare più elementi di informazioni estese contemporaneamente.  
  
 `pExtendedInfo`  
 \[out\] restituisce una matrice `VARIANT`oggetti che può essere utilizzata per recuperare le informazioni di proprietà estesa.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  
  
## Note  
 Questa interfaccia ottiene informazioni estese per l'oggetto.  L'api esiste solo a scopo di recuperare le informazioni non si prestano a essere recuperato mediante l'utilizzo `IDebugProperty::GetPropertyInfo`\).  
  
## Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)