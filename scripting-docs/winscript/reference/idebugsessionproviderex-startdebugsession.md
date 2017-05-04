---
title: "IDebugSessionProviderEx:StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProviderEx:StartDebugSession
apilocation: scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugSessionProviderEx:StartDebugSession
Avviare una sessione di debug con l'applicazione specificata.  
  
## Sintassi  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### Parametri  
 `pda`  
 \[in\] specifica l'applicazione di debug.  
  
 `fQuery`  
 \[in\] le True indica una query.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo avvia una sessione di debug con l'applicazione specificata.  Il debugger deve chiamare `IRemoteDebugApplication::ConnectDebugger` prima di uscire dalla chiamata.  
  
## Vedere anche  
 [Interfaccia IDebugSessionProviderEx](../../winscript/reference/idebugsessionproviderex-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)