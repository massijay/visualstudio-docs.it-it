---
title: "CA2219: Non generare eccezioni in clausole di eccezione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotRaiseExceptionsInExceptionClauses"
  - "CA2219"
helpviewer_keywords: 
  - "CA2219"
  - "DoNotRaiseExceptionsInExceptionClauses"
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2219: Non generare eccezioni in clausole di eccezione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale, sostanziale|  
  
## Causa  
 Un'eccezione viene generata da una clausola `finally`, da una clausola di filtro o da una clausola fault.  
  
## Descrizione della regola  
 Quando un'eccezione viene generata in una clausola di eccezione, complica notevolmente il debug.  
  
 Quando un'eccezione viene generata in una clausola `finally` o in una clausola fault, la nuova eccezione nasconde l'eccezione attiva, se presente.  Tale circostanza complica il rilevamento e il debug dell'errore originale.  
  
 Quando un'eccezione viene generata in una clausola di filtro, viene intercettata automaticamente dal runtime e il filtro restituisce false.  Poiché non è possibile rilevare la differenza tra la restituzione di false e la generazione di un'eccezione da parte di un filtro,  il rilevamento e il debug di errori nella logica del filtro risultano più difficili.  
  
## Come correggere le violazioni  
 Per correggere la violazione di questa regola, non generare in modo esplicito un'eccezione da una clausola `finally`, una clausola di filtro o una clausola fault.  
  
## Esclusione di avvisi  
 Non escludere un avviso per questa regola.  Non esistono scenari in cui un'eccezione generata in una clausola di eccezione comporti un vantaggio per il codice in esecuzione.  
  
## Regole correlate  
 [CA1065: Non generare eccezioni in posizioni non previste](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## Vedere anche  
 [Avvisi di progettazione](../code-quality/design-warnings.md)