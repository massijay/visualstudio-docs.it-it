---
title: "IDebugFormatter::GetStringForVarType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetStringForVarType
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetStringForVarType"
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetStringForVarType
Restituisce una stringa che rappresenta il valore specificato di VARTYPE.  
  
## Sintassi  
  
```  
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### Parametri  
 `vt`  
 \[in\] VARTYPE da rappresentare come stringa.  
  
 `ptdescArrayType`  
 \[in\] matrice di strutture che descrive i tipi.  
  
 `pbstr`  
 \[out\] stringa che rappresenta `vt`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Il metodo restituisce una stringa che rappresenta il valore specificato di VARTYPE.  
  
## Vedere anche  
 [Interfaccia IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)