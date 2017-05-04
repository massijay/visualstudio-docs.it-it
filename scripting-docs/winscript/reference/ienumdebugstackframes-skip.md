---
title: "IEnumDebugStackFrames::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Skip"
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Skip
Ignora un numero specificato di segmenti nella sequenza di enumerazione.  
  
## Sintassi  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\] numero di segmenti nella sequenza di enumerazione da ignorare.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo ignora un numero specificato di segmenti nella sequenza di enumerazione.  
  
## Vedere anche  
 [Interfaccia IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)