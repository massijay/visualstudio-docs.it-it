---
title: "CA1000: Non dichiarare membri statici su tipi generici | Microsoft Docs"
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
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
helpviewer_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1000: Non dichiarare membri statici su tipi generici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo generico visibile contiene un membro `static` \(`Shared` in Visual Basic\).  
  
## Descrizione della regola  
 Quando viene chiamato un membro `static` di tipo generico, è necessario specificare l'argomento di tipo relativo al tipo.  Quando viene chiamato un membro di istanza generica che non supporta l'inferenza, è necessario specificare l'argomento di tipo relativo al membro.  La sintassi per la specifica dell'argomento di tipo in questi due casi è diversa e dà facilmente adito a confusione, come dimostrato nelle chiamate seguenti:  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```c#  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 In generale è consigliabile evitare entrambe le dichiarazioni precedenti, in modo che non sia necessario specificare l'argomento di tipo quando viene chiamato il membro.  Ne risulta una sintassi per la chiamata di membri in generics che non si differenzia dalla sintassi per membri non\-generics.  Per ulteriori informazioni, vedere [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il membro statico oppure cambiarlo in un membro di istanza.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  La presenza di generics in una sintassi facile da comprendere e utilizzare riduce il tempo necessario all'apprendimento e aumenta la frequenza di adozione di nuove librerie.  
  
## Regole correlate  
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [Ca1003: Utilizzare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vedere anche  
 [Generics](/dotnet/csharp/programming-guide/generics/index)