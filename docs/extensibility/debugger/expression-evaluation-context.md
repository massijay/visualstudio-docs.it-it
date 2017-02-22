---
title: "Contesto di valutazione dell&#39;espressione | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "valutazione dell'espressione, contesto"
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Contesto di valutazione dell&#39;espressione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che esegue il debug, **un contesto di valutazione di espressioni**:  
  
-   Rappresenta un contesto per la valutazione di espressioni.  In genere, un contesto di valutazione corrisponde all'ambito lessicale all'interno di cui valutare variabili, parametri, funzioni e metodi.  Ad esempio, un contesto di valutazione di espressioni associato a uno stack frame fornire un contesto per esaminare le variabili locali, i parametri dei metodi e i membri della classe \(se applicabile\).  
  
-   Si verifica quando un programma è stato interrotto a un punto di interruzione.  L'espressione stessa è una struttura di dati che rappresenta un'espressione analizzata che è pronta per associare e valutano nel contesto specificato.  
  
     In maggiore dettaglio, le espressioni vengono create [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) utilizzando il metodo.  Quando un'espressione viene valutata, viene generata una stringa stampabile che contiene il nome e il tipo di variabile o argomento e il relativo valore.  Questa stringa viene visualizzata nella finestra Espressioni di controllo o nella finestra variabili locali dell'IDE.  
  
     Fornito `BSTR` e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) un'interfaccia, un motore di \(DE\) debug possibile creare [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) un'interfaccia analizza un'espressione.  Fornita un'interfaccia di `IDebugExpression2` , il DE possibile ottenere un valore con la valutazione sincrona o asincrona di espressione.  Questo valore, con il nome e il tipo della variabile o degli argomenti, viene inviato all'IDE per la visualizzazione.  
  
## Vedere anche  
 [Interfacce di valutazione di espressioni](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)