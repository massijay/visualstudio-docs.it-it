---
title: "Procedura: impostare le propriet&#224; di analisi del codice per progetti C/C++ | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.native"
  - "VC.Project.VCCLCompilerTool.EnablePrefast"
  - "VC.Project.VCFxCopTool.EnablePREfast"
  - "VC.Project.VCFxCopTool.IgnoreGeneratedCode"
helpviewer_keywords: 
  - "proprietà di analisi del codice C/C++"
  - "proprietà di analisi del codice"
  - "proprietà, analisi del codice C/C++"
  - "proprietà, Analisi codice"
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Procedura: impostare le propriet&#224; di analisi del codice per progetti C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile stabilire quali regole verranno utilizzate dallo strumento di analisi del codice per analizzare il codice in ciascuna configurazione del progetto.  È inoltre possibile configurare l'analisi del codice in modo da non visualizzare gli avvisi da codice generato e aggiunto al progetto da uno strumento di terze parti.  
  
## Pagina delle proprietà Analisi codice  
 La pagina delle proprietà **Analisi codice** contiene tutte le impostazioni di configurazione dell'analisi codice relative a un progetto.  Per aprire la pagina delle proprietà dell'analisi codice di un progetto in **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.  Espandere **Proprietà di configurazione** e fare clic sulla scheda **Analisi codice**.  
  
## Configurazione e piattaforma del progetto  
 Gli elenchi **Configurazione** e **Piattaforma** consentono di applicare impostazioni di analisi codice diverse a combinazioni di configurazione e piattaforma del progetto diverse.  È ad esempio possibile configurare l'analisi codice in modo da applicare un set di regole al progetto per le compilazioni di debug e un set diverso per le compilazioni di rilascio.  
  
## Attivazione dell'analisi del codice  
 È possibile decidere se abilitare l'analisi codice per il progetto selezionando **Abilita analisi codice per C\/C\+\+ in fase di compilazione**.  Mediante l'elenco **Configurazione** è possibile decidere, ad esempio, di disabilitare l'analisi del codice per le compilazioni di debug e di abilitarla per le compilazioni di rilascio.  
  
 Se il progetto contiene codice gestito, è possibile decidere se abilitare o disabilitare l'analisi codice selezionando **Abilita analisi codice in fase di compilazione**.  
  
 L'analisi codice è mirata al miglioramento della qualità del codice e a evitare errori comuni.  È pertanto consigliabile valutare attentamente l'eventualità di disabilitare l'analisi codice.  In genere è preferibile disabilitare i set di regole o regole singole che non si desidera applicare al progetto.  
  
## Codice generato  
 Gli sviluppatori spesso utilizzano strumenti che consentono uno sviluppo più rapido delle applicazioni.  Questi strumenti possono generare codice da aggiungere al progetto.  Può essere necessario visualizzare le violazioni delle regole individuate dall'analisi codice nel codice generato.  Tuttavia, se non si desidera gestire tale codice, è preferibile non visualizzare le violazioni.  
  
 La casella di controllo **Non visualizzare i risultati del codice generato** nella pagina delle proprietà **Generale** consente di scegliere se visualizzare o meno gli avvisi dell'analisi codice da codice gestito generato da uno strumento di terze parti.  
  
## Set di regole  
 Se il progetto contiene codice gestito, è possibile selezionare le regole da applicare nell'analisi codice selezionando un set di regole dall'elenco **Esegui questo set di regole**.  
  
## Vedere anche  
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Avvisi dell'analisi codice per il linguaggio C\/C\+\+](../code-quality/code-analysis-for-c-cpp-warnings.md)