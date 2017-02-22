---
title: "IDebugEngineLaunch2::CanTerminateProcess | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::CanTerminateProcess"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::CanTerminateProcess"
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineLaunch2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina se un processo può essere terminato.  
  
## Sintassi  
  
```cpp#  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```c#  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### Parametri  
 `pProcess`  
 \[in\]  [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) un oggetto che rappresenta il processo da terminare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  Restituisce `S_FALSE` se il motore non possono terminare il processo, ad esempio, in quanto viene negato.  
  
## Note  
 Se questo metodo restituisce `S_OK`, il metodo [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) può essere chiamato in realtà per terminare il processo.  
  
## Vedere anche  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)