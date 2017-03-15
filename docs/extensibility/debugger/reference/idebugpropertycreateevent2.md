---
title: "IDebugPropertyCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyCreateEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugPropertyCreateEvent2"
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene inviata dal motore \(DE\) di debug gestione \(SDM\) di debug della sessione quando viene creata una proprietà associata a un documento specifico.  
  
## Sintassi  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per segnalare che una proprietà è stata creata.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  Questa interfaccia è implementato se il DE ha creato una proprietà associata a uno script caricato o creato e se lo script venga visualizzato nell'IDE.  
  
## Note per i chiamanti  
 Il DE crea e che invia questo oggetto evento per notificare che una proprietà è stata creata.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è associata al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente viene illustrato il metodo dell'interfaccia di `IDebugPropertyCreateEvent2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|ottiene la nuova proprietà.|  
  
## Note  
 Se una proprietà con un documento specifico o uno script associate, il DE possibile inviare questo evento a SDM per aggiornare la finestra di **Documenti di script** con il nome del documento.  Lo SDM chiamato [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) con l'argomento `guidDocument` per recuperare `VARIANT` che contiene [IUnknown](/visual-cpp/atl/iunknown) un puntatore.  Lo SDM chiamerà [QueryInterface](/visual-cpp/atl/queryinterface) su questo puntatore per [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) recuperare l'interfaccia utilizzata per aggiornare la finestra di **Documenti di script** .  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)