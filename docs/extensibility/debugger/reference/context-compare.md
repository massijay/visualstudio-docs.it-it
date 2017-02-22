---
title: "CONTEXT_COMPARE | Microsoft Docs"
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
  - "CONTEXT_COMPARE"
helpviewer_keywords: 
  - "Enumerazione CONTEXT_COMPARE"
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

specifica i criteri per confrontare due contesti di memoria.  
  
## Sintassi  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```c#  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## Membri  
 CONTEXT\_EQUAL  
 Cercare il primo contesto di memoria nell'elenco equivalente al contesto di destinazione di memoria.  
  
 CONTEXT\_LESS\_THAN  
 Cercare il primo contesto di memoria nell'elenco minore del contesto di destinazione di memoria.  
  
 CONTEXT\_GREATER\_THAN  
 Cercare il primo contesto di memoria nell'elenco maggiore del contesto di destinazione di memoria.  
  
 CONTEXT\_LESS\_THAN\_OR\_EQUAL  
 Cercare il primo contesto di memoria nell'elenco che è minore o uguale al contesto di destinazione di memoria.  
  
 CONTEXT\_GREATER\_THAN\_OR\_EQUAL  
 Cercare il primo contesto di memoria nell'elenco maggiore o uguale al contesto di destinazione di memoria.  
  
 CONTEXT\_SAME\_SCOPE  
 Cercare il primo contesto di memoria nell'elenco nello stesso ambito del contesto di destinazione di memoria.  
  
 CONTEXT\_SAME\_FUNCTION  
 Cercare il primo contesto di memoria nell'elenco nella stessa funzione dell'ambito di destinazione di memoria.  
  
 CONTEXT\_SAME\_MODULE  
 Cercare il primo contesto di memoria nell'elenco nello stesso modulo del contesto di destinazione di memoria.  
  
 CONTEXT\_SAME\_PROCESS  
 Cercare il primo contesto di memoria nell'elenco nello stesso processo del contesto di destinazione di memoria.  
  
## Note  
 Passato come argomento [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) al metodo.  
  
 Questi valori vengono utilizzati per trovare il primo contesto di memoria in un elenco che soddisfa i criteri specificati di confronto.  Un contesto di memoria viene fornito un elenco dei contesti di memoria per compararsi con il metodo di `IDebugMemoryContext2::Compare` .  Il primo contesto di memoria nell'elenco per il quale l'operatore di confronto è `true` viene quindi restituito.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)