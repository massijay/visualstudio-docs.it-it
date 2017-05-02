---
title: "Interfaccia IMachineDebugManagerEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IMachineDebugManagerEvents"
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IMachineDebugManagerEvents
Modifiche dei segnali nell'elenco in esecuzione di un'applicazione gestita dall'amministratore del computer di debug.  Tale interfaccia può essere utilizzata dall'IDE del debugger per visualizzare un elenco dinamico delle applicazioni.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IMachineDebugManagerEvents` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Gestisce l'evento quando un'applicazione viene aggiunto all'elenco in esecuzione di un'applicazione.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Gestisce l'evento quando un'applicazione viene rimossa dall'elenco in esecuzione di un'applicazione.|