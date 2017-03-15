---
title: "Contesto del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contesti [debug SDK], debug"
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Contesto del codice
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che esegue il debug, un**contesto di codice**:  
  
-   Fornisce un'astrazione di una posizione nel codice come noto al motore di debug \(DE\).  Per la maggior parte delle architetture in fase di esecuzione corrente, un contesto di codice può essere considerato come un indirizzo nel flusso di istruzioni di un programma.  Per i linguaggi non tradizionali, in cui il codice non può essere rappresentato dalle istruzioni, un contesto di codice può essere rappresentato tramite altri mezzi.  
  
-   Viene descritta la posizione corrente nel flusso di esecuzione del programma sottoposto a debug.  
  
-   Esiste solo quando un programma è stato interrotto a un punto di interruzione.  
  
-   Dispone di un contesto associato al documento.  
  
-   Viene implementata da un'interfaccia di [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .  
  
## Vedere anche  
 [Contesto del documento](../../extensibility/debugger/document-context.md)   
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)