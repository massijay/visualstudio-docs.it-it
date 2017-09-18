---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Consente di \(o\) impedisce la valutazione di un'espressione si verifichi sul thread specificato, anche se il programma è stato interrotto.  
  
## Sintassi  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```c#  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### Parametri  
 `pOriginatingProgram`  
 \[in\]  [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) un oggetto che rappresenta il programma che sta valutando un'espressione.  
  
 `dwTid`  
 \[in\]  Specifica l'identificatore del thread.  
  
 `dwEvalFlags`  
 \[in\]  Una combinazione di flag [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) dall'enumerazione che specificano come la valutazione è necessario eseguire.  
  
 `pExprCallback`  
 \[in\]  [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Un oggetto da utilizzare per inviare gli eventi di debug che si verificano durante la valutazione di espressioni.  
  
 `fWatch`  
 \[in\]  Se diverso da zero \(`TRUE`\), consente la valutazione di espressioni nel thread identificato da `dwTid`; in caso contrario, lo zero \(`FALSE`\) impedisce la valutazione di espressioni nel thread.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Quando l'amministratore \(SDM\) di debug della sessione parte di un programma, identificato dal parametro di `pOriginatingProgram` , valutare un'espressione, notifica tutti gli altri programmi connessi chiamando il metodo.  
  
 La valutazione di espressioni in un programma può causare la generazione del codice in esecuzione in un altro, a causa della valutazione della funzione o di valutazione delle proprietà di `IDispatch` .  Per questo motivo, questo metodo consente alla valutazione delle espressioni funzioni e completi anche se il thread può essere suddiviso in questo programma.  
  
## Vedere anche  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)