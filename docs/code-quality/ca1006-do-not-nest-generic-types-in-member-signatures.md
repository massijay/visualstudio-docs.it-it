---
title: "CA1006: Non annidare tipi generici nelle firme dei membri | Microsoft Docs"
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
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords: 
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1006: Non annidare tipi generici nelle firme dei membri
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un membro visibile esternamente presenta una firma che contiene un argomento di tipo annidato.  
  
## Descrizione della regola  
 Un argomento di tipo annidato è un argomento di tipo che è anche un tipo generico.  Per chiamare un membro la cui firma contiene un argomento di tipo annidato, l'utente deve creare un'istanza su un tipo generico e passare il tipo al costruttore di un secondo tipo generico.  La sintassi e la procedura necessarie sono complesse ed è opportuno evitarle.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la progettazione per rimuovere l'argomento di tipo annidato.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  La presenza di generics in una sintassi facile da comprendere e utilizzare riduce il tempo necessario all'apprendimento e aumenta la frequenza di adozione di nuove librerie.  
  
## Esempio  
 Nell'esempio riportato di seguito sono illustrati un metodo che viola la regola e la sintassi necessaria per chiamare tale metodo.  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-cs[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## Regole correlate  
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [Ca1003: Utilizzare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vedere anche  
 [Generics](/dotnet/csharp/programming-guide/generics/index)