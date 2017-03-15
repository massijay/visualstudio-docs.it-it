---
title: "CA1505: evitare codice non manutenibile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnmaintainableCode"
  - "CA1505"
helpviewer_keywords: 
  - "AvoidUnmaintainableCode"
  - "CA1505"
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1505: evitare codice non manutenibile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|Category|Microsoft.Maintainability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo o metodo presenta un valore di indice di gestibilità basso.  
  
## Descrizione della regola  
 L'indice di gestibilità viene calcolato utilizzando la metrica seguente: righe di codice, volume del programma e complessità ciclomatica.  Il volume del programma è una misura della difficoltà di comprensione di un tipo o di un metodo basata sul numero di operatori e operandi nel codice.  La complessità ciclomatica è una misura della complessità strutturale del tipo o del metodo.  Per ulteriori informazioni sulla metrica del codice vedere [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
 Un indice di gestibilità basso indica che un tipo o metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione.  
  
## Come correggere le violazioni  
 Per correggere questa violazione, riprogettare il tipo o metodo e tentare di suddividerlo in tipi o metodi più piccoli e specifici.  
  
## Esclusione di avvisi  
 Escludere questo avviso quando un tipo o metodo è considerato accettabile nonostante le grandi dimensioni o quando il tipo o metodo non può essere suddiviso.  
  
## Vedere anche  
 [Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)   
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)