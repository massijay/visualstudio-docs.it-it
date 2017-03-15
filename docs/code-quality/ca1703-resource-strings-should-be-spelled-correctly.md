---
title: "CA1703: Le stringhe di risorsa devono essere digitate correttamente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResourceStringsShouldBeSpelledCorrectly"
  - "CA1703"
helpviewer_keywords: 
  - "CA1703"
  - "ResourceStringsShouldBeSpelledCorrectly"
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1703: Le stringhe di risorsa devono essere digitate correttamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|Category|Microsoft.Naming|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Una stringa di risorsa contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.  
  
## Descrizione della regola  
 Questa regola analizza la stringa di risorsa per parole, scomponendo in token le parole composte, e controlla l'ortografia di ogni parola\/token.  Per informazioni sull'algoritmo di analisi, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Per impostazione predefinita, viene utilizzata la versione in lingua inglese \(en\) del correttore ortografico.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, utilizzare parole ortograficamente corrette o aggiungere le parole a un dizionario personalizzato.  Per ulteriori informazioni sulle modalità di utilizzo dei dizionari personalizzati, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  L'utilizzo di una corretta ortografia consente di ridurre il tempo necessario per l'apprendimento delle nuove librerie software.  
  
## Regole correlate  
 [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)