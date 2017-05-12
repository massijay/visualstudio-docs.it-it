---
title: "IRemoteDebugApplicationThread::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetState"
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetState
Ottiene lo stato del thread.  
  
## Sintassi  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### Parametri  
 `pState`  
 \[out\] la combinazione di seguito stato del thread diminuisce:  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|THREAD\_STATE\_RUNNING|0x00000001|Il thread è in esecuzione.|  
|THREAD\_STATE\_SUSPENDED|0x00000002|Thread sospeso.|  
|THREAD\_BLOCKED|0x00000004|Il thread è bloccato.|  
|THREAD\_OUT\_OF\_CONTEXT|0x00000008|Il thread è dal contenuto.|  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo ottiene lo stato del thread.  
  
## Vedere anche  
 [Interfaccia IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)