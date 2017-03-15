---
title: "IDebugDocumentContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2"
helpviewer_keywords: 
  - "IDebugDocumentContext2"
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocumentContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta una posizione in un documento del file di origine.  
  
## Sintassi  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia come parte del supporto per il debug a livello di codice sorgente.  Oltre a una posizione nel codice sorgente, l'interfaccia fornisce metodi per confrontare i contesti e spostarsi all'interno di un documento di codice sorgente.  
  
## Note per i chiamanti  
 I metodi in diverse interfacce, il [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) più comune e [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) le interfacce, restituiscono l'interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugDocumentContext2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)|Ottiene il documento contenente tale contesto del documento.|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Ottiene il nome visibile del documento contenente tale contesto del documento.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Recupera un elenco di tutti i contesti di codice associati al contesto del documento.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Ottiene il linguaggio associato al contesto del documento.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo dell'istruzione del file del contesto del documento.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Ottiene il file nell'intervallo di origine di questo contesto del documento.|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Confronta il contesto di documento in una matrice specificata i contesti di documento.|  
|[Ricerca](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Consente di spostare il contesto del documento da un numero specificato di istruzioni o righe.|  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)