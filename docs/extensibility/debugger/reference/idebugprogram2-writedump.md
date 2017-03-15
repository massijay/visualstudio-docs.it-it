---
title: "IDebugProgram2::WriteDump | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::WriteDump"
helpviewer_keywords: 
  - "IDebugProgram2::WriteDump"
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Scrive un dump in un file.  
  
## Sintassi  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```c#  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### Parametri  
 `DumpType`  
 \[in\]  Un valore [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) dell'enumerazione che specifica il tipo di dump, ad esempio, breve o long.  
  
 `pszDumpUrl`  
 \[in\]  L'URL per scrivere il dump su.  In genere, è sotto forma di `file://c: \ percorso \ filename.ext`, ma può essere qualsiasi URL valido.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Un dump di programma in genere include lo stack frame corrente, lo stack stesso, un elenco dei thread del programma ed eventualmente tutta la memoria che il programma è proprietario.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)