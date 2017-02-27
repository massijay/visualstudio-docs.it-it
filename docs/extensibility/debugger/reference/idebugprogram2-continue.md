---
title: "IDebugProgram2::Continue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Continue"
helpviewer_keywords: 
  - "IDebugProgram2::Continue"
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Continua a eseguire il programma da uno stato interrotto.  Tutto lo stato precedente di esecuzione \(ad esempio un passaggio\) viene mantenuto e l'avvio del programma che esegue nuovamente.  
  
> [!NOTE]
>  Il metodo è deprecato.  In alternativa, utilizzare il metodo [Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md).  
  
## Sintassi  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### Parametri  
 `pThread`  
 \[in\]  [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) un oggetto che rappresenta il thread.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene chiamato in questo programma indipendentemente dal numero di programmi nel debug, o quali programma ha generato l'evento bloccato.  L'implementazione di deve mantenere lo stato precedente di esecuzione \(ad esempio un passaggio\) e continuare l'esecuzione come se non fosse stata interrotta mai prima del completamento dell'esecuzione precedente.  Ovvero se un thread in questo programma stesse tramite un'operazione di esegui istruzione\/routine e è stato arrestato perché un altro programma interrotto e quindi questo metodo sono stati chiamati, il programma deve completare originale esegue l'operazione.  
  
> [!WARNING]
>  Non inviare un evento bloccato o un evento \(sincrono\) immediato su [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) come gestire questa chiamata, in caso contrario il debugger può bloccare.  
  
## Vedere anche  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)