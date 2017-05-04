---
title: "IEnumRemoteDebugApplications::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplications.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplications::Skip"
ms.assetid: 9f6578d9-8de5-419c-b1b5-7cb07b6367fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplications::Skip
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
 [Interfaccia IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)