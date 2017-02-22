---
title: "CA1823: Evitare campi privati non utilizzati | Microsoft Docs"
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
  - "AvoidUnusedPrivateFields"
  - "CA1823"
helpviewer_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1823: Evitare campi privati non utilizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 La regola viene riportata quando esiste un campo privato nel codice, ma non viene utilizzato da alcun percorso del codice.  
  
## Descrizione della regola  
 Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il campo o aggiungere il codice che lo utilizza.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura.  
  
## Regole correlate  
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Rivedere i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)