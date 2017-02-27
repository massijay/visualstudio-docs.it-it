---
title: "IDebugDocumentText2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2"
helpviewer_keywords: 
  - "Interfaccia IDebugDocumentText2"
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta un documento di testo.  
  
## Sintassi  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## Note per gli implementatori  
 Il modulo \(DE\) di debug implementa questa interfaccia quando il codice sorgente che deve fornire è in formato di testo.  Poiché questo è il caso più comune, se un DE implementa [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) l'interfaccia, deve implementare anche l'interfaccia di `IDebugDocumentText2` .  
  
## Note per i chiamanti  
 utilizzare il metodo di `QueryInterface` per ottenere questa interfaccia da un'interfaccia di `IDebugDocument2` .  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi in un'interfaccia di `IDebugDocument2` , l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera la dimensione del testo in questa posizione nel documento.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera il testo nella posizione specificata nel documento.|  
  
## Note  
 Un oggetto che implementa questa interfaccia deve implementare anche l'interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> , che fornisce l'interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> per [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) un oggetto.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)