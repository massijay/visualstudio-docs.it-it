---
title: "IDebugProcess3::Continue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Continue"
helpviewer_keywords: 
  - "IDebugProcess3::Continue"
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Continua a eseguire questo processo in stato di interruzione.  Tutto lo stato precedente di esecuzione \(ad esempio un passaggio\) viene mantenuto einizio del processo che esegue nuovamente.  
  
> [!NOTE]
>  Questo metodo deve essere utilizzato al posto di [Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## Sintassi  
  
```cpp  
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
 \[in\]  [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Un oggetto che rappresenta il thread per continuare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Note  
 Questo metodo viene chiamato su questo processo indipendentemente dal numero di processi sono eseguire il debug, o quali processo ha generato l'evento bloccato.  L'implementazione di deve mantenere lo stato precedente di esecuzione \(ad esempio un passaggio\) e continuare l'esecuzione come se non fosse stata interrotta mai prima del completamento dell'esecuzione precedente.  Ovvero se un thread in questo processo stesse tramite un'operazione di esegui istruzione\/routine e è stato arrestato perché un altro processo interrotto e quindi `Continue` sono stati chiamati, il thread specificato deve completare originale esegue l'operazione.  
  
 **Avviso** non invia un evento bloccato o un evento \(sincrono\) immediato a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) contempo questa chiamata, in caso contrario il debugger può bloccare.  
  
## Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)