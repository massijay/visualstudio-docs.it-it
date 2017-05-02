---
title: "IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateAsyncDebugOperation"
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateAsyncDebugOperation
Fornisce l'accesso asincrono a un'operazione sincrona specificata di debug.  
  
## Sintassi  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### Parametri  
 `psdo`  
 \[in\] l'oggetto sincrono operazione di debug.  
  
 `ppado`  
 \[out\] l'oggetto asincrono delle operazioni di debug.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo consente ai motori di linguaggio valutino espressioni in modo asincrono senza in modo esplicito sincronizzazione con il thread del debugger.  Per ulteriori informazioni, vedere [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md) e [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)   
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)