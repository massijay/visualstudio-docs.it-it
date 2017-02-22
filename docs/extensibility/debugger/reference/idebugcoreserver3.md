---
title: "IDebugCoreServer3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3"
helpviewer_keywords: 
  - "Interfaccia IDebugCoreServer3"
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia consente l'accesso alle informazioni relative al server che il processo è in esecuzione.  
  
## Sintassi  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## Note per gli implementatori  
 Visual Studio implementa.  
  
## Note per i chiamanti  
 Utilizzare per ottenere [QueryInterface](/visual-cpp/atl/queryinterface) questa interfaccia [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) da un'interfaccia.  Una chiamata [Metodo GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) dal boxing anche restituisce questa interfaccia.  Questa interfaccia viene utilizzata più frequentemente da un fornitore di porte personalizzato per avviare i programmi in un server \(locale o remota\).  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) in un'interfaccia, l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera il nome del server.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera una versione descrittivo del nome del server|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indica i motori di debug specifici automaticamente di connessione ai processi quando tali processi avviati.|  
|[DiagnoseWebDebuggingError](../Topic/IDebugCoreServer3::DiagnoseWebDebuggingError.md)|Recupera un codice di errore specifico una volta automatico allegano esito negativo.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crea un'istanza di un modulo di debug sul server.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera un flag che indica se il server è lo stesso computer del chiamante.|  
|[GetConnectionProtocol](../Topic/IDebugCoreServer3::GetConnectionProtocol.md)|Recupera un valore che indica il protocollo utilizzato per comunicare con il server.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Disabilita tutte le impostazioni dell'auto\-attaccatura per tutti i motori di debug che il server è a conoscenza.|  
  
## Note  
 Un fornitore di porte personalizzato riceve [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia su una chiamata a [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).  L'interfaccia di `IDebugCoreServer3` può essere ottenuta dall'interfaccia.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [Metodo GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)