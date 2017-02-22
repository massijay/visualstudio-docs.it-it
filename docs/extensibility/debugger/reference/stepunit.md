---
title: "STEPUNIT | Microsoft Docs"
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
  - "STEPUNIT"
helpviewer_keywords: 
  - "Enumerazione STEPUNIT"
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# STEPUNIT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica gli unit test del passaggio per avanzare.  
  
## Sintassi  
  
```cpp#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```c#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## Membri  
 STEP\_STATEMENT  
 Passaggi dall'istruzione.  
  
 STEP\_LINE  
 Passaggi dalla riga.  
  
 STEP\_INSTRUCTION  
 Passaggi dall'istruzione.  
  
## Note  
 Passato come argomento [Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md) al metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md)