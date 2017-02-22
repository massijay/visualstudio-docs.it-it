---
title: "Modifica del valore di una variabile locale | Microsoft Docs"
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
  - "debug [debug SDK], la valutazione di espressioni"
  - "valutazione dell'espressione, la modifica di valori a livello di codice"
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Modifica del valore di una variabile locale
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando viene digitato un nuovo valore nel campo del valore di **variabili locali** finestra, il pacchetto di debug passa la stringa, durante la digitazione, l'analizzatore di espressioni \(EE\). L'analizzatore di Espressioni valuta questa stringa può contenere un semplice valore o un'espressione, e archivia il valore risultante locale associato.  
  
 Questo viene fornita una panoramica del processo di modifica del valore di una variabile locale:  
  
1.  Dopo aver inserito il nuovo valore, Visual Studio chiama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) sul [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto associato all'oggetto locale.  
  
2.  `IDebugProperty2::SetValueAsString` esegue le attività seguenti:  
  
    1.  Valuta la stringa per produrre un valore.  
  
    2.  Associa l'oggetto associato [IDebugField](../../extensibility/debugger/reference/idebugfield.md) per ottenere un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) oggetto.  
  
    3.  Converte il valore in una serie di byte.  
  
    4.  Chiamate [SetValue](../Topic/IDebugObject::SetValue.md) inserire byte del valore in memoria in modo che il programma in fase di debug può accedervi.  
  
3.  Visual Studio aggiorna il **variabili locali** visualizzare \(vedere [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md) per informazioni dettagliate\).  
  
 Questa procedura viene anche utilizzata per modificare il valore di una variabile nel **espressioni di controllo** finestra con la differenza che è il `IDebugProperty2` oggetto associato al valore della variabile locale che viene utilizzato al posto del `IDebugProperty2` associato locale stesso.  
  
## Contenuto della sezione  
 [Esempio di implementazione di modifica dei valori](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Utilizza l'esempio MyCEE per entrare nel processo di modifica dei valori.  
  
## Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)