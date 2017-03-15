---
title: "CA1061: Non nascondere i metodi di una classe base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
helpviewer_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# CA1061: Non nascondere i metodi di una classe base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo derivato consente di dichiarare un metodo con lo stesso nome e numero di parametri di uno dei relativi metodi base; uno o più parametri sono un tipo base del parametro corrispondente nel metodo base, mentre i rimanenti parametri dispongono di tipi identici ai parametri corrispondenti nel metodo base.  
  
## Descrizione della regola  
 Un metodo di un tipo base è nascosto da un metodo con lo stesso nome in un tipo derivato quando la firma di parametro del metodo derivato differisce solo dai tipi che sono derivati in modo più debole rispetto ai tipi corrispondenti nella firma di parametro del metodo base.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere o rinominare il metodo oppure modificare la firma di parametro in modo che il metodo non nasconda il metodo base.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che viola la regola.  
  
 [!code-cs[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]