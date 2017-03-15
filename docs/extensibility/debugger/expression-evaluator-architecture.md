---
title: "Architettura dell&#39;analizzatore di espressioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "architettura, analizzatori di espressioni"
  - "analizzatori di espressioni, architettura"
  - "debug [debug SDK], analizzatori di espressioni"
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Architettura dell&#39;analizzatore di espressioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'integrazione di un linguaggio proprietario nel pacchetto di debug di Visual Studio si intende implementare le interfacce dell'analizzatore di espressioni \(EE\) obbligatorio espressione e chiamare il provider simbolo di runtime del linguaggio comune \(SP\) e le interfacce di associazione. Gli oggetti di SP e di binder, oltre all'indirizzo corrente di esecuzione, sono il contesto in cui le espressioni vengono valutate. Le informazioni che queste interfacce producono e usano rappresentano i concetti chiave nell'architettura di un EE.  
  
## Panoramica  
  
### L'analisi dell'espressione  
 Quando si esegue il debug di un programma, le espressioni vengono valutate per diversi motivi, ma sempre quando il programma in corso il debug è stato arrestato a un punto di interruzione \(un punto di interruzione inserito dall'utente o uno causato da un'eccezione\). È in questo momento quando Visual Studio Ottiene uno stack frame, come rappresentato dal [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia dal motore di debug \(DE\). Visual Studio chiama quindi [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia. Questa interfaccia rappresenta un contesto in cui è possano valutare le espressioni; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) è il punto di ingresso per il processo di valutazione. Fino a questo punto, tutte le interfacce vengono implementate tramite la DE.  
  
 Quando `IDebugExpressionContext2::ParseText` viene chiamato, il DE crea un'istanza di motore di esecuzione associate alla lingua del file di origine in cui si è verificato il punto di interruzione \(le DE un'istanza di SH a questo punto\). L'analizzatore di Espressioni è rappresentato dal [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaccia. Chiama quindi il DE [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per convertire l'espressione, in formato testo, in un'espressione analizzata, pronto per la valutazione. Questa espressione analizzata è rappresentata dal [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaccia. Si noti che l'espressione viene in genere analizzato e non viene valutato a questo punto.  
  
 Il DE crea un oggetto che implementa il [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia, inserisce il `IDebugParsedExpression` nell'oggetto di `IDebugExpression2` oggetto e restituisce il `IDebugExpression2` dell'oggetto da `IDebugExpressionContext2::ParseText`.  
  
### La valutazione dell'espressione  
 Visual Studio chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per valutare l'espressione analizzata. Entrambi questi metodi chiamano [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) \(`IDebugExpression2::EvaluateSync` chiama il metodo immediatamente, mentre `IDebugExpression2::EvaluateAsync` chiama il metodo tramite un thread in background\) per valutare l'espressione analizzata e restituire un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il valore e il tipo dell'espressione analizzata.`IDebugParsedExpression::EvaluateSync` utilizza il SH, indirizzo e gestore di associazione forniti per convertire l'espressione analizzata in un valore effettivo, rappresentato dal `IDebugProperty2` interfaccia.  
  
### Ad esempio  
 Dopo un punto di interruzione in un programma in esecuzione, l'utente sceglie di visualizzare una variabile di **controllo immediato** la finestra di dialogo. Questa finestra di dialogo Mostra il nome della variabile, il relativo valore e il relativo tipo. L'utente in genere possibile modificare il valore.  
  
 Quando il **controllo immediato** viene visualizzata la finestra di dialogo, il nome della variabile in corso l'analisi viene inviato come testo per [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Questo metodo restituisce un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto che rappresenta l'espressione analizzata in questo caso, la variabile.[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) viene quindi chiamato per produrre un `IDebugProperty2` oggetto che rappresenta il valore della variabile e tipo, nonché il relativo nome. È questa informazioni visualizzate.  
  
 Se l'utente cambia il valore della variabile, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) viene chiamato con il nuovo valore, che modifica il valore della variabile in memoria in modo da utilizzare quando il programma riprende l'esecuzione.  
  
 Vedere [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md) Per ulteriori informazioni su questo processo di visualizzazione dei valori delle variabili. Vedere [Modifica del valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md) Per ulteriori informazioni su come viene modificato un valore della variabile.  
  
## Contenuto della sezione  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti che vengono passati al momento il DE chiama l'analizzatore di Espressioni.  
  
 [Interfacce dell'analizzatore di espressioni di espressione chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Descrive le interfacce fondamentali necessarie quando si scrive un EE, insieme al contesto di valutazione.  
  
## Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)   
 [Modifica del valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md)