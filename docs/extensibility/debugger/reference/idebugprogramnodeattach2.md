---
title: "IDebugProgramNodeAttach2 | Microsoft Docs"
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
  - "IDebugProgramNodeAttach2"
helpviewer_keywords: 
  - "Interfaccia IDebugProgramNodeAttach2"
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Consente un nodo di programma da parte di un tentativo di effettuare la connessione al programma associato.  
  
## Sintassi  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia è implementata nella stessa classe che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) l'interfaccia per ricevere la notifica di un'operazione di connessione e fornire una possibilità di annullare l'operazione di connessione.  
  
## Note per i chiamanti  
 Leggi questa interfaccia chiamando il metodo di `QueryInterface` [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) in un oggetto.  [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Il metodo deve essere chiamato prima [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) del metodo per fornire al nodo del programma la possibilità di interrompere il processo di connessione.  
  
## Metodi nell'ordine di Vtable  
 questa interfaccia implementa il seguente metodo:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Si connette al programma associato o ripianificare il processo di connessione [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) al metodo.|  
  
## Note  
 Questa interfaccia è l'alternativa consigliata al metodo deprecato [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) .  Tutti i motori di debug vengono sempre caricati con la funzione di `CoCreateInstance` , ovvero, viene creata un'istanza dallo spazio degli indirizzi del programma sottoposto a debug.  
  
 Se l'implementazione precedente del metodo di `IDebugProgramNode2::Attach_V7` stesse impostando semplicemente `GUID` del programma sottoposto a debug, quindi solo [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) il metodo deve essere implementato.  
  
 Se l'implementazione precedente del metodo di `IDebugProgramNode2::Attach_V7` utilizzare l'interfaccia di callback assegnato, quindi che la funzionalità sia stata spostata in un'implementazione [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) del metodo e dell'interfaccia di `IDebugProgramNodeAttach2` non deve essere implementato.  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)