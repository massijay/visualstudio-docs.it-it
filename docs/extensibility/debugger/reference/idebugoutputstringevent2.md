---
title: "IDebugOutputStringEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugOutputStringEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugOutputStringEvent2"
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene inviata dal motore \(DE\) di debug gestione \(SDM\) di debug della sessione per restituire una stringa.  
  
## Sintassi  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per inviare una stringa alla finestra di output dell'IDE.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento per inviare una stringa alla finestra di output.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è associata al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente viene illustrato il metodo di `IDebugOutputStringEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetString](../Topic/IDebugOutputStringEvent2::GetString.md)|Ottiene il messaggio visibili.|  
  
## Note  
 Ad esempio, il codice non gestito, la stringa da restituire possibile produrre quando il programma sottoposto a debug invia una stringa alla funzione Win32 `OutputDebugString` .  Questa stringa viene intercettata da DE e inviata sullo SDM ad esempio l'evento di `IDebugOutputStringEvent2` .  
  
 Per [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) inviare un messaggio che richiede una risposta dell'utente.  
  
 Per [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) inviare un messaggio di errore che non richiede una risposta.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)