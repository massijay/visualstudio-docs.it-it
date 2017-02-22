---
title: "IDebugProcess3::Execute | Microsoft Docs"
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
  - "IDebugProcess3::Execute"
helpviewer_keywords: 
  - "IDebugProcess3::Execute"
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Continua a eseguire questo processo in stato di interruzione.  Tutto lo stato precedente di esecuzione \(ad esempio un passaggio\) viene cancellato e l'avvio di processo che esegue nuovamente.  
  
> [!NOTE]
>  Questo metodo deve essere utilizzato al posto di [Esegui](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## Sintassi  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### Parametri  
 `pThread`  
 \[in\]  [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Un oggetto che rappresenta il thread per l'esecuzione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Note  
 Quando l'utente avvia l'esecuzione da uno stato arrestato in thread di un altro processo, questo metodo viene chiamato su questo processo.  Questo metodo viene chiamato quando l'utente seleziona il comando di **Avvia** dal menu Debug dell'IDE.  L'implementazione di questo metodo può essere sufficiente chiamando [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md) il metodo sul thread corrente del processo.  
  
> [!WARNING]
>  Non inviare un evento bloccato o un evento \(sincrono\) immediato su [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) come gestire questa chiamata, in caso contrario il debugger può bloccare.  
  
## Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)