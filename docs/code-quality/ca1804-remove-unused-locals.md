---
title: "CA1804: rimuovere locali non utilizzati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords: 
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1804: rimuovere locali non utilizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo dichiara una variabile locale, ma non utilizza la variabile se non come destinatario di un'istruzione di assegnazione.  Affinché venga eseguita un'analisi tramite questa regola, l'assembly testato deve essere compilato con informazioni di debug e il file di database del programma associato \(pdb\) deve essere disponibile.  
  
## Descrizione della regola  
 Le variabili locali inutilizzate e le assegnazioni non necessarie comportano un aumento delle dimensioni dell'assembly e una riduzione delle prestazioni.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere o utilizzare la variabile locale.  Si noti che il compilatore C\# incluso con [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] rimuove le variabili locali inutilizzate quando l'opzione `optimize` è attivata.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola se la variabile è stata creata dal compilatore.  L'esclusione di un avviso da questa regola o la disattivazione della regola è sicura anche se le prestazioni e la manutenzione del codice non sono prioritarie.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate alcune variabili locali inutilizzate.  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-cs[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## Regole correlate  
 [CA1809: Evitare un numero eccessivo di variabili locali](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Rivedere i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)