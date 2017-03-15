---
title: "Procedura: Creare o aggiornare criteri di archiviazione standard dell&#39;analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.policyeditor"
helpviewer_keywords: 
  - "analisi codice, migrazione dei criteri di archiviazione"
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 29
---
# Procedura: Creare o aggiornare criteri di archiviazione standard dell&#39;analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile richiedere che l'analisi codice venga eseguita su tutti i progetti di codice in un progetto team tramite i criteri di archiviazione dell'analisi del codice.  La richiesta dell'analisi del codice può migliorare la qualità del codice controllato nella codebase.  
  
> [!NOTE]
>  Questa funzionalità è disponibile solo se si utilizza Team Foundation Server.  
  
 I criteri di archiviazione del codice di analisi vengono configurati nelle impostazioni del progetto team e si applicano a ogni progetto di codice nel progetto team.  Le esecuzioni di analisi di codice vengono configurate per i progetti di codice nel file di progetto \(.xxproj\) per il progetto di codice.  Le esecuzioni di analisi di codice vengono eseguite sul computer locale.  Se si abilitano criteri di archiviazione dell'analisi di codice, al termine dell'ultima modifica è necessario compilare i file di un progetto di codice che devono essere archiviati. È inoltre necessario eseguire un'analisi di codice che contiene almeno le regole nelle impostazioni del progetto team nel computer in cui sono state apportate le modifiche.  
  
-   Per il codice gestito i criteri di archiviazione vengono impostati specificando un *set di regole* che contiene un sottoinsieme delle regole di analisi del codice.  
  
-   Per il codice C\/C\+\+i criteri di archiviazione necessitano dell'esecuzione di tutte le regole di analisi del codice.  È possibile aggiungere direttive del preprocessore per disabilitare regole specifiche per singoli progetti di codice nel progetto team.  
  
 Dopo avere specificato criteri di archiviazione per il codice gestito, i membri del team possono sincronizzare le impostazioni dell'analisi di codice per i progetti di codice con le impostazioni dei criteri del progetto team.  
  
### Per aprire l'editor dei criteri di archiviazione  
  
1.  In Team Explorer fare clic con il pulsante destro del mouse sul nome del progetto team, scegliere **Impostazioni progetto team**, quindi fare clic su **Controllo del codice sorgente**.  
  
2.  Nella finestra di dialogo **Controllo del codice sorgente** fare clic sulla scheda **Criteri di archiviazione**.  
  
3.  Effettuare una delle seguenti operazioni:  
  
    -   Fare clic su **Aggiungi** per creare nuovo criteri di archiviazione.  
  
    -   Fare doppio clic sull'elemento **Analisi codice** esistente nell'elenco **Tipo di criteri** per modificare i criteri.  
  
### Per impostare le opzioni dei criteri  
  
-   Selezionare o deselezionare le seguenti opzioni:  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |**Consenti archiviazione dei soli file della soluzione corrente.**|L'analisi del codice può essere eseguita esclusivamente sui file specificati nei file della configurazione del progetto e della soluzione.  Questi criteri garantiscono che venga analizzato tutto il codice che fa parte di una soluzione.|  
    |**Attiva analisi codice C\/C\+\+ \(\/analyze\)**|Richiede che tutti i progetti C o C\+\+ vengano compilati con l'opzione del compilatore \/analyze per eseguire l'analisi di codice prima che possano essere archiviati.|  
    |**Attiva analisi del codice gestito**|Richiede che tutti i progetti gestiti eseguano l'analisi di codice e la compilazione prima che possano essere archiviati.|  
  
### Per specificare un set di regole gestito  
  
-   Nell'elenco **Esegui set di regole** utilizzare uno dei metodi seguenti:  
  
    -   Selezionare un set di regole standard Microsoft.  
  
    -   Per selezionare un set di regole personalizzate, fare clic su **\<Seleziona set di regole dal controllo del codice sorgente..\>**, quindi digitare il percorso del controllo della versione del set di regole nel browser di controllo del codice sorgente.  La sintassi di un percorso del controllo della versione è:  
  
    -   **$\/** `TeamProjectName` **\/** `VersionControlPath`  
  
    -   Per ulteriori informazioni su come creare e implementare un set di regole personalizzate di criteri di archiviazione, vedere [Implementazione di criteri di archiviazione personalizzati per codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).  
  
## Vedere anche  
 [Creazione e utilizzo di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)