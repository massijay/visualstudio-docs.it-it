---
title: "IDebugDisassemblyStream2::Seek | Microsoft Docs"
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
  - "IDebugDisassemblyStream2::Seek"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Seek"
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Sposta il puntatore lettura nel flusso di disassembly un numero specificato di istruzioni relative a una posizione specificata.  
  
## Sintassi  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```c#  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### Parametri  
 `dwSeekStart`  
 \[in\]  Un valore [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md) dell'enumerazione che specifica la posizione relativa per avviare il processo di ricerca.  
  
 `pCodeContext`  
 \[in\]  [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) L'oggetto che rappresenta il contesto di codice che l'operazione di ricerca è relative.  Questo parametro viene utilizzato solo se `dwSeekStart` \= `SEEK_START_CODECONTEXT`; in caso contrario, questo parametro viene ignorato e può essere un valore null.  
  
 `uCodeLocationId`  
 \[in\]  L'identificatore posizione del codice che l'operazione di ricerca è relative.  Questo parametro viene utilizzato se `dwSeekStart` \= `SEEK_START_CODELOCID`; in caso contrario, questo parametro viene ignorato e può essere impostato su 0.  Vedere la sezione relativa alle osservazioni per [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) il metodo per una descrizione di un identificatore posizione del codice.  
  
 `iInstructions`  
 \[in\]  Il numero di istruzioni passare alla posizione specificata in `dwSeekStart`.  Questo valore può essere negativo per spostarsi indietro.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se il percorso di ricerca è stata a un punto oltre l'elenco delle istruzioni disponibili.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Se la ricerca è stata a una posizione antecedente l'inizio dell'elenco, la posizione letti sia impostato sulla prima istruzione nell'elenco.  Se il visualizzare era in una posizione dopo la fine dell'elenco, la posizione in lettura è impostata sull'ultima istruzione nell'elenco.  
  
## Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)