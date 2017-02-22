---
title: "IDebugProgram2::GetProcess | Microsoft Docs"
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
  - "IDebugProgram2::GetProcess"
helpviewer_keywords: 
  - "IDebugProgram2::GetProcess"
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottenere il processo che il programma è in esecuzione.  
  
## Sintassi  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### Parametri  
 `ppProcess`  
 \[out\]  restituisce [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) l'interfaccia che rappresenta il processo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 A meno che il \(DE\) modulo di debug implementi [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) l'interfaccia, l'implementazione di DE di questo metodo restituirà sempre `E_NOTIMPL` perché un DE non può determinare il processo è in esecuzione e pertanto non può soddisfare un'implementazione del metodo.  
  
 Implementare l'interfaccia di `IDebugEngineLaunch2` significa che il DE necessario sapere come creare un processo; di conseguenza, l'implementazione di DE [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dell'interfaccia può conoscere il processo è in esecuzione.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)