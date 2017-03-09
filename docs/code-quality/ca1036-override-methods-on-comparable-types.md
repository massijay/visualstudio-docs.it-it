---
title: "CA1036: Eseguire l&#39;override di metodi su tipi confrontabili | Microsoft Docs"
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
  - "CA1036"
  - "OverrideMethodsOnComparableTypes"
helpviewer_keywords: 
  - "OverrideMethodsOnComparableTypes"
  - "CA1036"
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1036: Eseguire l&#39;override di metodi su tipi confrontabili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|Categoria|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo pubblico o protetto implementa l'interfaccia <xref:System.IComparable?displayProperty=fullName> e non esegue l'override di <xref:System.Object.Equals%2A?displayProperty=fullName> né dell'operatore di uguaglianza, disuguaglianza, minore di o maggiore di specifico del linguaggio.  La regola non segnala una violazione se il tipo eredita solo un'implementazione dell'interfaccia.  
  
## Descrizione della regola  
 I tipi che definiscono un criterio di ordinamento personalizzato implementano l'interfaccia <xref:System.IComparable>.  Il metodo <xref:System.IComparable.CompareTo%2A> restituisce un Integer che indica il criterio di ordinamento corretto per due istanze del tipo.  Questa regola identifica i tipi che impostano un criterio di ordinamento, implicando che il significato ordinario di uguaglianza, disuguaglianza, minore di e maggiore di non è applicabile.  Quando si fornisce un'implementazione di <xref:System.IComparable>, è necessario eseguire anche l'override di <xref:System.Object.Equals%2A> in modo che restituisca valori coerenti con <xref:System.IComparable.CompareTo%2A>.  Se si esegue l'override di <xref:System.Object.Equals%2A> e il linguaggio in uso supporta gli overload degli operatori, è inoltre necessario fornire operatori coerenti con <xref:System.Object.Equals%2A>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, eseguire l'override di <xref:System.Object.Equals%2A>.  Se il linguaggio di programmazione in uso supporta l'overload degli operatori, fornire gli operatori riportati di seguito:  
  
-   op\_Equality  
  
-   op\_Inequality  
  
-   op\_LessThan  
  
-   op\_GreaterThan  
  
 In C\#, i token utilizzati per rappresentare questi operatori sono i seguenti: \=\=, \!\=, \<, and \>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se la violazione è causata da operatori mancanti e il linguaggio di programmazione non supporta l'overload degli operatori, come nel caso di Visual Basic .NET.  L'esclusione di un avviso da questa regola quando genera in operatori diversi da op\_Equality è sicura anche se viene determinato che l'implementazione degli operatori non ha senso nel contesto di applicazione.  Tuttavia, se si esegue l'override di Object.Equals, è sempre necessario eseguire l'override di op\_Equality e dell'operatore \=\=.  
  
## Esempio  
 Nell'esempio riportato di seguito è contenuto un tipo che implementa correttamente <xref:System.IComparable>.  I commenti al codice identificano i metodi che soddisfano varie regole correlate a <xref:System.Object.Equals%2A> e all'interfaccia <xref:System.IComparable>.  
  
 [!code-cs[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## Esempio  
 Nell'applicazione riportata di seguito viene verificato il comportamento dell'implementazione <xref:System.IComparable> illustrata in precedenza.  
  
 [!code-cs[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## Vedere anche  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operatori di uguaglianza](../Topic/Equality%20Operators.md)