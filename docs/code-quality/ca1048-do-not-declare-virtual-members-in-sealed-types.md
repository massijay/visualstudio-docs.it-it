---
title: "CA1048: Non dichiarare membri virtuali nei tipi sealed | Microsoft Docs"
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
  - "DoNotDeclareVirtualMembersInSealedTypes"
  - "CA1048"
helpviewer_keywords: 
  - "CA1048"
  - "DoNotDeclareVirtualMembersInSealedTypes"
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1048: Non dichiarare membri virtuali nei tipi sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico è sealed e dichiara un metodo che è `virtual` \(`Overridable` in Visual Basic\) e non finale.  Questa regola non segnala violazioni per tipi delegati che devono seguire questo modello.  
  
## Descrizione della regola  
 I tipi dichiarano metodi come virtuali in modo che l'ereditarietà di tipi possa eseguire l'override dell'implementazione del metodo virtuale.  Per definizione, non è possibile ereditare da un tipo sealed, rendendo un metodo virtuale su un tipo sealed non significativo.  
  
 Con i compilatori Visual Basic .NET e C\# i tipi non possono violare questa regola.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rendere il metodo non virtuale oppure rendere il tipo ereditabile.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Se si lascia il tipo nello stato corrente è possibile causare problemi di gestione e non ottenere alcun vantaggio.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola questa regola.  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]