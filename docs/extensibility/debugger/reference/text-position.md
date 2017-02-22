---
title: "TEXT_POSITION | Microsoft Docs"
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
  - "TEXT_POSITION"
helpviewer_keywords: 
  - "Struttura TEXT_POSITION"
ms.assetid: 6dcec574-a852-49fa-8c2e-2e71cbb5e3c6
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# TEXT_POSITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene descritta la posizione di riga nel testo specificato.  
  
## Sintassi  
  
```cpp#  
typedef struct _tagTEXT_POSITION {   
   DWORD dwLine;  
   DWORD dwColumn;  
} TEXT_POSITION;  
```  
  
```c#  
public struct TEXT_POSITION {   
   public uint dwLine;  
   public uint dwColumn;  
};  
```  
  
## Membri  
 dwLine  
 Indice della riga nel file di origine.  
  
 dwColumn  
 Offset del carattere della riga.  
  
## Note  
 Questa struttura viene utilizzata in [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) e [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) strutture.  
  
 Questa struttura viene soddisfatta da una chiamata ai metodi seguenti:  
  
-   [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)  
  
-   [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)  
  
-   [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)  
  
-   [GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)  
  
 Questa struttura passata come parametro ai seguenti metodi:  
  
-   [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)  
  
-   [onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)  
  
-   [onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)  
  
-   [onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)  
  
-   [onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)   
 [GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)   
 [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)