---
title: "CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi | Microsoft Docs"
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
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Un nome del tipo corrisponde a uno dei nomi degli spazi dei nomi di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in un confronto senza distinzione tra maiuscole e minuscole.  
  
## Descrizione della regola  
 I nomi dei tipi non devono corrispondere ai nomi degli spazi dei nomi definiti nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  La violazione di questa regola può ridurre l'utilizzabilità della libreria.  
  
## Come correggere le violazioni  
 Selezionare un nome di tipo che non corrisponda al nome di uno spazio dei nomi della libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Esclusione di avvisi  
 Per i nuovi sviluppi, non vi sono scenari noti in cui sia necessario escludere un avviso da questa regola.  Prima di eliminare l'avviso, valutare attentamente come gli utenti della libreria potrebbero essere disorientati dal nome corrispondente.  Per le librerie fornite, potrebbe essere necessario escludere un avviso da questa regola.