---
title: "Interfaccia IDebugApplicationThread110 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugApplicationThread110"
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Interfaccia IDebugApplicationThread110
Fornisce ulteriori funzionalità per l'interfaccia [Interfaccia IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md).  
  
> [!IMPORTANT]
>  L'interfaccia viene implementata da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Metodi  
 L'interfaccia `IDebugApplicationThread110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Effettua una chiamata asincrona nel thread principale.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Un conteggio del numero di richieste del thread dai meccanismi di alternanza di thread PDM sono attualmente elaborazione.  In genere 0 o 1, ma è possibile che questo sia maggiore se l'avvio di una chiamata del thread che elaborano ma attiva un sincrono richiamano del thread oppure la sospensione del thread \(ad esempio, attivando un evento di IDebugApplicationEvents che viene visualizzato nel thread del debugger\)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) è stato chiamato su l thread e non ha ancora completato.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Questo thread è in uno stato che può elaborare le chiamate eseguite tramite i meccanismi di alternanza di thread PDM \(come SynchronousCallInThread\).|