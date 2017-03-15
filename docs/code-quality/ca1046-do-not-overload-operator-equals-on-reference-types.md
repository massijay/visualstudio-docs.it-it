---
title: "CA1046: Non eseguire l&#39;overload dell&#39;operatore &quot;uguale a&quot; per i tipi di riferimento | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
  - "CA1046"
helpviewer_keywords: 
  - "CA1046"
  - "DoNotOverrideOperatorEqualsOnReferenceTypes"
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1046: Non eseguire l&#39;overload dell&#39;operatore &quot;uguale a&quot; per i tipi di riferimento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo di riferimento pubblico annidato o pubblico esegue l'overload dell'operatore di uguaglianza.  
  
## Descrizione della regola  
 Per i tipi di riferimento, l'implementazione predefinita dell'operatore di uguaglianza è quasi sempre corretta.  Per impostazione predefinita, i due riferimenti sono uguali solo se puntano allo stesso oggetto.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere l'implementazione dell'operatore di uguaglianza.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura quando il tipo di riferimento presenta il comportamento di un tipo di valore incorporato.  Se ha significato eseguire addizioni o sottrazioni sulle istanze del tipo, è probabilmente corretto implementare l'operatore di uguaglianza ed escludere la violazione.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato il comportamento predefinito quando si confrontano due riferimenti.  
  
 [!code-cs[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## Esempio  
 Nell'applicazione riportata di seguito vengono confrontati alcuni riferimenti.  
  
 [!code-cs[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **a \= new \(2,2\) and b \= new \(2,2\) are equal?**  
 **Nessun c e a sono uguali?**  
 **Sì b e a sono \=\=?**  
 **Nessun c e a sono \=\=?**  
 **Sì**   
## Regole correlate  
 [CA1013: Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## Vedere anche  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operatori di uguaglianza](../Topic/Equality%20Operators.md)