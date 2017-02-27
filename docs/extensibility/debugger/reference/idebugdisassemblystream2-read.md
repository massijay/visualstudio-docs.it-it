---
title: "IDebugDisassemblyStream2::Read | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Read"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Read"
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Lette istruzioni a partire dalla posizione corrente nel flusso di disassembly.  
  
## Sintassi  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```c#  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### Parametri  
 `dwInstructions`  
 \[in\]  Il numero di istruzioni disassemblare.  Questo valore è anche la lunghezza massima della matrice di `prgDisassembly` .  
  
 `dwFields`  
 \[in\]  Una combinazione di flag [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) dall'enumerazione che indicano quali campi di `prgDisassembly` devono essere compilati.  
  
 `pdwInstructionsRead`  
 \[out\]  Restituisce il numero di istruzioni in realtà smontate.  
  
 `prgDisassembly`  
 \[out\]  Una matrice [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) di strutture che viene riempita con codice smontato, una struttura per istruzioni smontata.  La lunghezza della matrice è rientri viene stabilito dal parametro di `dwInstructions` .  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il numero massimo di istruzioni disponibili nell'ambito corrente può essere ottenuto chiamando [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) il metodo.  
  
 La posizione corrente in cui l'istruzione seguente viene letta da può essere modificata chiamando [Ricerca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) il metodo.  
  
 Il flag di `DSF_OPERANDS_SYMBOLS` è possibile aggiungere al flag di `DSF_OPERANDS` nel parametro di `dwFields` per indicare che i nomi dei simboli devono essere utilizzati quando smonta le istruzioni.  
  
## Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Ricerca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)