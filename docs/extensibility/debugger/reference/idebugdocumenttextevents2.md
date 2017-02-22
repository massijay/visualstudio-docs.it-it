---
title: "IDebugDocumentTextEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2"
helpviewer_keywords: 
  - "Interfaccia IDebugDocumentTextEvents2"
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene utilizzata per notificare a Visual Studio sulle modifiche al documento di origine disponibili nel motore di debug.  
  
## Sintassi  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per supportare apportare modifiche al codice sorgente.  Questa interfaccia in genere viene implementata nello stesso oggetto che implementa [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) l'interfaccia.  
  
## Note per i chiamanti  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ottiene questa interfaccia con una chiamata al metodo di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> .  L'interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> viene ottenuta da una chiamata al metodo di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> .  L'interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> si ottiene chiamando [QueryInterface](/visual-cpp/atl/queryinterface) il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) metodo su un'interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugDocumentTextEvents2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica che l'intero documento è stato eliminato.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica al pacchetto di debug che il testo è stato immesso nel documento.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica al pacchetto di debug che il testo è stato rimosso dal documento.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica al pacchetto di debug che il testo è stato sostituito nel documento.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica al pacchetto di debug che gli attributi di testo sono stati aggiornati nel documento.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al ricevitore dell'evento che gli attributi del documento sono stati aggiornati.|  
  
## Note  
 Solo i motori di debug che forniscono i propri documenti approfitterebbero dell'interfaccia di `IDebugDocumentTextEvent2` .  Un esempio è dato da un motore di debug di script.  Nel corso dell'interpretazione degli script, il nuovo codice sorgente può essere generato non presente in un file su disco e è noto solo a DE.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)