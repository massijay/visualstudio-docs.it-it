---
title: "CA1034: I tipi annidati non devono essere visibili | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
helpviewer_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1034: I tipi annidati non devono essere visibili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo visibile esternamente contiene una dichiarazione di tipo visibile esternamente.  Le enumerazioni e i tipi protetti annidati non sono interessati da questa regola.  
  
## Descrizione della regola  
 Un tipo annidato è un tipo dichiarato all'interno dell'ambito di un altro tipo.  I tipi annidati sono utili per incapsulare dettagli di implementazione privati del tipo contenitore.  I tipi annidati utilizzati per questo scopo non devono essere visibili esternamente.  
  
 Evitare di utilizzare tipi annidati visibili esternamente per raggruppamenti logici o per evitare conflitti di nomi, utilizzare invece spazi dei nomi.  
  
 I tipi annidati includono la nozione di accessibilità del membro, che non viene compresa chiaramente da alcuni programmatori.  
  
 I tipi protetti possono essere utilizzati in sottoclassi e i tipi annidati negli scenari di personalizzazione avanzata.  
  
## Come correggere le violazioni  
 Se non si desidera che il tipo annidato sia visibile esternamente, modificare l'accessibilità del tipo.  In caso contrario rimuovere il tipo annidato dall'elemento padre.  Se lo scopo dell'annidamento è quello di assegnare una categoria al tipo annidato, utilizzare in sostituzione uno spazio dei nomi per creare la gerarchia.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-cs[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]