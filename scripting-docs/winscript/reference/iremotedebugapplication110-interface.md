---
title: "Interfaccia IRemoteDebugApplication110 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IRemoteDebugApplication110"
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Interfaccia IRemoteDebugApplication110
Utilizzato per fornire nuove funzionalità che possono essere chiamate dai debugger di script e dai chiamanti in\-process.  
  
> [!IMPORTANT]
>  L'interfaccia viene implementata da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Metodi  
 L'interfaccia `IRemoteDebugApplication110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Chiamato per aggiornare le opzioni del debugger.  l'impostazione predefinita di opzioni a 0 \(SDO\_NONE\).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Restituisce l'insieme corrente delle opzioni abilitate.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Restituisce il thread principale per gli host che chiamano la funzione SetSite.|