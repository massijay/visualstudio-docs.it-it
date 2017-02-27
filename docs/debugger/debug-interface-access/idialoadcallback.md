---
title: "IDiaLoadCallback | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaLoadCallback (interfaccia)"
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Riceve i callback dal simbolo di diametro che individua la routine, quindi abilitando un'interfaccia utente per segnalare lo stato di avanzamento del tentativo di posizione.  
  
## Sintassi  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 I seguenti metodi esposti da questa interfaccia:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Chiamato quando una directory debug è stata trovata nel file EXE.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Chiamato quando un file candidate dbg è stato aperto.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Chiamato quando un file candidate pdb è stato aperto.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Determina se query del Registro di sistema possono essere utilizzati per individuare i percorsi di ricerca dei simboli.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Determina se l'accesso è consentito in un server di simboli ai simboli di risoluzione.|  
  
## Note  
 L'applicazione client implementa questa interfaccia e viene fornito un riferimento a nella chiamata a [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
 Per le restrizioni aggiuntive che possono essere impostate a un processo di caricamento, vedere [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) interfaccia.  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)