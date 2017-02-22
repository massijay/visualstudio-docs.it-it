---
title: "CA2226: Gli operatori devono avere overload simmetrici | Microsoft Docs"
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
  - "OperatorsShouldHaveSymmetricalOverloads"
  - "CA2226"
helpviewer_keywords: 
  - "CA2226"
  - "OperatorsShouldHaveSymmetricalOverloads"
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2226: Gli operatori devono avere overload simmetrici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperatorsShouldHaveSymmetricalOverloads|  
|CheckId|CA2226|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo implementa l'operatore di uguaglianza o di disuguaglianza e non implementa l'operatore opposto.  
  
## Descrizione della regola  
 Non vi sono casi in cui l'operatore di uguaglianza o disuguaglianza sia applicabile a istanze di un tipo e l'operatore opposto non sia definito.  I tipi implementano in genere l'operatore di disuguaglianza restituendo il valore negato dell'operatore di uguaglianza.  
  
 Il compilatore C\# genera un errore per le violazioni di questa regola.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare entrambi gli operatori di uguaglianza e disuguaglianza oppure rimuovere l'operatore presente.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Il tipo non funzionerebbe in modo coerente con [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Regole correlate  
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)