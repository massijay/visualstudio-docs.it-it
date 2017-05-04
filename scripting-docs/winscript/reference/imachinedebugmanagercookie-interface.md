---
title: "Interfaccia IMachineDebugManagerCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IMachineDebugManagerCookie"
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IMachineDebugManagerCookie
Simile all'interfaccia `IMachineDebugManager`, supporta l'interfaccia `IMachineDebugManagerCookie` il debug cookie.  
  
 Questa interfaccia \(con l'interfaccia `IDebugCookie` \) consente script da eseguire in un processo del debugger dello script senza richiedere che il debugger tenere traccia degli script.  
  
 Un debugger di script chiama il metodo `IDebugCookie::SetDebugCookie` l'amministratore di processo \(PDM\) di debug.  Quindi, il PDM inviare tali cookie con qualsiasi richiesta di aggiungere o rimuovere un'applicazione di script o di Debug Machine Manager \(MDM\), utilizzando metodi di interfaccia `IMachineDebugManagerCookie`.  Il MDM quindi notifica ogni debugger di modifica, eccetto che dispone di tale cookie.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IMachineDebugManagerCookie` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Aggiunta un'applicazione all'elenco in esecuzione di un'applicazione.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Restituisce un enumeratore l'elenco aggiornato delle applicazioni in esecuzione.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Rimuove un'applicazione dall'elenco in esecuzione di un'applicazione.|  
  
## Vedere anche  
 [Interfaccia IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Interfaccia IDebugCookie](../../winscript/reference/idebugcookie-interface.md)