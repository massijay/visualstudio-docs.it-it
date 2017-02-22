---
title: "Analizzatore di espressioni | Microsoft Docs"
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
  - "espressioni [Debugging SDK]"
  - "debug [debug SDK], la valutazione di espressioni"
  - "valutazione di espressioni"
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Analizzatore di espressioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli analizzatori \(EE\) di espressioni che esaminano la sintassi di un linguaggio per analizzare e valutare variabili ed espressioni in fase di esecuzione, consentendo li da visualizzare dall'utente quando l'ide è in modalità di interruzione.  
  
## Utilizzando gli analizzatori di espressioni  
 Le espressioni vengono create [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) utilizzando il metodo, come segue:  
  
1.  il motore di debug \(DE\) implementa [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) l'interfaccia.  
  
2.  Il pacchetto di debug ottiene un oggetto di `IDebugExpressionContext2` [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) da un'interfaccia e chiama quindi il metodo di `IDebugStackFrame2::ParseText` per ottenere [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) un oggetto.  
  
3.  Il pacchetto di debug chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) il metodo o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) il metodo per ottenere il valore dell'espressione.  `IDebugExpression2::EvaluateAsync` viene chiamato dal comando\/finestra di controllo immediato.  Tutti gli altri componenti dell'interfaccia utente chiamano `IDebugExpression2::EvaluateSync`.  
  
4.  Il risultato della valutazione di un'espressione è [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) un oggetto, che contiene il nome, il tipo e il valore del risultato della valutazione di un'espressione.  
  
 Durante la valutazione di un'espressione, l'EE richiede le informazioni da parte del provider del simbolo.  Il provider del simbolo vengono fornite informazioni sui simboli utilizzato per l'identificazione e la comprensione dell'espressione analizzata.  
  
 Quando la valutazione asincrona dell'espressione è completa, un evento asincrono viene inviato da DE tramite gestione \(SDM\) di debug della sessione per notificare all'IDE che la valutazione delle espressioni è completa.  Quando la valutazione sincrona di espressione viene completata, il risultato della valutazione viene restituito dalla chiamata al metodo di `IDebugExpression2::EvaluateSync` .  
  
## note di implementazione  
 I motori di debug di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] previsto per comunicare con l'analizzatore di espressioni che utilizza le interfacce \(CLR\) di Common Language Runtime.  Di conseguenza, un analizzatore di espressioni che funziona con i motori di debug di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve supportare il CLR \(un elenco completo di tutte le interfacce di debug di CLR è disponibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]\).  
  
## Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)