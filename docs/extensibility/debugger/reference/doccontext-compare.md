---
title: "DOCCONTEXT_COMPARE | Microsoft Docs"
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
  - "DOCCONTEXT_COMPARE"
helpviewer_keywords: 
  - "Enumerazione DOCCONTEXT_COMPARE"
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica i criteri per confrontare due contesti del documento.  
  
## Sintassi  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```c#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## Membri  
 DOCCONTEXT\_EQUAL  
 Cercare il primo contesto del documento nell'elenco equivalente al contesto di destinazione del documento.  
  
 DOCCONTEXT\_LESS\_THAN  
 Cercare il primo contesto del documento nell'elenco minore del contesto di destinazione del documento.  
  
 DOCCONTEXT\_GREATER\_THAN  
 Cercare il primo contesto del documento nell'elenco maggiore del contesto di destinazione del documento.  
  
 DOCCONTEXT\_SAME\_DOCUMENT  
 Cercare il primo contesto del documento nell'elenco nello stesso documento come contesto di destinazione del documento.  
  
## Note  
 Passato come argomento [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) al metodo.  
  
 Questi valori vengono utilizzati per specificare i criteri di confronto per cercare il primo contesto del documento in un elenco.  Un contesto del documento viene fornito un elenco dei contesti di documento per compararsi con il metodo di `IDebugDocumentContext2::Compare` .  Il primo contesto del documento nell'elenco per il quale l'operatore di confronto è `true` viene quindi restituito.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)