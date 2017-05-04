---
title: "Interfaccia IRemoteDebugApplicationEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IRemoteDebugApplicationEx"
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Interfaccia IRemoteDebugApplicationEx
Rappresenta un'applicazione in esecuzione.  Non deve corrispondere a un processo del sistema operativo.  In genere, un debugger a un'applicazione per il debug.  L'amministratore processo di debug in genere implementato l'oggetto applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IRemoteDebugApplicationEx` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Restituisce l'id processo per l'applicazione host.|  
|GetHostMachineName|Restituisce il nome del computer che l'applicazione host è in esecuzione.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Imposta il linguaggio per la localizzazione del debugger.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Forza il debugger in modalità di istruzione singola.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Revoca un comando di interruzione.|  
|SetProxyBlanketAndAddRef|Le informazioni sulla sicurezza COM degli aggiornamenti su un proxy per un oggetto del debugger assicurino la compatibilità con il debug remoto da Windows 95 in base ai sistemi operativi.|  
|ReleaseFromSetProxyBlanket|Versioni AddRef da SetProxyBlanketAndAddRef.|