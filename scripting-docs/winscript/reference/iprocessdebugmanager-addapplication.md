---
title: "IProcessDebugManager::AddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.AddApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::AddApplication"
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::AddApplication
Aggiunta un'applicazione all'elenco dei computer di debug delle applicazioni in esecuzione.  
  
## Sintassi  
  
```  
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### Parametri  
 `pda`  
 \[in\] l'applicazione di debug aggiungere all'elenco delle applicazioni in esecuzione.  
  
 `pdwAppCookie`  
 \[out\] cookie A utilizzate per rimuovere l'applicazione dall'amministratore del computer di debug.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo aggiunge un'applicazione all'elenco in esecuzione dell'amministratore del computer di debug.  
  
## Vedere anche  
 [Interfaccia IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)