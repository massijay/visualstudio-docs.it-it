---
title: "IDebugFirewallConfigurationCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugFirewallConfigurationCallback2"
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Abilita il modulo di debug che utilizza DCOM per chiedere all'interfaccia utente di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] per assicurarsi che il firewall non bloccare il debug remoto.  
  
## Sintassi  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## Note per gli implementatori  
 Implementato dall'oggetto della porta di amministratore di debug della sessione.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugFirewallConfigurationCallback2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Richieste che il debug remoto del blocco di firewall.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll