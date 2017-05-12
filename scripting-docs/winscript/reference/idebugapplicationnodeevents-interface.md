---
title: "Interfaccia IDebugApplicationNodeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugApplicationNodeEvents"
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugApplicationNodeEvents
Fornisce l'interfaccia eventi per l'interfaccia `IDebugApplicationNode`.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugApplicationNodeEvents` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Gestisce l'evento quando un nodo figlio viene aggiunto a un oggetto del nodo dell'applicazione di debug.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Gestisce l'evento quando un nodo figlio viene rimosso da un oggetto del nodo dell'applicazione di debug.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Gestisce l'evento per indicare che l'oggetto del nodo dell'applicazione di debug è stato rimosso da un nodo padre.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Gestisce l'evento per indicare che l'oggetto del nodo dell'applicazione di debug è stato associato a un nodo padre.|  
  
## Vedere anche  
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)