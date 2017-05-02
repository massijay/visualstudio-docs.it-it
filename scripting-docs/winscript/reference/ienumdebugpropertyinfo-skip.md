---
title: "IEnumDebugPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Skip"
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Skip
Ignora un numero specificato di strutture `DebugPropertyInfo` in una sequenza di enumerazione.  
  
## Sintassi  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\] numero di strutture `DebugPropertyInfo` nella sequenza di enumerazione da ignorare.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  Restituisce `S_FALSE` e imposta il puntatore dell'elemento corrente al termine dell'enumerazione se `celt` è maggiore del numero di elementi che rimangono nell'enumeratore.  
  
## Vedere anche  
 [Interfaccia IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)