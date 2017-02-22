---
title: "IDebugModuleLoadEvent2 | Microsoft Docs"
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
  - "IDebugModuleLoadEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugModuleLoadEvent2"
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModuleLoadEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene inviata dal motore \(DE\) di debug gestione \(SDM\) di debug della sessione quando un modulo viene caricato o scaricato.  
  
## Sintassi  
  
```  
IDebugModuleLoadEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per segnalare che un modulo è stato caricato o scaricato stato.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE crea e che invia questo oggetto evento per notificare che un modulo è stato caricato o scaricato stato.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è associata al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente viene illustrato il metodo di `IDebugModuleLoadEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|Ottiene il modulo in fase di caricamento o scaricati.|  
  
## Note  
 Visual Studio utilizza questo evento per mantenere la finestra di **moduli** aggiornata.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)