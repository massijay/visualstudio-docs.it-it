---
title: "Analisi della qualit&#224; del codice gestito tramite analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analisi codice, codice gestito"
  - "analisi codice gestito"
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Analisi della qualit&#224; del codice gestito tramite analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare gli strumenti di analisi del codice di Visual Studio per individuare potenziali problemi nel codice, ad esempio accesso ai dati non sicuro, violazioni di utilizzo e problemi di progettazione.  L'analisi codice può essere eseguita su applicazioni .NET Framework, native \(C e C\+\+\) e di database.  L'analisi del codice gestito prevede la suddivisione delle regole in *set di regole* specifici in base ai diversi problemi di codifica.  
  
## Attività comuni  
  
|Attività comuni|Contenuto di supporto|  
|---------------------|---------------------------|  
|**Fare pratica:** acquisire nozioni fondamentali di analisi codice correggendo i difetti di una semplice applicazione .NET Framework.|-   [Procedura dettagliata: Analisi del codice gestito per l'identificazione di errori del codice](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Configurare l'analisi codice per un progetto:** le regole del codice gestito sono suddivise in set di regole riguardanti aree specifiche, ad esempio sicurezza e progettazione.  È possibile utilizzare uno dei set di regole standard Microsoft o crearne di personalizzati.|-   [Panoramica dell'analisi codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Utilizzo di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Rimuovere avvisi tramite l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Eseguire l'analisi codice:** è possibile specificare che l'analisi codice venga eseguita automaticamente ogni volta che viene compilata una configurazione di progetto oppure è possibile eseguirla manualmente in un progetto.|-   [Procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Procedura: eseguire manualmente l'analisi del codice](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analizzare i risultati dell'analisi codice:** gli avvisi e gli errori dell'analisi del codice vengono elencati nella finestra di Analisi del codice.  È possibile scegliere il titolo di un avviso o di un errore per visualizzare ulteriori informazioni sull'avviso e visualizzare ed evidenziare la riga di codice che infrange la regola.  È possibile scegliere l'id dell'avviso per visualizzare informazioni dettagliate nella Libreria MSDN che include informazioni ed esempi di come risolvere il problema.|-   [Procedura: Visualizzare gli errori del codice gestito](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analisi del codice per gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Avvisi generati da CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Metodi anonimi e analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integrare l'analisi codice con il ciclo di vita dello sviluppo:** i criteri di archiviazione di [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] consentono ai team di sviluppo di assicurarsi che tutte le archiviazioni di codice soddisfino un set comune di standard di analisi codice.  La creazione di un elemento di lavoro per una violazione di una regola di analisi codice è una procedura semplice che è possibile eseguire nella finestra Elenco errori.|-   [Miglioramento della qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Procedura: sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto team](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Procedura: Creare un elemento di lavoro per un errore del codice gestito](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|