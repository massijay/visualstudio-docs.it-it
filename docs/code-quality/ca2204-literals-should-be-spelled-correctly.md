---
title: "CA2204: I valori letterali devono essere digitati in modo corretto | Microsoft Docs"
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
  - "Literals should be spelled correctly"
  - "CA2204"
  - "LiteralsShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA2204"
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2204: I valori letterali devono essere digitati in modo corretto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo passa una stringa letterale che viene utilizzata in un parametro o proprietà che richiede una stringa localizzata e la stringa letterale contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.  
  
## Descrizione della regola  
 Questa regola controlla una stringa letterale passata come un valore a un parametro o una proprietà quando uno o più dei casi seguenti è vero:  
  
-   L'attributo <xref:System.ComponentModel.LocalizableAttribute> del parametro o proprietà è impostato su true.  
  
-   Il parametro o il nome della proprietà contiene "Testo", "Messaggio" o "Barra del titolo."  
  
-   Il nome del parametro di stringa passato a un metodo Console.Write o Console.WriteLine è "valore" o "formato."  
  
 Questa regola analizza le parole che compongono la stringa letterale, suddividendo in token le parole composte, e controlla l'ortografia di ciascuna parola\/token.  Per informazioni sull'algoritmo di analisi, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Per impostazione predefinita, viene utilizzata la versione in lingua inglese \(en\) del correttore ortografico.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, correggere l'ortografia della parola o aggiungere la parola a un dizionario personalizzato.  Per ulteriori informazioni sulle modalità di utilizzo dei dizionari personalizzati, vedere [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  L'utilizzo di una corretta ortografia consente di ridurre la curva di apprendimento richiesta per le nuove librerie software.  
  
## Regole correlate  
 [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)