---
title: "IDebugPortEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2"
helpviewer_keywords: 
  - "Interfaccia IDebugPortEvents2"
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia a un listener \(in genere l'amministratore di debug della sessione \[SDM\] o un modulo di debug\) del processo e creazione e l'eliminazione del programma su una porta specifica.  Queste informazioni possono essere utilizzate per offrire un aspetto in tempo reale dei processi e pianifica l'esecuzione sulla porta.  
  
## Sintassi  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## Note per gli implementatori  
 Visual Studio in genere implementa questa interfaccia per ricevere le notifiche sulla creazione e l'eliminazione del programma.  Il modulo di debug anche possibile implementare questa interfaccia per l'ascolto di tali eventi della porta.  
  
## Note per i chiamanti  
 Tutte [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) le interfacce è possibile eseguire una query per un'interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> .  Quindi il metodo di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> per `IDebugPortEvents2` viene chiamato nell'interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> per ottenere un'interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> .  Infine, il metodo di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> viene chiamato per l'invio di eventi con [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) il metodo.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente viene illustrato il metodo di `IDebugPortEvents2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Invia gli eventi che descrivono la creazione e l'eliminazione dei processi e dei programmi sulla porta.|  
  
## Note  
 `IDebugPortEvents2` viene utilizzato da SDM ai programmi di debug in esecuzione in un processo già si sta eseguendo il debug.  
  
 Gli eventi della porta vengono passati a SDM da questa interfaccia.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)