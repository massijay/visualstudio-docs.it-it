---
title: "Scrittura di un analizzatore di espressioni di Common Language Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analizzatori di espressioni, esercitazione"
  - "valutazione dell'espressione, esempi"
  - "esercitazione sul debug analizzatori di espressioni [debug SDK]"
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Scrittura di un analizzatore di espressioni di Common Language Runtime
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'analizzatore di espressioni \(EE\) è la parte di un motore di debug \(DE\) che gestisce la sintassi e semantica del linguaggio di programmazione che ha generato il codice in fase di debug. Le espressioni devono essere valutate nel contesto di un linguaggio di programmazione. In alcuni linguaggi, ad esempio, l'espressione "A \+ B", "la somma di A e b." In altre lingue, la stessa espressione potrebbe indicare "A o B." Pertanto, un oggetto separato EE deve essere scritto per ogni linguaggio di programmazione che genera il codice oggetto da sottoporre a debug nell'IDE di Visual Studio.  
  
 Alcuni aspetti del pacchetto di debug di Visual Studio devono interpretare il codice nel contesto del linguaggio di programmazione. Ad esempio, quando si interrompe esecuzione in un punto di interruzione, tutte le espressioni che l'utente ha digitato in un **espressioni di controllo** finestra deve essere valutata e visualizzata. Inoltre, l'utente può modificare il valore di una variabile locale digitando un'espressione in un **espressioni di controllo** finestra o nel **immediato** finestra.  
  
## In questa sezione  
 [Common Language Runtime e la valutazione di espressioni](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Viene illustrato che quando si sta integrando il linguaggio di programmazione proprietario nell'IDE di Visual Studio, la scrittura di un EE in grado di valutazione di espressioni all'interno del contesto del linguaggio proprietario consente di compilare in Microsoft intermediate language \(MSIL\) senza scrivere un motore di debug.  
  
 [Architettura dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Viene illustrato come implementare le interfacce necessarie EE e chiamare il common language runtime simbolo provider \(SP\) e interfacce di associazione.  
  
 [Registrazione di un analizzatore di espressioni](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Indica che l'analizzatore di Espressioni deve registrarsi in quanto una class factory con sia il common language runtime e gli ambienti di runtime di Visual Studio.  
  
 [Implementazione di un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Viene descritto come il processo di valutazione di un'espressione include il motore di debug \(DE\), il provider di simboli \(SP\), l'oggetto di associazione e l'analizzatore di espressioni \(EE\).  
  
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)  
 Viene descritto come, quando viene sospesa l'esecuzione, il pacchetto di debug chiama DE per ottenere un elenco di argomenti e variabili locali.  
  
 [Valutazione di un'espressione di finestra Espressioni di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Documenti come il pacchetto di debug di Visual Studio chiama DE per determinare il valore corrente di ogni espressione nell'elenco di espressioni di controllo.  
  
 [Modifica del valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Viene illustrato come modificare il valore di una variabile locale, ogni riga della finestra variabili locali è associato un oggetto che fornisce il nome, tipo e il valore corrente di una variabile locale.  
  
 [Implementazione di tipo visualizzatori e visualizzatori personalizzati](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Viene illustrato quale interfaccia deve essere implementato dal componente che per supportare i visualizzatori di tipi e i visualizzatori personalizzati.  
  
## Vedere anche  
 [Estensibilità del Debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)