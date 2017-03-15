---
title: "CA1005: Evitare un uso eccessivo di parametri nei tipi generici | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1005: Evitare un uso eccessivo di parametri nei tipi generici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo generico visibile esternamente presenta più di due parametri di tipo.  
  
## Descrizione della regola  
 Quanto più è alto il numero di parametri di tipo contenuti, maggiore è la difficoltà di sapere e ricordare cosa rappresenta ciascun parametro.  Di solito, è ovvio con un parametro di tipo, come in `List<T>`, e in alcuni casi anche con due, come in `Dictionary<TKey, TValue>`.  Se i parametri di tipo sono più di due, la difficoltà si rivela eccessiva per la maggior parte degli utenti \(ad esempio, `TooManyTypeParameters<T, K, V>` in C\# o `TooManyTypeParameters(Of T, K, V)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la progettazione in modo che non vengano utilizzati più di due parametri di tipo.  
  
## Esclusione di avvisi  
 Non escludere avvisi per questa regola a meno che la progettazione non richieda assolutamente più di due parametri di tipo.  La presenza di generics in una sintassi facile da comprendere e utilizzare riduce il tempo necessario all'apprendimento e aumenta la frequenza di adozione di nuove librerie.  
  
## Regole correlate  
 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [Ca1003: Utilizzare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vedere anche  
 [Generics](/dotnet/csharp/programming-guide/generics/index)