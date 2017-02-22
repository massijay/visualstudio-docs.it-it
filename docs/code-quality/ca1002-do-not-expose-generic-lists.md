---
title: "CA1002: Non esporre elenchi generici | Microsoft Docs"
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
  - "DoNotExposeGenericLists"
  - "CA1002"
helpviewer_keywords: 
  - "CA1002"
  - "DoNotExposeGenericLists"
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1002: Non esporre elenchi generici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotExposeGenericLists|  
|CheckId|CA1002|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo contiene un membro visibile esternamente che corrisponde a un tipo <xref:System.Collections.Generic.List%601?displayProperty=fullName>, restituisce un tipo <xref:System.Collections.Generic.List%601?displayProperty=fullName> oppure la cui firma include un parametro <xref:System.Collections.Generic.List%601?displayProperty=fullName>.  
  
## Descrizione della regola  
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> è una raccolta generica progettata per le prestazioni e non per l'ereditarietà.  <xref:System.Collections.Generic.List%601?displayProperty=fullName> non contiene membri virtuali che rendono più semplice la modifica del comportamento di una classe ereditata.  Le raccolte seguenti sono state progettate per l'ereditarietà e dovrebbero essere esposte in luogo di <xref:System.Collections.Generic.List%601?displayProperty=fullName>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il tipo <xref:System.Collections.Generic.List%601?displayProperty=fullName> in una delle raccolte generiche progettate per l'ereditarietà.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola a meno che non si preveda di considerare l'assembly che ha generato l'avviso una libreria riutilizzabile.  Ad esempio, potrebbe essere sicuro escludere l'avviso in un un'applicazione di regolazione delle prestazioni in cui si sia ottenuto un miglioramento delle prestazioni mediante l'utilizzo degli elenchi generici.  
  
## Regole correlate  
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [Ca1003: Utilizzare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vedere anche  
 [Generics](/dotnet/csharp/programming-guide/generics/index)