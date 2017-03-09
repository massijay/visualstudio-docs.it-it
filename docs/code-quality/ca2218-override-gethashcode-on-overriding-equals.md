---
title: "CA2218: Eseguire l&#39;override di GetHashCode all&#39;override di Equals | Microsoft Docs"
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
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
helpviewer_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2218: Eseguire l&#39;override di GetHashCode all&#39;override di Equals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo pubblico esegue l'override di <xref:System.Object.Equals%2A?displayProperty=fullName>, ma non di <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.  
  
## Descrizione della regola  
 Il metodo <xref:System.Object.GetHashCode%2A> restituisce un valore, basato sull'istanza corrente, appropriato per algoritmi di hash e strutture di dati come una tabella hash.  Due oggetti dello stesso tipo e uguali devono restituire lo stesso codice hash per assicurare il corretto funzionamento delle istanze dei tipi seguenti:  
  
-   <xref:System.Collections.HashTable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortList?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybredDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   Tipi che implementano <xref:System.Collections.Generic.IEqualityComparer?displayProperty=fullName>  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, fornire un'implementazione di <xref:System.Object.GetHashCode%2A>.  Per una coppia di oggetti dello stesso tipo, è necessario assicurarsi che l'implementazione restituisca lo stesso valore se implementazione di <xref:System.Object.Equals%2A> restituisce `true` per la coppia.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio di classe  
  
### Descrizione  
 Nell'esempio riportato di seguito viene illustrata una classe \(tipo di riferimento\) che viola questa regola.  
  
### Codice  
 [!code-cs[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### Commenti  
 Nell'esempio seguente viene corretta la violazione eseguendo l'override di <xref:System.Object.GetHashCode>.  
  
### Codice  
 [!code-cs[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
## Esempio di struttura  
  
### Descrizione  
 Nell'esempio riportato di seguito viene mostrata una struttura \(tipo di valore\) che viola questa regola.  
  
### Codice  
 [!code-cs[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
### Commenti  
 Nell'esempio seguente viene corretta la violazione eseguendo l'override di <xref:System.Object.GetHashCode>.  
  
### Codice  
 [!code-cs[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]  
  
## Regole correlate  
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## Vedere anche  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.HashTable?displayProperty=fullName>   
 [Operatori di uguaglianza](../Topic/Equality%20Operators.md)