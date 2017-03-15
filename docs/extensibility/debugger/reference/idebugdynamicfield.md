---
title: "IDebugDynamicField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDynamicField"
helpviewer_keywords: 
  - "Interfaccia IDebugDynamicField"
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDynamicField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta un tipo di variabile.  
  
## Sintassi  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata dai provider del simbolo come classe base per qualsiasi tipo che può essere determinato in fase di esecuzione.  Si tratta del codice gestito solo.  
  
## Note per i chiamanti  
 Questa interfaccia rappresenta una classe di base da cui di più specializzato le interfacce può essere derivato.  
  
## Metodi nell'ordine di Vtable  
 Questa interfaccia non fornisce metodi diverse da quelle ereditate da `IDebugField`.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)