---
title: "CA2200: Eseguire il rethrow per conservare i dettagli dello stack | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RethrowToPreserveStackDetails"
  - "CA2200"
helpviewer_keywords: 
  - "CA2200"
  - "RethrowToPreserveStackDetails"
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2200: Eseguire il rethrow per conservare i dettagli dello stack
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Viene rigenerata un'eccezione e quest'ultima è specificata in modo esplicito nell'istruzione `throw`.  
  
## Descrizione della regola  
 Dopo che è stata generata un'eccezione, parte delle informazioni in essa contenute è data dalla traccia dello stack.  ‎La traccia dello stack è un elenco della gerarchia delle chiamate ai metodi che inizia con il metodo che genera l'eccezione e termina con quello che la rileva.  Se un'eccezione viene rilanciata specificandola nell'istruzione `throw`, la traccia dello stack viene riavviata in corrispondenza del metodo corrente e l'elenco delle chiamate ai metodi tra il metodo originale che ha generato l'eccezione e il metodo corrente va perso.  Per mantenere con l'eccezione le informazioni della traccia dello stack originale, utilizzare l'istruzione `throw` senza specificare l'eccezione.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rigenerare l'eccezione senza specificarla in modo esplicito.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati il metodo `CatchAndRethrowExplicitly` che viola la regola e il metodo `CatchAndRethrowImplicitly` che la soddisfa.  
  
 [!CODE [FxCop.Usage.Rethrow#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow#1)]