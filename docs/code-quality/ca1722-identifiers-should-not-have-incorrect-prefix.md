---
title: "CA1722: Gli identificatori non devono contenere il prefisso non corretto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotHaveIncorrectPrefix"
  - "CA1722"
helpviewer_keywords: 
  - "CA1722"
  - "IdentifiersShouldNotHaveIncorrectPrefix"
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1722: Gli identificatori non devono contenere il prefisso non corretto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Un identificatore contiene un prefisso non corretto.  
  
## Descrizione della regola  
 Per convenzione, solo determinati elementi di programmazione presentano nomi che iniziano con un prefisso specifico.  
  
 I nomi dei tipi non presentano un prefisso specifico e non devono avere il prefisso "C".  Questa regola segnala violazioni per i nomi di tipi come "CMyClass", mentre non segnala violazioni per i nomi di tipi come "Cache".  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Rimuovere il prefisso dall'identificatore.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Regole correlate  
 [CA1715: Gli identificatori devono contenere il prefisso corretto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)