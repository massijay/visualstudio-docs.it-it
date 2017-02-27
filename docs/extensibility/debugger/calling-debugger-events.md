---
title: "Eventi di chiamata del Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], eventi"
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Eventi di chiamata del Debugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli eventi nelle sessioni di debug vengono eseguite in un ordine specifico.  
  
## Descrizione  
 Per comprendere il modello di chiamate tra il motore di \(DE\) debug e la sessione di debug amministratore \(SDM\), il codice rappresenta l'ordine degli eventi che si verificano in una sessione di debug tipica:  
  
1.  [La connessione e la disconnessione di un programma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [avviare il debugger](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [terminare un programma](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [creare un punto di interruzione](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Quando un punto di interruzione è associato o è distinto](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Errori del punto di interruzione](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Raggiunto un punto di interruzione](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Per eliminare un punto di interruzione](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Fornire modalità di interruzione](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Entrare in modalità di interruzione](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Valutazione di espressioni in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Gestione delle eccezioni](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## Vedere anche  
 [Creazione di un motore di Debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)