---
title: "IDebugProgram2::EnumCodeContexts | Microsoft Docs"
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
  - "IDebugProgram2::EnumCodeContexts"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodeContexts"
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un elenco dei contesti di codice per una posizione specificata in un file di origine.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```c#  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### Parametri  
 `pDocPos`  
 \[in\]  [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) Un oggetto che rappresenta un percorso astratta in un file di origine noto all'IDE.  
  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) un oggetto che contiene un elenco dei contesti di codice.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo consente che l'amministratore \(SDM\) di debug della sessione o l'ide esegue il mapping di una posizione del file di origine in un percorso di codice.  Più contesti di codice viene restituito se il database di origine genera i blocchi più di codice \(ad esempio, modelli C\+\+\).  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)