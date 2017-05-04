---
title: "IEnumDebugCodeContexts::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Skip"
ms.assetid: ba917f57-f7a9-419f-96d6-8f4378b12c57
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Skip
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
 [Interfaccia IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)