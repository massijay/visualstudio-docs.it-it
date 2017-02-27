---
title: "CA2224: Eseguire l&#39;override di Equals all&#39;override dell&#39;operatore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
  - "OverrideEqualsOnOverridingOperatorEquals"
helpviewer_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2224: Eseguire l&#39;override di Equals all&#39;override dell&#39;operatore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo pubblico implementa l'operatore di uguaglianza, ma non esegue l'override di <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Descrizione della regola  
 L'operatore di uguaglianza costituisce un modo pratico dal punto di vista sintattico per accedere alla funzionalità del metodo <xref:System.Object.Equals%2A>.  Se si implementa l'operatore di uguaglianza, la relativa logica deve essere identica a quella di <xref:System.Object.Equals%2A>.  
  
 Il compilatore C\# emette un avviso se il codice viola questa regola.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, è necessario rimuovere l'implementazione dell'operatore di uguaglianza oppure eseguire l'override di <xref:System.Object.Equals%2A> affinché i due metodi restituiscano gli stessi valori.  Se l'operatore di uguaglianza non introduce un comportamento incoerente, è possibile correggere la violazione fornendo un'implementazione di <xref:System.Object.Equals%2A> che chiama il metodo <xref:System.Object.Equals%2A> nella classe base.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se l'operatore di uguaglianza restituisce lo stesso valore dell'implementazione ereditata di <xref:System.Object.Equals%2A>.  Nella sezione relativa agli esempi è incluso un tipo che consente l'esclusione sicura di un avviso da questa regola.  
  
## Esempi di definizioni di uguaglianza incoerenti  
  
### Descrizione  
 Nell'esempio seguente viene mostrato un tipo con definizioni incoerenti di uguaglianza.  `BadPoint` modifica il significato di uguaglianza fornendo un'implementazione personalizzata dell'operatore di uguaglianza, ma non esegue l'override di <xref:System.Object.Equals%2A> in modo da presentare un comportamento identico.  
  
### Codice  
 [!code-cs[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## Esempio  
 Nel codice riportato di seguito viene verificato il comportamento di `BadPoint`.  
  
 [!code-cs[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **a \= \(\[0\] 1,1\) e b \= \(\[1\] 2,2\) sono uguali?**  
 **No a \=\= b?**  
 **No a1 e a sono uguali?**  
 **Sì a1 \=\= a ?**  
 **Sì b e bcopy sono uguali ?**  
 **No b \=\= bcopy ?**  
 **Sì**   
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola tecnicamente questa regola, ma non presenta un comportamento incoerente.  
  
 [!code-cs[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## Esempio  
 Nel codice riportato di seguito viene verificato il comportamento di `GoodPoint`.  
  
 [!code-cs[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **a \= \(1,1\) e b \= \(2,2\) sono uguali?**  
 **No a \=\= b?**  
 **No a1 e a sono uguali?**  
 **Sì a1 \=\= a ?**  
 **Sì b e bcopy sono uguali ?**  
 **Sì b \=\= bcopy ?**  
 **Sì**   
## Esempio di classe  
  
### Descrizione  
 Nell'esempio riportato di seguito viene illustrata una classe \(tipo di riferimento\) che viola questa regola.  
  
### Codice  
 [!code-cs[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## Esempio  
 Nell'esempio seguente viene corretta la violazione eseguendo l'override di <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## Esempio di struttura  
  
### Descrizione  
 Nell'esempio riportato di seguito viene mostrata una struttura \(tipo di valore\) che viola questa regola.  
  
### Codice  
 [!code-cs[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## Esempio  
 Nell'esempio seguente viene corretta la violazione eseguendo l'override di <xref:System.ValueType.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## Regole correlate  
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)