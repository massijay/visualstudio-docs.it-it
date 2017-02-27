---
title: "Stack frame | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "stack frame, debug"
  - "debug [Debugging SDK], stack frame"
  - "stack frame"
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Stack frame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In termini di architettura del debugger, **uno stack frame**:  
  
-   è un'astrazione di uno stack che fornisce il contesto di esecuzione di un thread.  Un thread esegue sempre all'interno di una funzione.  Uno stack frame vengono utilizzate le variabili locali della funzione e gli argomenti su.  Per eseguire il debug con Visual Studio, il linguaggio o l'ambiente che viene eseguito il debug deve supportare gli stack frame.  
  
-   È possibile identificare quali autodescriversi e restituire il thread associato.  Uno stack frame anche possibile restituire il contesto di codice che rappresenta il puntatore all'istruzione corrente nonché i contesti associati di valutazione di espressioni e la documentazione.  
  
-   Include proprietà che descrivono il nome, il tipo e il valore delle variabili locali e gli argomenti e visualizzati in diverse finestre di debug dell'IDE.  
  
-   È [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) rappresentato da un'interfaccia, in genere creata da un motore di debug \(DE\) o da una macchina virtuale in conseguenza dell'esecuzione di un thread.  
  
## Vedere anche  
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)   
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Il motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)