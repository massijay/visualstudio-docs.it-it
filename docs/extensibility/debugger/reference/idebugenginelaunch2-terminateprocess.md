---
title: "IDebugEngineLaunch2::TerminateProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::TerminateProcess"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::TerminateProcess"
ms.assetid: f7039e7f-5f57-4222-9ad2-11a66b2da6e0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineLaunch2::TerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

termina un processo.  
  
## Sintassi  
  
```cpp#  
HRESULT TerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```c#  
int TerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### Parametri  
 `pProcess`  
 \[in\]  [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) un oggetto che rappresenta il processo da terminare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  
  
## Note  
 chiamare [CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md) il metodo prima di chiamare questo metodo.  
  
## Vedere anche  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)