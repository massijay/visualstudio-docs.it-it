---
title: "Interfaccia IDebugApplicationNode100 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugApplicationNode100"
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Interfaccia IDebugApplicationNode100
L'interfaccia `IDebugApplicationNode100` estendere la funzionalità [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  È possibile ottenere un'istanza di questa interfaccia chiamando QueryInterface in un'implementazione [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  L'interfaccia viene implementata da PDM v10.0 e maggiore.  Trovato in activdbg100.h.  
  
## Metodi  
 L'interfaccia `IDebugApplicationNode100` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Ottiene i documenti di testo che sono invisibili al filtro specificato.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Determina se il documento specificato appartiene a uno dei nodi figlio del nodo.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Imposta il filtro su una determinata implementazione [Interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md).  Consente ai debugger di script filtrare nodi figlio dell'applicazione generati dal compilatore in modo che il PDM più non inviare gli eventi quando i nodi vengono creati o rimossi.  Per impostazione predefinita, tutti i nodi saranno inviati.|