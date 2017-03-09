---
title: "Panoramica dell&#39;analisi codice gestito | Microsoft Docs"
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
  - "vs.projectpropertypages.codeanalysis"
helpviewer_keywords: 
  - "analisi codice, codice gestito"
  - "codice gestito, analisi codice"
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 35
caps.handback.revision: 35
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Panoramica dell&#39;analisi codice gestito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'analisi del codice gestito analizza gli assembly gestiti e fornisce informazioni sugli assembly, ad esempio le violazioni delle regole di programmazione e progettazione definite nelle linee guida di progettazione di Microsoft .NET Framework.  
  
 Lo strumento di analisi rappresenta i controlli eseguiti durante un'analisi come messaggi di avviso.  I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.  
  
## Integrazione nell'IDE \(Integrated Development Environment\)  
 Gli sviluppatori possono eseguire l'analisi del codice del progetto automaticamente o manualmente.  
  
 Per eseguire l'analisi codice ogni volta che si compila un progetto, selezionare **Attiva analisi codice in fase di compilazione \(definisce la costante CODE\_ANALYSIS\)**.  Per ulteriori informazioni, vedere [Procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Per eseguire manualmente l'analisi del codice su un progetto, dal menu **Analizza** scegliere **Esegui analisi del codice su** *ProjectName*.  Per ulteriori informazioni, vedere [Procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## Set di regole  
 Le regole di analisi per il codice gestito vengono raggruppate in *set di regole*.  È possibile utilizzare uno dei set di regole standard Microsoft oppure creare un set di regole personalizzato per soddisfare una specifica esigenza.  Per ulteriori informazioni, vedere [Utilizzo di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## Eliminazione nell'origine  
 È in genere utile indicare se un avviso non è applicabile.  In questo modo lo sviluppatore e altri individui che potrebbero rivedere il codice in un secondo momento verranno informati del fatto che un avviso è stato sottoposto ad analisi, quindi è stato eliminato o ignorato.  
  
 L'eliminazione nell'origine degli avvisi viene implementata attraverso attributi personalizzati.  Per non visualizzare un avviso, aggiungere l'attributo `SuppressMessage` al codice sorgente, come illustrato nell'esempio seguente:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Per ulteriori informazioni, vedere [Rimuovere avvisi tramite l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## Eseguire l'analisi del codice come parte dei criteri di archiviazione  
 Le organizzazioni richiedono talvolta che tutte le archiviazioni soddisfino determinati criteri,  tra cui, in particolare:  
  
-   Assenza di errori di compilazione nel codice da archiviare.  
  
-   Esecuzione dell'analisi del codice durante la compilazione più recente.  
  
 A tale scopo, è utile quindi definire dei criteri specifici per l'archiviazione.  Per ulteriori informazioni, vedere [Miglioramento della qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## Integrazione di Team Build  
 È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi come parte del processo di compilazione.  Per ulteriori informazioni, vedere [Compilare l'applicazione](../Topic/Build%20the%20application.md).  
  
## Vedere anche  
 [Utilizzo di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)