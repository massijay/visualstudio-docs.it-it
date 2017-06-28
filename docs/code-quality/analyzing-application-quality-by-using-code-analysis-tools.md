---
title: "Analisi della qualit&#224; dell&#39;applicazione tramite gli strumenti di analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.analysisresults"
helpviewer_keywords: 
  - "qualità dell'applicazione, analisi"
  - "analisi codice"
  - "sviluppo basato su team, analisi di qualità dell'applicazione"
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# Analisi della qualit&#224; dell&#39;applicazione tramite gli strumenti di analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Contenuto della sezione  
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 L'analisi del codice di Visual Studio per il codice gestito fornisce informazioni sugli assembly gestiti, ad esempio le violazioni delle regole di programmazione e progettazione definite nelle linee guida di progettazione di Microsoft .NET Framework.  I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.  
  
 [Analisi della qualità del codice C\/C\+\+](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 Lo strumento di analisi del codice C\/C\+\+ fornisce agli sviluppatori informazioni sui possibili errori nel codice sorgente C\/C\+\+.  Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, la memoria non inizializzata, dereferenziazioni al puntatore null e perdite di memoria e risorse.  
  
 [Utilizzo di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 Selezionare e creare *set di regole* da applicare al progetto.  
  
 [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)  
 Correggere gli errori nella funzionalità di analisi codice.  
  
 [Miglioramento della qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 Quando si usa il controllo della versione di Team Foundation \(TFVC\), è possibile creare criteri di archiviazione per i progetti team che applicano procedure consigliate che consentono di ottenere codice migliore e maggiore efficienza per lo sviluppo in gruppo.  I criteri di archiviazione sono regole che vengono impostate a livello di progetto team e applicate nei computer degli sviluppatori prima che sia consentita l'archiviazione del codice.  
  
### Code Analysis for Drivers  
 Gli strumenti di analisi del codice consentono di migliorare la stabilità e l'affidabilità del driver analizzando sistematicamente il codice sorgente del driver.  
  
 [Analisi della qualità del driver tramite gli strumenti di analisi del codice](http://go.microsoft.com/fwlink/?LinkId=227618)  
 Code Analysis for Drivers è uno strumento di verifica statica in fase di compilazione che rileva gli errori di codifica di base nei programmi C e C\+\+ e include un modulo specializzato che consente di rilevare errori principalmente nel codice driver in modalità kernel.  Static Driver Verifier \(SDV\) è uno strumento di verifica statica che analizza sistematicamente il codice sorgente dei driver in modalità kernel Windows.  SDV stabilisce se il driver interagisce correttamente con il kernel del sistema operativo Windows.  
  
 [Avvisi di Code Analysis for Drivers](http://go.microsoft.com/fwlink/?LinkId=225920)  
 Descrive gli avvisi che Code Analysis for Drivers segnala quando rileva un possibile errore nel codice del driver.  
  
## Attività correlate  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 Inserire qui la descrizione.  
  
 [Eseguire unit test del codice](../test/unit-test-your-code.md)  
 Inserire qui la descrizione.