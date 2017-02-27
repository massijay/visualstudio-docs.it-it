---
title: "IDebugDocument2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2"
helpviewer_keywords: 
  - "Interfaccia IDebugDocument2"
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocument2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta un documento di origine.  
  
## Sintassi  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## Note per gli implementatori  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] in genere implementa.  Il modulo \(DE\) di debug anche possibile implementare questa interfaccia quando necessario fornire il codice sorgente e il database di origine non esiste sul disco.  In tali casi, il DE anche implementi [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) e [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) interfacce nonché alcuni metodi aggiuntivi [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) e [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) le interfacce.  
  
## Note per i chiamanti  
 I metodi di `IDebugDocumentContext2`, in `IDebugDisassemblyStream2`, in `IDebugDocumentPosition2`e le interfacce di `IDebugActivateDocumentEvent2` restituiscono questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugDocument2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ottiene il nome del documento in uno dei form.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ottiene l'identificatore di classe del documento.|  
  
## Note  
 Questa interfaccia è implementata solo quando il DE fornisce il codice sorgente.  Ad esempio, quando si esegue il debug di script in una pagina HTML, l'oggetto fornisce di DE il codice sorgente perché l'origine viene scaricata in modo dinamico o generato e non esiste come file su disco.  Quando si esegue il debug dei linguaggi tradizionali, ad esempio C\+\+, questa interfaccia non deve essere distribuita.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)   
 [GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)