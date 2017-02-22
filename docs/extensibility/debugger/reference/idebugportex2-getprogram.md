---
title: "IDebugPortEx2::GetProgram | Microsoft Docs"
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
  - "IDebugPortEx2::GetProgram"
helpviewer_keywords: 
  - "IDebugPortEx2::GetProgram"
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2::GetProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il programma associato a un nodo di programma.  
  
## Sintassi  
  
```cpp#  
HRESULT GetProgram(   
   IDebugProgramNode2* pProgramNode,  
   IDebugProgram2**    ppProgram  
);  
```  
  
```c#  
int GetProgram(   
   IDebugProgramNode2 pProgramNode,  
   out IDebugProgram2 ppProgram  
);  
```  
  
#### Parametri  
 `pProgramNode`  
 \[in\]  [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Un oggetto che rappresenta il nodo del programma.  
  
 `ppProgram`  
 \[out\]  Restituisce [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) un oggetto che rappresenta il programma associato al nodo del programma.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)