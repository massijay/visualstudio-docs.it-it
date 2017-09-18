---
title: "IDebugProgram2::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Step"
helpviewer_keywords: 
  - "IDebugProgram2::Step"
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esegue un'operazione.  
  
> [!NOTE]
>  Il metodo è deprecato.  In alternativa, utilizzare il metodo [Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## Sintassi  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```c#  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### Parametri  
 `pThread`  
 \[in\]  [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Un oggetto che rappresenta il thread che viene eseguito l'istruzione.  
  
 `sk`  
 \[in\]  Un valore [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) dell'enumerazione che specifica il tipo di passaggio.  
  
 `step`  
 \[in\]  Un valore [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) dell'enumerazione che specifica lo unit test del passaggio \(ad esempio, tramite l'istruzione o l'istruzione\).  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Nel caso vi sia una sincronizzazione dei thread o comunicazione tra i thread, gli altri thread nel programma devono essere eseguiti quando un particolare thread è l'uscita.  
  
> [!WARNING]
>  Non inviare un evento bloccato o un evento \(sincrono\) immediato su [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) come gestire questa chiamata, in caso contrario il debugger può bloccare.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)