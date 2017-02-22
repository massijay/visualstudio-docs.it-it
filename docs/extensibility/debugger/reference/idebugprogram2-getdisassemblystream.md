---
title: "IDebugProgram2::GetDisassemblyStream | Microsoft Docs"
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
  - "IDebugProgram2::GetDisassemblyStream"
helpviewer_keywords: 
  - "IDebugProgram2::GetDisassemblyStream"
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il flusso di disassembly per questo programma o una parte del programma.  
  
## Sintassi  
  
```cpp#  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```c#  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### Parametri  
 `dwScope`  
 \[in\]  Specifica un valore [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) dell'enumerazione che definisce l'ambito del flusso di disassembly.  
  
 `pCodeContext`  
 \[in\]  [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Un oggetto che rappresenta la posizione in cui avviare il flusso di disassembly.  
  
 `ppDisassemblyStream`  
 \[out\]  Restituisce [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) un oggetto che rappresenta il flusso di disassembly.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  restituisce `E_DISASM_NOTSUPPORTED` se il disassembly non è supportato per questa architettura particolare.  
  
## Note  
 Se il parametro di `dwScopes` include il flag di `DSS_HUGE` [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) l'enumerazione impostata, il disassembly si prevede che restituisca numerose istruzioni disassembly, ad esempio, di un intero file o modulo.  Se il flag di `DSS_HUGE` non è impostato, il disassembly si prevede che limiti a una piccola area, in genere di sola funzione.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)