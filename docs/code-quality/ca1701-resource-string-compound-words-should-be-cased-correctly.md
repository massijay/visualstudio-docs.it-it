---
title: "CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResourceStringCompoundWordsShouldBeCasedCorrectly"
  - "CA1701"
helpviewer_keywords: 
  - "CA1701"
  - "ResourceStringCompoundWordsShouldBeCasedCorrectly"
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|Category|Microsoft.Naming|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Una stringa di risorsa contiene una parola composta che non sembra essere stata digitata correttamente con distinzione tra maiuscole e minuscole.  
  
## Descrizione della regola  
 Ogni parola nella stringa di risorsa è suddivisa in token basati sulla distinzione tra maiuscole e minuscole.  Ogni combinazione di due token contigui viene controllata in base alla libreria del correttore ortografico Microsoft.  Se riconosciuta, la parola produce una violazione della regola.  Esempi di parole composte con cui si verifichi una violazione sono rispettivamente "SommaControllo" e "MultiPart", che devono invece essere digitate nelle forme "Somma controllo" e "Multipart."  Nel caso di un precedente uso comune, nella regola vengono incorporate numerose eccezioni e vengono contrassegnate molte parole singole che dovrebbero essere digitate separatamente, ad esempio "Toolbar" e "Filename".  In questo esempio vengono contrassegnate le parole "ToolBar" e "FileName".  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Modificare la parola in modo che risulti digitata correttamente con distinzione tra maiuscole e minuscole.  
  
## Esclusione di avvisi  
 La soppressione degli avvisi relativi a questa regola è considerata sicura quando le due parti della parola composta vengono riconosciute dal dizionario ortografico e si desidera utilizzare due parole.  
  
 È possibile aggiungere anche parole composte a un dizionario personalizzato per il correttore ortografico.  Le parole nel dizionario personalizzato non causano violazioni.  Per ulteriori informazioni, vedere [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## Regole correlate  
 [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## Vedere anche  
 [Convenzioni di lettere maiuscole\/minuscole](../Topic/Capitalization%20Conventions.md)   
 [Convenzioni di denominazione](../Topic/Naming%20Guidelines.md)