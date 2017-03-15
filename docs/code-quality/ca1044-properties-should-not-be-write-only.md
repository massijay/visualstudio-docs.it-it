---
title: "CA1044: Le propriet&#224; non devono essere in sola scrittura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PropertiesShouldNotBeWriteOnly"
  - "CA1044"
helpviewer_keywords: 
  - "CA1044"
  - "PropertiesShouldNotBeWriteOnly"
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1044: Le propriet&#224; non devono essere in sola scrittura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 La proprietà pubblica o protetta presenta una funzione di accesso set, ma non una funzione di accesso get.  
  
## Descrizione della regola  
 Le funzioni di accesso get forniscono accesso in lettura a una proprietà, mentre le funzioni di accesso set forniscono accesso in scrittura.  Sebbene la presenza di proprietà di sola lettura sia accettabile e spesso necessaria, le linee guida di progettazione proibiscono l'utilizzo di proprietà di sola scrittura.  Questo si verifica perché consentire a un utente di impostare un valore e poi impedirgli di visualizzarlo non offre alcuna garanzia di sicurezza.  Inoltre, senza accesso in lettura, lo stato degli oggetti condivisi non può essere visualizzato, il che ne limita l'utilità.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere una funzione di accesso get alla proprietà.  In alternativa, se il comportamento di una proprietà in sola scrittura è necessario, valutare la conversione di tale proprietà in un metodo.  
  
## Esclusione di avvisi  
 È consigliabile non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito, `BadClassWithWriteOnlyProperty` è un tipo contenente una proprietà di sola scrittura.  `GoodClassWithReadWriteProperty` contiene il codice corretto.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-cs[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]