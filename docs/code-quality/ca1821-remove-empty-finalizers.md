---
title: "CA1821: Rimuovere i finalizzatori vuoti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RemoveEmptyFinalizers"
  - "CA1821"
helpviewer_keywords: 
  - "CA1821"
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA1821: Rimuovere i finalizzatori vuoti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo implementa un finalizzatore vuoto, chiama solo il finalizzatore del tipo di base o chiama solo metodi emessi in base a determinate condizioni.  
  
## Descrizione della regola  
 Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto.  Il Garbage Collector eseguirà il finalizzatore prima di raccogliere l'oggetto.  Pertanto, per raccogliere l'oggetto saranno necessarie due raccolte.  Un finalizzatore vuoto produrrebbe sovraccarico aggiuntivo senza alcun vantaggio.  
  
## Come correggere le violazioni  
 Rimuovere il finalizzatore vuoto.  Se un finalizzatore è richiesto per il debug, includerlo per intero nelle direttive `#if DEBUG / #endif`.  
  
## Esclusione di avvisi  
 Non sopprimere un messaggio da questa regola.  La mancata eliminazione della finalizzazione comporta un calo delle prestazioni e non offre alcun vantaggio.  
  
## Esempio  
 Nell'esempio seguente è illustrato un finalizzatore vuoto che deve essere rimosso, un finalizzatore che deve essere incluso nelle direttive `#if DEBUG / #endif` e un finalizzatore che utilizza correttamente le direttive `#if DEBUG / #endif`.  
  
 [!code-cs[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]