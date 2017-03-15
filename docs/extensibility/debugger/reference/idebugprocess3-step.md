---
title: "IDebugProcess3::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Step"
helpviewer_keywords: 
  - "IDebugProcess3::Step"
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Causa il processo dell'istruzione o all'istruzione di punto uno.  
  
> [!NOTE]
>  Questo metodo deve essere utilizzato al posto di [Passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## Sintassi  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```c#  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### Parametri  
 `pThread`  
 \[in\]  [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Un oggetto che rappresenta il thread che viene eseguito l'istruzione.  
  
 `sk`  
 \[in\]  Uno [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) dei valori.  
  
 `step`  
 \[in\]  Uno [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) dei valori.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario restituisce il codice di errore.  
  
## Note  
 Nel caso vi sia una sincronizzazione dei thread o comunicazione tra i thread, gli altri thread nel processo devono essere eseguiti quando un particolare thread è l'uscita.  
  
 **Avviso** non invia un evento bloccato o un evento \(sincrono\) immediato a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) contempo questa chiamata, in caso contrario il debugger può bloccare.  
  
## Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)