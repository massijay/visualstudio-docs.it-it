---
title: "CA1802: Utilizza valori letterali dove appropriato | Microsoft Docs"
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
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
helpviewer_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1802: Utilizza valori letterali dove appropriato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un campo viene dichiarato `static` e `readonly` \(`Shared` e `ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) e viene inizializzato con un valore calcolabile in fase di compilazione.  
  
## Descrizione della regola  
 Il valore di un campo `static` `readonly` viene calcolato in fase di esecuzione quando viene chiamato il costruttore statico per il tipo dichiarante.  Se il campo `static` `readonly` viene inizializzato al momento della dichiarazione e un costruttore statico non viene dichiarato esplicitamente, il compilatore crea un costruttore statico per inizializzare il campo.  
  
 Il valore di un campo `const` viene calcolato in fase di compilazione e memorizzato nei metadati, aumentando in tal modo le prestazioni in fase di runtime in confronto a un campo `static` `readonly`.  
  
 Dal momento che il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione in un campo `const` in modo che il calcolo del valore venga effettuato in fase di compilazione invece che in fase di esecuzione.  
  
## Come correggere le violazioni  
 Per correggere un violazione di questa regola, sostituire i modificatori `static` e `readonly` con il modificatore `const`.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola, così come la disattivazione della regola, è sicura se le prestazioni non costituiscono un problema.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati un tipo `UseReadOnly` che viola la regola e un tipo `UseConstant` che la soddisfa.  
  
 [!CODE [FxCop.Performance.UseLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals#1)]