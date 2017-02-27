---
title: "IDebugBreakEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugBreakEvent2"
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia consente all'amministratore di debug della sessione \(SDM\) che l'interruzione asincrona correttamente completata.  
  
## Sintassi  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per supportare l'utente interrompe un programma.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto di questa interfaccia \(utilizzi [QueryInterface](/visual-cpp/atl/queryinterface) di SDM accedere all'interfaccia di `IDebugEvent2` \).  
  
## Note per i chiamanti  
 Le chiamate di SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quando l'utente ha richiesto il programma sottoposto a debug per essere sospeso.  quando il programma correttamente è stato messo in pausa, il DE invia l'evento di `IDebugBreakEvent2` .  Questo evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback fornite da SDM quando è collegato al programma sottoposto a debug.  
  
## Note  
 Ad esempio, un utente può selezionare il comando di **interrompere tutti** scegliere dal menu Debug uscire da un programma eseguito un ciclo infinito.  Lo SDM indica al programma di interruzione chiamando [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md).  Il DE invia `IDebugBreakEvent2` quando il programma viene interrotto.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)