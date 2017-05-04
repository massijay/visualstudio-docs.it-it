---
title: "Interfaccia IDebugDocumentTextEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugDocumentTextEvents"
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugDocumentTextEvents
Fornisce eventi che segnalano le modifiche al documento di testo collegato.  
  
> [!NOTE]
>  Le modifiche di testo di documento quando gli eventi su questa generazione dell'interfaccia.  I gestori eventi possono recuperare il nuovo testo tramite l'interfaccia `IDebugDocumentText`.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugDocumentTextEvents` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Indica che il documento sottostante è stato eliminato e non è più valido|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Indica che il nuovo testo è stato aggiunto al documento|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Indica che il testo è stato rimosso dal documento.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Indica che il testo è stato sostituito.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Indica che gli attributi di testo associati all'intervallo sottostante di posizione di carattere sono stati modificati.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Indica che gli attributi di documento sono stati modificati.|