---
title: "IDebugEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2"
helpviewer_keywords: 
  - "Interfaccia IDebugEngine2"
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta un motore di debug \(DE\).  Viene utilizzata per gestire vari aspetti di una sessione di debug, da creare i punti di interruzione a impostare e per eliminare le eccezioni.  
  
## Sintassi  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata da un oggetto personalizzato DE per gestire il debug di programmi.  Questa interfaccia deve essere implementata da DE.  
  
## Note per i chiamanti  
 Questa interfaccia viene chiamata dall'amministratore di debug della sessione \(SDM\) per gestire la sessione di debug, inclusa la gestione delle eccezioni, creare i punti di interruzione e la risposta a eventi sincroni inviati da DE.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugEngine2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumeratore per tutti i programmi in corso il debug da un DE.|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Associa un DE a un programma.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Creazione di un punto di interruzione in attesa in DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Specifica come il DE necessario gestire un'eccezione specificata.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Rimuove eccezione specificata in modo da più non è gestita dal motore di debug.|  
|[RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md)|Cancella l'elenco delle eccezioni che l'ide ha impostato per un'architettura o un linguaggio in fase di esecuzione specifico.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ottiene il GUID di DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Notifica a un DE che il programma specificato in modo che atipica è stato interrotto e che il DE necessario eliminare tutti i riferimenti al programma e inviare un programma eliminato l'evento.|  
|[ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)|Chiamato da SDM per indicare che un evento di debug sincrono, precedentemente inviato da DE a SDM, è stato ricevuto e elaborato stato.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Imposta le impostazioni locali di DE.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Imposta attualmente la chiave radice del Registro di sistema in uso da DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Imposta una metrica.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Le richieste che tutti i programmi in corso il debug da questo DE interrotte l'esecuzione la volta successiva che uno dei thread tenta di eseguire.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)