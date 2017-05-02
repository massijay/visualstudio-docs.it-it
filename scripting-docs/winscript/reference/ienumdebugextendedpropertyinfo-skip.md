---
title: "IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Skip"
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Skip
Ignora un numero specificato di strutture `ExtendedDebugPropertyInfo` in una sequenza di enumerazione.  
  
## Sintassi  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\] numero di strutture `ExtendedDebugPropertyInfo` nella sequenza di enumerazione da ignorare.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  Restituisce `S_FALSE` e imposta il puntatore dell'elemento corrente al termine dell'enumerazione se `celt` è maggiore del numero di elementi che rimangono nell'enumeratore.  
  
## Vedere anche  
 [Interfaccia IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Struttura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)