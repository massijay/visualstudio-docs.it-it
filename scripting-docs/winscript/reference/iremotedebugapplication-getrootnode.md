---
title: "IRemoteDebugApplication::GetRootNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.GetRootNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::GetRootNode"
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::GetRootNode
Restituisce il nodo dell'applicazione in cui tutti i nodi associati all'applicazione vengono aggiunti.  
  
## Sintassi  
  
```  
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### Parametri  
 `ppdanRoot`  
 \[out\] il nodo dell'applicazione di debug in cui tutti i nodi associati all'applicazione vengono aggiunti.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo restituisce il nodo dell'applicazione in cui tutti i nodi associati all'applicazione vengono aggiunti.  
  
## Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)