---
title: "CA1502: Evitare complessit&#224; eccessiva | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveComplexity"
  - "CA1502"
helpviewer_keywords: 
  - "CA1502"
  - "AvoidExcessiveComplexity"
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1502: Evitare complessit&#224; eccessiva
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|Category|Microsoft.Maintainability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo presenta una complessità ciclomatica eccessiva.  
  
## Descrizione della regola  
 La *complessità ciclomatica* misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali.  Una complessità ciclomatica bassa indica in genere un metodo di semplice comprensione, test e gestione.  La complessità ciclomatica viene calcolata da un grafico di flusso di controllo del metodo ed è espressa nel modo seguente:  
  
 complessità ciclomatica \= il numero di bordi \- il numero di nodi \+ 1  
  
 dove un nodo rappresenta un punto di ramo logico e un margine rappresenta una linea tra nodi.  
  
 Quando la complessità ciclomatica è maggiore di 25, la regola segnala una violazione.  
  
 Per ulteriori informazioni sulla metrica del codice vedere [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, effettuare il refactoring del metodo per ridurne la complessità ciclomatica.  
  
## Esclusione di avvisi  
 È consigliabile non visualizzare un avviso di questa regola se non è possibile ridurre facilmente la complessità e se il metodo può essere compreso, testato e gestito senza problemi.  In particolare, un metodo che contiene un'istruzione `switch` \(`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) di grandi dimensioni è adatto all'esclusione.  Il rischio di destabilizzare la codebase in una fase avanzata del ciclo di sviluppo o di introdurre una modifica imprevista nel comportamento in fase di esecuzione nel codice precedentemente fornito può superare i vantaggi in termini di gestibilità derivanti dal refactoring del codice.  
  
## Calcolo della complessità ciclomatica  
 La complessità ciclomatica viene calcolata aggiungendo 1 agli elementi seguenti:  
  
-   Numero di rami \(ad esempio `if`, `while`e `do`\)  
  
-   Numero di istruzioni `case` in `switch`  
  
 Negli esempi seguenti sono illustrati i metodi con varie complessità ciclomatiche.  
  
## Esempio  
 **Complessità ciclomatica di 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## Esempio  
 **Complessità ciclomatica di 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## Esempio  
 **Complessità ciclomatica di 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## Esempio  
 **Complessità ciclomatica di 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## Regole correlate  
 [CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)