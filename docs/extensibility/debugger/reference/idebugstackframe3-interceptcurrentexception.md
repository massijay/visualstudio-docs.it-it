---
title: "IDebugStackFrame3::InterceptCurrentException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
helpviewer_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Chiamato dal debugger nello stack frame corrente quando si desidera rilevare l'eccezione corrente.  
  
## Sintassi  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```c#  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### Parametri  
 `dwFlags`  
 \[in\]  Specifica le azioni da eseguire.  Attualmente, solo [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) il valore `IEA_INTERCEPT` è supportato e deve essere specificato.  
  
 `pqwCookie`  
 \[out\]  Valore univoco che identifica un'eccezione specifica.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
 Di seguito sono la maggior parte dei risultati di errore comune.  
  
|delle modifiche a..."|Descrizione|  
|---------------------------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|L'eccezione corrente non può essere rilevata.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Il frame corrente di esecuzione non è stato trovato un gestore di nuovo.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Questo metodo non è supportato per il frame.|  
  
## Note  
 Quando viene generata un'eccezione, il controllo di notevoli miglioramenti del debugger dal runtime ai punti chiave durante il processo di gestione delle eccezioni.  Durante questi punti principali, il debugger può richiedere lo stack frame corrente se il frame desidera rilevare l'eccezione.  In questo modo, viene generata un'eccezione intercettata è essenzialmente un gestore di eccezioni immediatamente per uno stack frame, anche se lo stack frame non dispone di un gestore di eccezioni, ad esempio un blocco try\/catch nel codice programma\).  
  
 Quando il debugger desidera sapere se l'eccezione viene rilevata, chiama questo metodo per l'oggetto corrente dello stack frame.  Questo metodo è responsabile della gestione dei dettagli dell'eccezione.  Se [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) l'interfaccia non viene distribuita o il metodo di `InterceptStackException` restituisce qualsiasi errore, il debugger continua a elaborare l'eccezione generale.  
  
> [!NOTE]
>  Le eccezioni possono essere rilevate solo nel codice gestito, ovvero, quando il programma sottoposto a debug è in esecuzione nel runtime di .NET.  Naturalmente, gli implementatori di terze parti di linguaggio possono implementare `InterceptStackException` nei propri motori di debug se quindi scegliere.  
  
 Dopo aver l'intercettazione viene completata, [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) viene segnalato.  
  
## Vedere anche  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)