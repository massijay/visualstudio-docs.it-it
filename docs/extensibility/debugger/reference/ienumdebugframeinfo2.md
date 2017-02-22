---
title: "IEnumDebugFrameInfo2 | Microsoft Docs"
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
  - "IEnumDebugFrameInfo2"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2"
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia enumera [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) le strutture.  
  
## Sintassi  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per definire un elenco di strutture che descrive lo stack di chiamate corrente.  
  
## Note per i chiamanti  
 Chiamate [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) di Visual Studio per ottenere questa interfaccia tutte le volte che un punto di interruzione, viene generata un'eccezione, o un arresto si verifica in un programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IEnumDebugFrameInfo2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../Topic/IEnumDebugFrameInfo2::Next.md)|Recupera un numero specificato [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) di strutture in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Ignora un numero specificato [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) di strutture in una sequenza di enumerazione.|  
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clona](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)|Ottiene il numero [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) di strutture in un enumeratore.|  
  
## Note  
 Visual Studio ottiene questa interfaccia come il primo passaggio per gestire un punto di interruzione, viene generata un'eccezione, o una pausa utente\-generata nel programma sottoposto a debug.  L'elenco [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) delle strutture rappresenta lo stack di chiamate corrente, alla chiamata di funzione corrente all'inizio dell'elenco e la chiamata di funzione precedente all'elenco.  Ogni `FRAMEINFO` rappresenta uno stack frame, un contesto in cui le espressioni possono essere valutate e variabili locali essere esaminati.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)