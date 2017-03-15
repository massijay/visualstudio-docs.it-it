---
title: "CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole | Microsoft Docs"
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
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
helpviewer_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|Leparolecompostedevonoesseredigitatecorrettamentecondistinzionetramaiuscoleeminuscole|  
|CheckId|CA1702|  
|Category|Microsoft.Naming|  
|Breaking Change|Sostanziale \- Quando generato su assembly.<br /><br /> Non sostanziale \- Quando generato su parametri di tipo.|  
  
## Causa  
 Il nome di un identificatore contiene più parole, fra cui almeno una che sembra essere composta e digitata in modo non corretto.  
  
## Descrizione della regola  
 Il nome dell'identificatore viene distinto in parole, distinguendo fra maiuscole e minuscole.  Ogni combinazione formata da due parole contigue viene controllata dalla libreria di verifica ortografia Microsoft.  Quando viene riconosciuto, l'identificatore diviene causa di violazione della regola.  Esempi di parole composte con cui si verifichi una violazione sono rispettivamente "SommaControllo" e "MultiPart", che devono invece essere digitate nelle forme "Somma controllo" e "Multipart."  A causa del precedente uso comune, nella regola vengono incorporate numerose eccezioni e vengono contrassegnate molte parole singole, come "Toolbar" e "Filename", che dovrebbero essere digitate come due parole distinte, \(in questo caso "ToolBar" e "FileName"\).  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Modificare il modo in modo che presenti le lettere maiuscole e minuscole corrette.  
  
## Esclusione di avvisi  
 La soppressione degli avvisi relativi a questa regola è considerata sicura quando le due parti della parola composta vengono riconosciute dal dizionario ortografico e si desidera utilizzare due parole.  
  
## Regole correlate  
 [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## Vedere anche  
 [Convenzioni di denominazione](../Topic/Naming%20Guidelines.md)   
 [Convenzioni di lettere maiuscole\/minuscole](../Topic/Capitalization%20Conventions.md)