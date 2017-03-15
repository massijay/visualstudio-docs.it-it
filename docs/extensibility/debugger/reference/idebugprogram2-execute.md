---
title: "IDebugProgram2::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Execute"
helpviewer_keywords: 
  - "IDebugProgram2::Execute"
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Continua a eseguire il programma da uno stato interrotto.  Tutto lo stato precedente di esecuzione \(ad esempio un passaggio\) viene cancellato e l'avvio del programma che esegue nuovamente.  
  
> [!NOTE]
>  Il metodo è deprecato.  In alternativa, utilizzare il metodo [Esegui](../../../extensibility/debugger/reference/idebugprocess3-execute.md).  
  
## Sintassi  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```c#  
int Execute();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Quando l'utente avvia l'esecuzione da uno stato arrestato in thread di un altro programma, questo metodo viene chiamato in questo programma.  Questo metodo viene chiamato quando l'utente seleziona il comando di **Avvia** dal menu Debug dell'IDE.  L'implementazione di questo metodo può essere sufficiente chiamando [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md) il metodo sul thread corrente nel programma.  
  
> [!WARNING]
>  Non inviare un evento bloccato o un evento \(sincrono\) immediato su [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) come gestire questa chiamata, in caso contrario il debugger può bloccare.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)