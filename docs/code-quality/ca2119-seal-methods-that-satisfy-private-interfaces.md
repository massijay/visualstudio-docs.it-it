---
title: "CA2119: Impostare come sealed i metodi che soddisfano interfacce private | Microsoft Docs"
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
  - "SealMethodsThatSatisfyPrivateInterfaces"
  - "CA2119"
helpviewer_keywords: 
  - "CA2119"
  - "SealMethodsThatSatisfyPrivateInterfaces"
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2119: Impostare come sealed i metodi che soddisfano interfacce private
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico ereditabile fornisce un'implementazione di metodo sottoponibile a override di un'interfaccia `internal` \(`Friend` in Visual Basic\).  
  
## Descrizione della regola  
 I metodi dell'interfaccia dispongono di accessibilità pubblica, che non è possibile modificare mediante il tipo di implementazione.  Un'interfaccia interna crea un contratto di cui non è prevista l'implementazione all'esterno dell'assembly che definisce l'interfaccia.  Un tipo pubblico che implementa un metodo di un'interfaccia interna mediante il modificatore `virtual` \(`Overridable` in Visual Basic\) consente di eseguire l'override del metodo con un tipo derivato che si trova all'esterno dell'assembly.  Se un secondo tipo nell'assembly di definizione chiama il metodo e prevede un contratto solo interno, è possibile che il comportamento risulti compromesso quando il metodo sottoposto a override nell'assembly esterno viene invece eseguito.  In tal modo viene creata una vulnerabilità della sicurezza.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, impedire che venga eseguito l'override del metodo esternamente all'assembly utilizzando una delle soluzioni illustrate di seguito:  
  
-   Rendere `sealed` \(`NotInheritable` in Visual Basic\) il tipo di dichiarazione.  
  
-   Modificare l'accessibilità del tipo di dichiarazione in `internal` \(`Friend` in Visual Basic\).  
  
-   Rimuovere tutti i costruttori pubblici dal tipo di dichiarazione.  
  
-   Implementare il metodo senza utilizzare il modificatore `virtual`.  
  
-   Implementare il metodo in maniera esplicita.  
  
## Esclusione di avvisi  
 È sicuro escludere un avviso da questa regola se dopo un attento esame risulterà che non potranno derivare problemi di sicurezza se verrà eseguito l'override del metodo esterno all'assembly.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo, `BaseImplementation`, che viola questa regola.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-cs[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## Esempio  
 Nell'esempio seguente viene utilizzata l'implementazione del metodo virtuale dell'esempio precedente:  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-cs[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## Vedere anche  
 [Interfacce](/dotnet/csharp/programming-guide/interfaces/index)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)