---
title: "Interfaccia ISimpleConnectionPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia ISimpleConnectionPoint"
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia ISimpleConnectionPoint
Fornisce un modo semplice per la descrizione e l'enumerazione degli eventi generati su un punto di connessione specifica.  Questa interfaccia anche semplice collegare un oggetto `IDispatch` tali eventi.  L'interfaccia viene implementata dall'amministratore di processo \(PDM\) di debug e utilizzata dal motore di gestione di script.  
  
 Questa interfaccia è disponibile da `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `ISimpleConnectionPoint` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Stabilisce una connessione tra l'oggetto semplice del punto di connessione e il sink del client.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Restituisce il DISPID e il nome di ogni evento in un intervallo specificato degli eventi.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Restituisce il numero di eventi esposti su questa interfaccia.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Termina una connessione consultiva precedentemente stabilita tramite `ISimpleConnectionPoint::Advise`.|  
  
## Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)