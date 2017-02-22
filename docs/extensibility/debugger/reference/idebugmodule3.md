---
title: "IDebugModule3 | Microsoft Docs"
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
  - "IDebugModule3"
helpviewer_keywords: 
  - "Interfaccia IDebugModule3"
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un modulo che supporta si alternano le posizioni dei simboli e degli stati di JustMyCode.  
  
## Sintassi  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per supportare le posizioni alternative di simboli e per l'utilizzo degli stati di JustMyCode \( [Glossario di Debugger di Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) per una definizione di “JustMyCode„\).  
  
## Note per i chiamanti  
 Una chiamata [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) a restituisce questa interfaccia.  Il DE invia [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) l'interfaccia gestione \(SDM\) di debug della sessione utilizzando il metodo [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .  Inoltre, una chiamata [QueryInterface](/visual-cpp/atl/queryinterface) precedente [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) a un'interfaccia restituisce questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) in un'interfaccia, l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Restituisce un elenco di percorsi di ricerca dei simboli e i risultati di ricerca di ogni percorso.|  
|[LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)|Carica e inizializza i simboli del modulo corrente.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Restituisce contrassegnano specificare se il modulo rappresenta il codice utente.|  
|[SetJustMyCodeState](../Topic/IDebugModule3::SetJustMyCodeState.md)|Specifica se il modulo deve essere considerato codice utente o meno.|  
  
## Note  
 Visual Studio è l'utente tipico dell'interfaccia.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)