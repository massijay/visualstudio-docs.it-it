---
title: "EVENTATTRIBUTES | Microsoft Docs"
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
  - "EVENTATTRIBUTES"
helpviewer_keywords: 
  - "Enumerazione EVENTATTRIBUTES"
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica gli attributi dell'evento.  
  
## Sintassi  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```c#  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## Membri  
 EVENT\_ASYNCHRONOUS  
 Indica che l'evento è asincrono e alcuna risposta all'evento è necessaria.  
  
 EVENT\_SYNCHRONOUS  
 Indica che l'evento è sincrono, risposta all'[ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)utilizzo di.  
  
 EVENT\_STOPPING  
 Indica che si tratta di un evento bloccato.  Deve essere combinati con `EVENT_ASYNCHRONOUS` o `EVENT_SYNCHRONOUS`.  
  
 EVENT\_ASYNC\_STOP  
 Indica un evento bloccato asincrono.  Non è attualmente tale evento.  Questo flag è solo un segnaposto.  
  
 EVENT\_SYNCHRONIZATION\_STOP  
 Indica un evento bloccato sincrono \(una combinazione di `EVENT_SYNCHRONOUS` e di `EVENT_STOPPING`\).  Questo valore viene utilizzato dal motore \(DE\) di debug quando invia un evento bloccato.  La risposta viene effettuata tramite una chiamata a [Esegui](../../../extensibility/debugger/reference/idebugprogram2-execute.md)[Passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md), o [Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT\_IMMEDIATE  
 Indica un evento che viene inviata immediatamente e in modo sincrono all'IDE.  Questo flag viene combinato con altri flag come `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, o `EVENT_SYNC_STOP` per indicare il tipo di evento e il fatto che il meccanismo di risposta \(se presenti\) è noto.  
  
 EVENT\_EXPRESSION\_EVALUATION  
 L'evento è un risultato della valutazione di un'espressione.  
  
## Note  
 Questi valori vengono passati nel parametro di `dwAttrib` [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) del metodo.  
  
 Questi valori possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)