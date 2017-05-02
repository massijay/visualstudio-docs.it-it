---
title: "Interfaccia IDebugApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugApplication"
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Interfaccia IDebugApplication
Espone metodi del debug remoto non verranno utilizzati dai motori del linguaggio e gli host.  
  
 Oltre ai metodi ereditati da `IRemoteDebugApplication`, l'interfaccia `IDebugApplication` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Imposta il nome dell'applicazione.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|All'amministratore del processo di debug che un motore di linguaggio in modalità di istruzione singola sta per ritornare al relativo chiamante.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Determina la stringa specificata venga visualizzato nell'IDE del debugger.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Avvia l'ide predefinito del debugger e associa una sessione di debug a questa applicazione, se una non è già collegata.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Determina il thread corrente di bloccare e invia una notifica del punto di interruzione all'IDE del debugger.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Causa questa applicazione rilasciare tutti i riferimenti e immettere stato inattivo.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Restituisce i flag correnti dell'interruzione dell'applicazione.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Restituisce il thread associato al thread attualmente in esecuzione.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Fornisce l'accesso asincrono a un'operazione sincrona specificata di debug.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Aggiunge un provider dell'enumeratore lo stack frame all'applicazione.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Rimuove un provider dell'enumeratore lo stack frame dall'applicazione.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Determina se il thread corrente di esecuzione è il thread del debugger.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Fornisce un meccanismo per il chiamante al codice di esecuzione nel thread del debugger.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Creare un nodo di applicazioni associato a un provider di documento specifico.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Genera un evento generico all'interfaccia `IApplicationDebugger` del debugger.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Determina il thread corrente di bloccare e invia una notifica di errore all'IDE del debugger.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Determina se un debugger just\-in\-time \(JIT\) viene registrato.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Determina se il debug JIT è host muti registrazione automatica di debug.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Aggiunge un provider globale del contesto di un'espressione a questa applicazione.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Rimuove un provider globale di contesto di un'espressione da questa applicazione.|