---
title: "CA1051: Non dichiarare campi di istanza visibili | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
helpviewer_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1051: Non dichiarare campi di istanza visibili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo visibile esternamente dispone di un campo istanza visibile esternamente.  
  
## Descrizione della regola  
 L'utilizzo principale di un campo deve essere come dettaglio di implementazione.  I campi devono essere `private` o `internal` e devono essere esposti mediante le proprietà.  L'accesso a una proprietà è tanto semplice quanto l'accesso a un campo e il codice nelle funzioni di accesso di una proprietà può cambiare con l'espandersi delle funzionalità del tipo senza introdurre modifiche sostanziali.  Le proprietà che restituiscono solo il valore di un campo privato o interno sono ottimizzate per l'esecuzione analoga all'accesso a un campo; l'utilizzo di campi visibili esternamente rispetto alle proprietà comporta un lieve vantaggio in termini di prestazioni.  
  
 La visibilità esterna fa riferimento ai livelli di accessibilità `public`, `protected` e `protected internal` \(`Public`, `Protected` e `Protected Friend` in Visual Basic\).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rendere il campo `private` o `internal` ed esporlo mediante una proprietà visibile esternamente.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  I campi visibili esternamente non forniscono vantaggi non disponibili alle proprietà.  Inoltre, i campi pubblici non possono essere protetti da [Link Demands](../Topic/Link%20Demands.md).  Vedere [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo \(`BadPublicInstanceFields`\) che viola questa regola.  `GoodPublicInstanceFields` mostra il codice corretto.  
  
 [!code-cs[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## Regole correlate  
 [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## Vedere anche  
 [Link Demands](../Topic/Link%20Demands.md)