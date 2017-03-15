---
title: "IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce un oggetto di contesto di codice corrispondente a un identificatore specificato posizione del codice.  
  
## Sintassi  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Parametri  
 `uCodeLocationId`  
 \[in\]  Specifica l'identificatore posizione del codice.  Vedere la sezione relativa alle osservazioni per [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) il metodo per una descrizione di un identificatore posizione del codice.  
  
 `ppCodeContext`  
 \[out\]  Restituisce [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) un oggetto che rappresenta il contesto di codice.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 L'identificatore posizione del codice può essere restituito da una chiamata [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md) al metodo e può [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) essere visualizzato nella struttura.  
  
 Per convertire un contesto di codice in un identificatore posizione del codice, chiamare [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) il metodo.  
  
## Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)