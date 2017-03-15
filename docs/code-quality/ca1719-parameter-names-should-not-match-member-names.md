---
title: "CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldNotMatchMemberNames"
  - "CA1719"
helpviewer_keywords: 
  - "CA1719"
  - "ParameterNamesShouldNotMatchMemberNames"
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Il nome di un membro visibile esternamente corrisponde, in un confronto senza distinzione tra maiuscole e minuscole, al nome di uno dei relativi parametri.  
  
## Descrizione della regola  
 Un nome di parametro deve comunicare il significato di un parametro e un nome di membro deve comunicare il significato di un membro.  Le progettazioni in cui questi nomi coincidono sono rare.  Assegnare a un parametro lo stesso nome del relativo membro non è intuitiva e rende più complesso l'utilizzo della libreria.  
  
## Come correggere le violazioni  
 Selezionare un nome di parametro diverso dal nome del membro.  
  
## Esclusione di avvisi  
 Per i nuovi sviluppi, non vi sono scenari noti in cui sia necessario escludere un avviso da questa regola.  Per le librerie fornite, potrebbe essere necessario escludere un avviso da questa regola.  
  
## Regole correlate  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)