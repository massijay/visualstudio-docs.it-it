---
title: "CA1010: Le raccolte devono implementare un&#39;interfaccia generica | Microsoft Docs"
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
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
helpviewer_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1010: Le raccolte devono implementare un&#39;interfaccia generica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo visibile esternamente implementa l'interfaccia <xref:System.Collections.IEnumerable?displayProperty=fullName> ma non l'interfaccia <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> e l'assembly che lo contiene è destinato a [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  La regola ignora i tipi che implementano <xref:System.Collections.IDictionary?displayProperty=fullName>.  
  
## Descrizione della regola  
 Per ampliare la possibilità di utilizzo di una raccolta, implementare una delle interfacce di raccolte generiche.  La raccolta potrà poi essere utilizzata per inserire dati in tipi di raccolte generiche come la seguente:  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare una delle seguenti interfacce di raccolte generiche:  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura; la raccolta, tuttavia, avrà un utilizzo più limitato.  
  
## Esempio di violazione  
  
### Descrizione  
 Nell'esempio seguente viene mostrata una classe \(tipo di riferimento\) che deriva dalla classe non generica `CollectionBase` che viola questa regola.  
  
### Codice  
 [!code-cs[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### Commenti  
 Per correggere questo tipo di violazione è necessario implementare le interfacce generiche o impostare la classe di base su un tipo che implementa già interfacce generiche e non generiche, ad esempio la classe `Collection<T>`.  
  
## Correzione tramite modifica della classe base  
  
### Descrizione  
 Nell'esempio riportato di seguito viene corretta la violazione impostando la classe di base della raccolta impostata sulla classe non generica `CollectionBase` sulla classe generica `Collection<T>` \(`Collection(Of T)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Codice  
 [!code-cs[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### Commenti  
 La modifica della classe base di una classe già rilasciata è considerata una modifica sostanziale che può causare interruzioni per i consumer esistenti.  
  
## Correzione tramite implementazione di interfaccia  
  
### Descrizione  
 Nell'esempio riportato di seguito viene corretta la violazione implementando le seguenti interfacce generiche: `IEnumerable<T>`, `ICollection<T>` e `IList<T>` \(`IEnumerable(Of T)`, `ICollection(Of T)` e `IList(Of T)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Codice  
 [!code-cs[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## Regole correlate  
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [Ca1003: Utilizzare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vedere anche  
 [Generics](/dotnet/csharp/programming-guide/generics/index)