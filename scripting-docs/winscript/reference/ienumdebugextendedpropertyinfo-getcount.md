---
title: "IEnumDebugExtendedPropertyInfo::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.GetCount
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::GetCount"
ms.assetid: 2c862f62-b57c-4cd4-ac4e-7d372fbda9a4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::GetCount
Ottiene il numero di strutture `ExtendedDebugPropertyInfo` l'enumeratore.  
  
## Sintassi  
  
```  
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### Parametri  
 `pcelt`  
 \[out\] restituisce il numero di strutture `ExtendedDebugPropertyInfo` l'enumeratore.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  
  
## Vedere anche  
 [Interfaccia IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Struttura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)