---
title: "IDebugPortNotify2::AddProgramNode | Microsoft Docs"
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
  - "IDebugPortNotify2::AddProgramNode"
helpviewer_keywords: 
  - "IDebugPortNotify2::AddProgramNode"
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortNotify2::AddProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Registra un programma che può essere eseguito il debug con la porta che viene eseguito.  
  
## Sintassi  
  
```cpp#  
HRESULT AddProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int AddProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Parametri  
 `pProgramNode`  
 \[in\]  [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) un oggetto che rappresenta il programma da registrare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Un nodo di programma può essere annullato la registrazione dalla porta chiamando [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) il metodo.  
  
## Vedere anche  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)