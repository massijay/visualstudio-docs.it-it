---
title: "CA1307: Specificare StringComparison | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1307: Specificare StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un'operazione di confronto tra stringhe utilizza un overload del metodo che non imposta un parametro <xref:System.StringComparison>.  
  
## Descrizione della regola  
 Molte operazioni stringa, soprattutto i metodi <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A>, forniscono un overload che accetta un valore dell'enumerazione <xref:System.StringComparison> come parametro.  
  
 Quando esiste un overload che accetta un parametro <xref:System.StringComparison>, è necessario utilizzarlo al posto dell'overload che non lo accetta.  Impostando in modo esplicito questo parametro, il codice diventa più chiaro e facile da gestire.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, impostare i metodi di confronto tra stringhe su overload che accettano l'enumerazione <xref:System.StringComparison> come parametro.  Modificare ad esempio `String.Compare(str1, str2)` in `String.Compare(str1, str2, StringComparison.Ordinal)`  
  
## Esclusione di avvisi  
 È consigliabile non visualizzare un avviso di questa regola quando la libreria o l'applicazione è destinata a un pubblico locale limitato e non verrà pertanto localizzata.  
  
## Vedere anche  
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)   
 [CA1309: Utilizza StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)