---
title: "CA1004: I metodi generici devono fornire parametri di tipo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
helpviewer_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1004: I metodi generici devono fornire parametri di tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 La firma di parametro di un metodo generico visibile esternamente non contiene tipi che corrispondono a tutti i parametri di tipo del metodo.  
  
## Descrizione della regola  
 Per inferenza si intende la procedura con cui viene determinato l'argomento di tipo di un metodo generico in base al tipo di argomento passato al metodo, piuttosto che in base alla specifica esplicita dell'argomento di tipo.  Per consentire l'inferenza, la firma di parametro di un metodo generico deve includere un parametro dello stesso tipo del parametro di tipo relativo al metodo.  In tal caso non è necessario specificare l'argomento di tipo.  Quando si utilizza l'inferenza per tutti i parametri di tipo, la sintassi per la chiamata di metodi di istanza generici e non generici è identica.  In tal modo l'utilizzabilità dei metodi generici viene semplificata.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la progettazione in modo che la firma di parametro contenga lo stesso tipo per ciascun parametro di tipo del metodo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  La presenza di generics in una sintassi facile da comprendere e utilizzare riduce il tempo necessario all'apprendimento e aumenta la frequenza di adozione di nuove librerie.  
  
## Esempio  
 Nell'esempio riportato di seguito è illustrata la sintassi per chiamare due metodi generici.  L'argomento di tipo relativo a `InferredTypeArgument` viene dedotto, mentre l'argomento di tipo relativo a `NotInferredTypeArgument` deve essere specificato in maniera esplicita.  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-cs[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## Regole correlate  
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [Ca1003: Utilizzare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vedere anche  
 [Generics](/dotnet/csharp/programming-guide/generics/index)