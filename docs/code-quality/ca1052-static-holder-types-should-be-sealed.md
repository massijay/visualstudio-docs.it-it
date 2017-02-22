---
title: "CA1052: I tipi che contengono membri statici devono essere sealed | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords: 
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1052: I tipi che contengono membri statici devono essere sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o protetto contiene solo membri statici e non è dichiarato con il modificatore [sealed](/dotnet/csharp/language-reference/keywords/sealed) \([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)\).  
  
## Descrizione della regola  
 La regola presuppone che un tipo che contiene solo membri statici non sia progettato per essere ereditato perché il tipo non fornisce alcuna funzionalità sottoponibile a override in un tipo derivato.  Un tipo non adatto ad essere ereditato deve essere contrassegnato con il modificatore `sealed` per proibirne l'utilizzo come tipo di base.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, contrassegnare il tipo come `sealed`.  Se la destinazione è [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 o versioni precedenti, un approccio migliore consiste nel contrassegnare il tipo come `static`.  In questo modo, si evita di dover dichiarare un costruttore privato per impedire la creazione della classe.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola solo se il tipo è progettato per essere ereditato.  L'assenza del modificatore `sealed` indica che il tipo può essere utilizzato come tipo di base.  
  
## Esempio di una violazione  
  
### Descrizione  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  
  
### Codice  
 [!code-cs[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## Correzione tramite modificatore statico  
  
### Descrizione  
 Nell'esempio seguente viene illustrato come correggere una violazione di questa regola contrassegnando il tipo con il modificatore `static`.  
  
### Codice  
 [!code-cs[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## Regole correlate  
 [CA1053: I tipi che contengono membri statici non devono avere costruttori](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)