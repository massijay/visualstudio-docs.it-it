---
title: "IDebugDisassemblyStream2::GetSize | Microsoft Docs"
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
  - "IDebugDisassemblyStream2::GetSize"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetSize"
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene la dimensione nelle istruzioni del flusso di disassembly.  
  
## Sintassi  
  
```cpp#  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```c#  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### Parametri  
 `pnSize`  
 \[out\]  Restituisce le dimensioni, nelle istruzioni.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il valore restituito da questo metodo può essere utilizzato per allocare una matrice [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) di strutture che viene quindi passata [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) al metodo.  
  
## Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)