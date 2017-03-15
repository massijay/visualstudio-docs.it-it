---
title: "IDebugProgram2::EnumCodePaths | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumCodePaths"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodePaths"
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un elenco di percorsi di codice per una posizione specificata in un file di origine.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```c#  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### Parametri  
 `pszHint`  
 \[in\]  La parola sotto il cursore nella visualizzazione di **disassembly** o di **database di origine** nell'IDE.  
  
 `pStart`  
 \[in\]  [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) un oggetto che rappresenta il contesto di codice corrente.  
  
 `pFrame`  
 \[in\]  [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) Un oggetto che rappresenta lo stack frame associato al punto di interruzione corrente.  
  
 `fSource`  
 \[in\]  Diverso da zero \(`TRUE`\) se nella visualizzazione di **database di origine** , o in zero \(`FALSE`\) se nella visualizzazione di **disassembly** .  
  
 `ppEnum`  
 \[out\]  Restituisce [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) un oggetto che contiene un elenco di percorsi di codice.  
  
 `ppSafety`  
 \[out\]  Restituisce [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) un oggetto che rappresenta un contesto di codice da impostare come punto di interruzione nel percorso di codice scelto sia sottoposto a override.  Ciò può verificarsi nel caso di un'espressione booleana esegue un corto circuito, ad esempio.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Un percorso di codice viene descritto il nome di una funzione o un metodo che viene chiamato per ottenere il punto corrente nell'esecuzione del programma.  Un elenco di percorsi di codice rappresenta lo stack di chiamate.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)