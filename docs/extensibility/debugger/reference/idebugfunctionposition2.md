---
title: "IDebugFunctionPosition2 | Microsoft Docs"
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
  - "IDebugFunctionPosition2"
helpviewer_keywords: 
  - "Interfaccia IDebugFunctionPosition2"
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta una posizione astratta di una funzione in un documento di origine.  
  
## Sintassi  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore di \(DE\) debug implementa questa interfaccia per rappresentare la posizione di una funzione all'interno di un documento di origine.  
  
## Note per i chiamanti  
 Questa interfaccia è disponibile come [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) componente di un'unione \(in particolare, [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) una struttura\) appartenenti a sua volta [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) della struttura, utilizzata per la creazione di un punto di interruzione in attesa.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugFunctionPosition2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Ottiene il nome della funzione che si tratta di.|  
|[GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)|Ottiene l'offset dall'inizio della funzione.|  
  
## Note  
 La posizione è rappresentata da questa interfaccia è basato su testo, in particolare, [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) una struttura.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)