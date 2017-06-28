---
title: "Avvisi di crittografia | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 7
---
# Avvisi di crittografia
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di crittografia supportano applicazioni e librerie più sicure attraverso l'uso corretto della crittografia. Questi avvisi contribuiscono ad evitare che il programma presenti difetti nella sicurezza. Se si disabilita uno qualsiasi di questi avvisi, è opportuno indicarne chiaramente il motivo nel codice e informare il responsabile della sicurezza designato per il progetto di sviluppo.  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA5350: non usare algoritmi di crittografia vulnerabili](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Oggi si usano algoritmi di crittografia e funzioni hash deboli per diversi motivi, ma non dovrebbero essere usati per garantire la riservatezza o l'integrità dei dati che proteggono. Questa regola si attiva quando vengono rilevati algoritmi TripleDES, SHA1 o RIPEMD160 nel codice.|  
|[CA5351: non usare algoritmi di crittografia interrotti](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Gli algoritmi di crittografia violati non sono considerati sicuri e il loro uso è fortemente sconsigliato. Questa regola si attiva quando nel codice vengono rilevati l'algoritmo hash MD5 oppure gli algoritmi di crittografia DES o RC2.|