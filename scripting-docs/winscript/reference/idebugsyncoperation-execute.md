---
title: "IDebugSyncOperation::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.Execute
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::Execute"
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::Execute
In modo sincrono esegue l'operazione e restituisce.  
  
## Sintassi  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### Parametri  
 `ppunkResult`  
 \[out\] il parametro dell'oggetto restituito dall'operazione.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_ABORT`|l'operazione è stata interrotta chiamando il metodo `IDebugSyncOperation::InProgressAbort`.|  
  
## Note  
 L'amministratore processo di debug nel thread di destinazione chiama il metodo `Execute` in modo sincrono.  
  
## Vedere anche  
 [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)