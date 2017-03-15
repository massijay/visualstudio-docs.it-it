---
title: "IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica se l'eccezione debba essere passata al programma sottoposto a debug durante l'esecuzione riprende, o se l'eccezione viene rimossa.  
  
## Sintassi  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```c#  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### Parametri  
 `fPass`  
 \[in\]  Diverso da zero \(`TRUE`\) se l'eccezione viene passata al programma sottoposto a debug durante l'esecuzione riprende, o zero \(`FALSE`\) se l'eccezione viene rimossa.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Chiamare questo metodo non comporta alcun codice venga eseguito nel programma sottoposto a debug.  La chiamata viene solo di impostare lo stato di dopo l'esecuzione di codice.  Ad esempio, le chiamate [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) al metodo possono restituire `S_OK` con [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md). campo di`dwState` impostato su `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 L'ide possa ricevere [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) l'evento e chiamare [Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md) il metodo.  Il motore \(DE\) di debug deve avere un comportamento predefinito per gestire il caso in cui il metodo di `PassToDebuggee` non viene chiamato.  
  
## Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md)