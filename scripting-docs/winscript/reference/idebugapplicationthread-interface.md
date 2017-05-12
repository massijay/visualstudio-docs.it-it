---
title: "Interfaccia IDebugApplicationThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugApplicationThread"
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugApplicationThread
Consente ai motori del linguaggio e gli host di fornire la sincronizzazione dei thread e tengano gestire le informazioni sullo stato di specifiche di debug.  L'interfaccia estende l'interfaccia `IRemoteDebugApplicationThread` per fornire l'accesso remoto non del thread.  
  
 Oltre ai metodi ereditati da `IRemoteDebugApplicationThread`, l'interfaccia `IDebugApplicationThread` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Fornisce un meccanismo per il chiamante al codice di esecuzione nel thread dell'applicazione.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Determina se il thread è il thread attualmente in esecuzione.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Determina se il thread è il thread del debugger.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Imposta la descrizione del thread.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Imposta la descrizione dello stato del thread.|