---
title: "Interfaccia IDebugApplication110 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugApplication110"
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Interfaccia IDebugApplication110
L'interfaccia `IDebugApplication110` estendere la funzionalità [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  È possibile ottenere un'istanza di questa interfaccia chiamando QueryInterface in un'implementazione [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  L'interfaccia viene implementata da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Metodi  
 L'interfaccia `IDebugApplication110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Effettua una chiamata sincrona il thread principale.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Effettua una chiamata asincrona nel thread principale.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Attende uno degli handle specificate da segnalare mentre nelle chiamate cross\-thread da inserire al thread.  Questo metodo deve essere chiamato dal thread del debugger.|