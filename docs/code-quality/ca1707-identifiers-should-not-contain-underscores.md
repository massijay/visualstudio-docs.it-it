---
title: "CA1707: Gli identificatori non devono contenere caratteri di sottolineatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotContainUnderscores"
  - "CA1707"
helpviewer_keywords: 
  - "CA1707"
  - "IdentifiersShouldNotContainUnderscores"
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1707: Gli identificatori non devono contenere caratteri di sottolineatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Category|Microsoft.Naming|  
|Breaking Change|Sostanziale: quando generato su assembly<br /><br /> Non sostanziale \- Quando generato su parametri di tipo|  
  
## Causa  
 Il nome di un identificatore contiene il carattere di sottolineatura \(\_\).  
  
## Descrizione della regola  
 Per convenzione i nomi degli identificatori non contengono il carattere di sottolineatura \(\_\).  In base alla regola vengono controllati spazi dei nomi, tipi, membri e parametri.  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Rimuovere tutti i caratteri di sottolineatura dal nome.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Regole correlate  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)