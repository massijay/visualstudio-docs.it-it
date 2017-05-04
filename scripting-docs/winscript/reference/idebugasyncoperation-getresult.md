---
title: "IDebugAsyncOperation::GetResult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::GetResult"
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::GetResult
Fornisce il parametro dell'oggetto di ritorno e valore restituito dall'operazione sincrona di debug.  
  
## Sintassi  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### Parametri  
 `phrResult`  
 \[out\] se l'operazione viene completata, `phrResult` è il valore restituito `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 \[out\] se l'operazione viene completata, `ppunkResult` è il parametro dell'oggetto restituito dall'operazione.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_PENDING`|L'operazione non è stata completata.|  
  
## Note  
 Se l'operazione è stata completata, questo metodo restituisce `HRESULT` e il parametro dell'oggetto da `IDebugSyncOperation::Execute`.  
  
## Vedere anche  
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)