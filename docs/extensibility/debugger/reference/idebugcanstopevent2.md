---
title: "IDebugCanStopEvent2 | Microsoft Docs"
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
  - "IDebugCanStopEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugBreakpointRequest2"
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene utilizzata per richiedere all'amministratore di debug della sessione \(SDM\) se l'arresto della posizione corrente di codice.  
  
## Sintassi  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per supportare l'esecuzione un'istruzione al codice sorgente.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto di questa interfaccia \(utilizzi [QueryInterface](/visual-cpp/atl/queryinterface) di SDM accedere all'interfaccia di `IDebugEvent2` \).  
  
 L'implementazione di questa interfaccia deve comunicare la chiamata di SDM [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) al motore di debug.  Ad esempio, può essere eseguita con un messaggio inviato al thread di gestione dei messaggi del motore di debug o l'oggetto che implementa questa interfaccia possibile utilizzare un riferimento al motore di debug e la richiamata nel motore di debug con il flag è viene trasformata `IDebugCanStopEvent2::CanStop`.  
  
## Note per i chiamanti  
 Il DE possibile inviare questo metodo ogni volta il DE viene richiesto per continuare l'esecuzione e di DE esegue il codice un'istruzione alla volta.  Questo evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback fornite da SDM quando è collegato al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugCanStopEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)|ottiene il motivo per questo evento.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Specifica se il programma di cui viene eseguito il debug deve essere interrotta nella posizione di questo evento \(e inviare un evento che descrive il motivo per arrestare\) o continuare immediatamente l'esecuzione.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ottiene il contesto del documento che specifica la posizione di questo evento.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ottiene il contesto di codice che specifica la posizione di questo evento.|  
  
## Note  
 Il DE invia questa interfaccia se l'utente effettua una funzione e il DE non trova informazioni di debug presenti o le informazioni di debug sono presenti ma il DE non sa se il codice sorgente è possibile visualizzare per quel percorso.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)