---
title: "IDebugProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2"
helpviewer_keywords: 
  - "Interfaccia IDebugProgram2"
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un programma in esecuzione in un processo.  
  
## Sintassi  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug e un fornitore di porte personalizzato implementare questa interfaccia per rappresentare un programma in un processo.  L'amministratore \(SDM\) di debug della sessione implementa anche l'interfaccia per fornire informazioni a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## Note per i chiamanti  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) L'evento restituisce questa interfaccia per creare un nuovo programma.  Questa interfaccia viene utilizzata come parametro per molti metodi su più interfacce.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugProgram2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Enumera i thread in esecuzione nel programma.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ottiene il nome del programma.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ottiene il processo che il programma è in esecuzione.|  
|[Termina](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Termina il programma.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Connette al programma.|  
|[CanDetach](../Topic/IDebugProgram2::CanDetach.md)|Determina se un modulo di \(DE\) debug possibile rimuovere dal programma.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Rimuove il debugger dal programma.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ottiene un identificatore univoco globale per il programma.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ottiene le proprietà del programma.|  
|[Esegui](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua a eseguire il programma da uno stato interrotto.  Tutto lo stato precedente di esecuzione viene cancellato.|  
|[Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua a eseguire il programma da uno stato interrotto.  Tutto lo stato precedente di esecuzione viene mantenuto.|  
|[Passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md)|esegue un'operazione.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Le richieste dal programma verrà interrotta la volta successiva che uno dei thread esegue il codice.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ottiene il nome e l'identificatore del motore di \(DE\) debug che esegue il programma.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|enumera i contesti di codice per una posizione specificata in un file di origine.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ottiene i byte di memoria di questo programma.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ottiene il flusso di disassembly per questo programma o parte del programma.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Enumera i moduli che il programma ha caricato ed esegue.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ottiene l'aggiornamento di Modifica e continuazione \(ENC\) per il programma.<br /><br /> Il modulo di debug personalizzato non implementa questo metodo \(restituiscano sempre `E_NOTIMPL`\).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Enumera i percorsi di codice del programma.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Scrive un dump in un file.|  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Note  
 Un programma è un funzionamento del contenitore del thread in un'architettura di runtime particolare, mentre un processo è costituito da uno o più programmi.  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [Successivo](../Topic/IEnumDebugPrograms2::Next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)