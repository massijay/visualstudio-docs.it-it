---
title: "IEnumDebugExtendedPropertyInfo::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Next"
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Next
Recupera un numero specificatodi strutture di`ExtendedDebugPropertyInfo` in una sequenza di enumerazione.  
  
## Sintassi  
  
```  
HRESULT Next (  
   ULONG celt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\] numero di strutturedi `ExtendedDebugPropertyInfo`da recuperare.  
  
 `rgelt`  
 \[out\] matrice di strutture `ExtendedDebugPropertyInfo` recuperate.  
  
 `pceltFetched`  
 \[out\] numero di strutture `ExtendedDebugPropertyInfo` effettivamente recuperate.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  
  
## Vedere anche  
 [Interfaccia IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Struttura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)