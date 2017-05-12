---
title: "Interfaccia IRemoteDebugApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IRemoteDebugApplication"
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Interfaccia IRemoteDebugApplication
Rappresenta un'applicazione in esecuzione.  Non deve corrispondere a un processo del sistema operativo.  In genere, un debugger a un'applicazione per il debug.  L'amministratore processo di debug in genere implementato l'oggetto applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IRemoteDebugApplication` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Continua un'applicazione che è attualmente in un punto di interruzione.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Causa l'applicazione interrompere il debugger la prima.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Connettere un debugger all'applicazione.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Disconnette il debugger corrente dall'applicazione.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Restituisce il debugger corrente collegato all'applicazione.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Fornisce un meccanismo per l'ide del debugger, out\-of\-process in esecuzione all'applicazione, creare oggetti nel processo dell'applicazione.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Indica se l'applicazione viene velocemente.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Enumera i thread notoriamente associato all'applicazione.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Restituisce il nome di questo nodo dell'applicazione.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Restituisce il nodo dell'applicazione in cui tutti i nodi associati all'applicazione vengono aggiunti.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Enumera i contesti globali di espressione per tutti i linguaggi in esecuzione in questa applicazione.|