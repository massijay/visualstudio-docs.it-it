---
title: "IDebugDocumentChecksum2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugDocumentChecksum2"
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Rappresenta un checksum per un documento di debug e di passare il checksum tra i componenti.  
  
## Sintassi  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## Note per gli implementatori  
 Tale interfaccia può essere implementata da qualsiasi componente che espone [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) l'interfaccia.  Tuttavia, è principalmente implementata dai motori di debug in modo da poter essere passato nuovamente all'IDE e utilizzare il checksum incorporato in un file di simboli \(\*.pdb\) quando rileva un database di origine.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugDocumentChecksum2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera l'identificatore di checksum e l'algoritmo del documento specificato il numero massimo di byte da utilizzare.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll