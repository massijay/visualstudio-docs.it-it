---
title: "IDebugEntryPointEvent2 | Microsoft Docs"
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
  - "IDebugEntryPointEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugEntryPointEvent2"
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Il motore \(DE\) di debug invia questa interfaccia gestione \(SDM\) di debug della sessione quando il programma sta per l'esecuzione della prima istruzione del codice utente.  
  
## Sintassi  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia come parte delle operazioni standard.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento quando il programma sottoposto a debug è stato caricato ed è possibile eseguire la prima istruzione del codice utente.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è collegato al programma sottoposto a debug.  
  
## Note  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) viene inviato quando il programma sta per l'esecuzione della primissima istruzione.  Ad esempio, `IDebugEntryPoint2` viene inviato quando il programma sta per l'esecuzione della funzione di `main` utente.  
  
 Quando il DE invia `IDebugEntryPointEvent2`, la posizione corrente del codice dovrà essere alla prima istruzione del codice utente, come `main`.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)