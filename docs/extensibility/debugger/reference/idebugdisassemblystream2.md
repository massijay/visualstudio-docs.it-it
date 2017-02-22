---
title: "IDebugDisassemblyStream2 | Microsoft Docs"
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
  - "IDebugDisassemblyStream2"
helpviewer_keywords: 
  - "Interfaccia IDebugDisassemblyStream2"
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un flusso delle istruzioni.  
  
## Sintassi  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il modulo di debug implementa questa interfaccia per supportare il disassembly codice di programma.  
  
## Note per i chiamanti  
 Una chiamata [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) al metodo restituisce questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugDisassemblyStream2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lette istruzioni a partire dalla posizione corrente nel flusso di disassembly.|  
|[Ricerca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Sposta il puntatore lettura nel flusso di disassembly un numero specificato di istruzioni relative a una posizione specificata.|  
|[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)|Restituisce un identificatore posizione del codice per un contesto di codice specifico.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Restituisce un oggetto di contesto di codice corrispondente a un identificatore specificato posizione del codice.|  
|[GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)|Restituisce un identificatore posizione del codice che rappresenta la posizione corrente di codice.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ottiene il documento di origine associato con questo flusso di disassembly.|  
|[GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)|Ottiene l'estensione di questo flusso di disassembly.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ottiene la dimensione del flusso di disassembly.|  
  
## Note  
 Il flusso di disassembly può essere creato per rappresentare l'intero spazio degli indirizzi o solo una funzione o un modulo all'interno dello spazio.  Ogni istruzione è [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) rappresentata da una struttura restituita da una chiamata [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) al metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)