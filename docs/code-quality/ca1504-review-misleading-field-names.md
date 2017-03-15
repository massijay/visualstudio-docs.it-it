---
title: "CA1504: Controllare i nomi dei campi fuorvianti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewMisleadingFieldNames"
  - "CA1504"
helpviewer_keywords: 
  - "CA1504"
  - "ReviewMisleadingFieldNames"
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1504: Controllare i nomi dei campi fuorvianti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|Category|Microsoft.Maintainability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Il nome di un campo di istanza inizia con "s\_" o il nome di un campo `static` \(`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) inizia con "m\_".  
  
## Descrizione della regola  
 I nomi dei campi che iniziano con "s\_" sono associati a dati statici da molti utenti.  Analogamente, i nomi dei campi che iniziano con "m\_" sono associati a dati di istanza \(membro\).  Per facilitare la gestione del codice, è opportuno che i nomi seguano le convenzioni comuni.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rinominare il campo utilizzando il prefisso appropriato.  In alternativa, rendere il campo conforme al suffisso corrente aggiungendo o rimuovendo il modificatore `static`.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.