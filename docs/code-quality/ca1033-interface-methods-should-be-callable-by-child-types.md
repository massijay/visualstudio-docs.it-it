---
title: "CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio | Microsoft Docs"
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
  - "InterfaceMethodsShouldBeCallableByChildTypes"
  - "CA1033"
helpviewer_keywords: 
  - "CA1033"
  - "InterfaceMethodsShouldBeCallableByChildTypes"
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|  
|CheckId|CA1033|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo visibile esternamente non sealed fornisce un'implementazione di metodo esplicita di un'interfaccia pubblica e non fornisce un metodo visibile esternamente alternativo con lo stesso nome.  
  
## Descrizione della regola  
 Si consideri un tipo di base che implementi in modo esplicito un metodo di interfaccia pubblica.  Un tipo che deriva dal tipo di base può accedere al metodo di interfaccia ereditata solo tramite un riferimento all'istanza corrente \(`this` in C\#\) di cui è stato eseguito il cast nell'interfaccia.  Se il tipo derivato reimplementa in modo esplicito il metodo di interfaccia ereditata, l'implementazione di base non è più accessibile.  La chiamata tramite il riferimento a un'istanza corrente richiamerà l'implementazione derivata causando la ricorsione e un eventuale overflow dello stack.  
  
 Questa regola non segnala una violazione per un'implementazione esplicita di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> quando viene fornito un metodo visibile esternamente `Close()` o `System.IDisposable.Dispose(Boolean)`.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare un nuovo metodo che esponga la stessa funzionalità e sia visibile ai tipi derivati oppure passare a un'implementazione non esplicita.  Se è accettabile una modifica sostanziale, come alternativa è possibile rendere il tipo sealed.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se viene fornito un metodo visibile esternamente con la stessa funzionalità, ma con nome diverso rispetto al metodo implementato in modo esplicito.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati un tipo `ViolatingBase` che viola la regola e un tipo `FixedBase` che mostra una correzione per la violazione.  
  
 [!code-cs[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]  
  
## Vedere anche  
 [Interfacce](/dotnet/csharp/programming-guide/interfaces/index)