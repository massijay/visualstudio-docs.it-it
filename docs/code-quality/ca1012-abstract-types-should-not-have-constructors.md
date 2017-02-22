---
title: "CA1012: I tipi astratti non devono avere costruttori | Microsoft Docs"
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
  - "AbstractTypesShouldNotHaveConstructors"
  - "CA1012"
helpviewer_keywords: 
  - "CA1012"
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1012: I tipi astratti non devono avere costruttori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo pubblico è astratto e presenta un costruttore pubblico.  
  
## Descrizione della regola  
 I costruttori sui tipi astratti possono essere chiamati solo da tipi derivati.  Poiché i costruttori pubblici creano istanze di un tipo e non è possibile creare istanze di un tipo astratto, per una buona progettazione non bisognerebbe creare un tipo astratto con costruttore pubblico.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rendere protetto il costruttore oppure non dichiarare il tipo come astratto.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Il tipo astratto dispone di un costruttore pubblico.  
  
## Esempio  
 Nell'esempio riportato di seguito è contenuto un tipo astratto che viola questa regola.  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-cs[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## Esempio  
 Nell'esempio seguente , la violazione precedente viene corretta tramite l'impostazione dell'accessibilità del costruttore da `public` su `protected`.  
  
 [!code-cs[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]