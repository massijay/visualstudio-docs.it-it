---
title: "Interfaccia IActiveScriptSiteDebugEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptSiteDebugEx"
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IActiveScriptSiteDebugEx
Implementare questa interfaccia con l'interfaccia `IActiveScriptSiteDebug` se si scrive un host che deve ottenere una notifica di un errore di runtime in un'applicazione ed eventualmente di connessione all'applicazione per il debug.  L'amministratore processo di debug include la notifica con `IActiveScriptDebug` se un debugger lo script si trova sul computer.  Se nessun debugger lo script viene trovato, il PDM fornisce la notifica con `IActiveScriptDebugEx` anziché.  
  
 Per ottenere una notifica di un errore di runtime, l'host deve gestire [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/it-it/cf7639f9-a699-4571-9f3a-82ef52c0b5f4).  Sulla base di un'azione utente, è possibile decidere se connettere il debugger e tornare interni, o restituire avviare il debugger nel parametro di OnScriptErrorDebug `pfEnterDebugger`.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|All'host su un errore di runtime script quando l'amministratore del processo di debug non trova un debugger Just\-in\-time\- esterno.|