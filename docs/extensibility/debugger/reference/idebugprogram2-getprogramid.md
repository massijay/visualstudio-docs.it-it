---
title: "IDebugProgram2::GetProgramId | Microsoft Docs"
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
  - "IDebugProgram2::GetProgramId"
helpviewer_keywords: 
  - "IDebugProgram2::GetProgramId"
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetProgramId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene un GUID per il programma.  
  
## Sintassi  
  
```cpp#  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```c#  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### Parametri  
 `pguidProgramId`  
 \[out\]  Restituisce `GUID` di questo programma.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il modulo \(DE\) di debug deve restituire l'identificatore del programma originariamente superato [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) ai metodi.  Ciò consente l'identificazione del programma tra i componenti del debugger.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)