---
title: "Procedura dettagliata: Profilatura dalla riga di comando tramite campionamento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, procedure dettagliate"
  - "strumenti per le prestazioni, procedure dettagliate"
  - "strumenti per le prestazioni, strumenti da riga di comando"
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Procedura dettagliata: Profilatura dalla riga di comando tramite campionamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come profilare un'applicazione mediante strumenti della riga di comando e campionamento per identificare problemi relativi alle prestazioni.  
  
 Verranno mostrati in dettaglio tutti i passaggi del processo di profilatura di un'applicazione gestita utilizzando strumenti della riga di comando, nonché l'utilizzo del campionamento per isolare e identificare i problemi di prestazioni dell'applicazione.  
  
 Nel corso di questa procedura dettagliata verranno effettuate le seguenti operazioni:  
  
-   Profilatura di un'applicazione mediante strumenti della riga di comando e campionamento.  
  
-   Esame dei risultati di profilatura mediante campionamento per individuare e risolvere i problemi di prestazioni.  
  
## Prerequisiti  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
-   Conoscenza di livello medio di [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]  
  
-   Conoscenza di livello medio dell'utilizzo degli strumenti della riga di comando  
  
-   Una copia di [Esempio PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md).  
  
-   Per utilizzare le informazioni fornite dalla profilatura, è preferibile che siano disponibili le informazioni sui simboli di debug.  
  
## Profilatura da riga di comando mediante il metodo di campionamento  
 Il campionamento è il metodo di profilatura con cui un determinato processo viene sottoposto regolarmente a polling al fine di stabilire quale sia la funzione attiva.  Nei dati risultanti è presente un conteggio della frequenza con cui la funzione si è trovata in cima allo stack di chiamate quando è stato effettuato il campionamento del processo.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli Strumenti di Profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di Visual Studio.  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  PeopleTrax è un'applicazione a 32 bit.  
  
#### Per profilare l'applicazione PeopleTrax utilizzando il metodo di campionamento  
  
1.  Installare l'applicazione di esempio PeopleTrax e compilare la versione Release dell'applicazione.  
  
2.  Aprire una finestra del prompt dei comandi e aggiungere la directory Strumenti di profilatura alla variabile di ambiente locale Path.  
  
3.  Impostare la directory di lavoro sulla directory che contiene i binari di PeopleTrax.  
  
4.  Digitare il comando seguente per impostare le variabili di ambiente appropriate:  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5.  Iniziare la profilatura eseguendo VSPerfCmd.exe, ovvero lo strumento della riga di comando che controlla il profiler.  Il comando seguente consente di avviare l'applicazione e il profiler in modalità di campionamento:  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Il processo del profiler viene avviato e collegato al processo PeopleTrax.exe.  Il processo del profiler inizia a scrivere i dati di profilatura raccolti nel file di report.  
  
6.  Fare clic su **Get People**.  
  
7.  Scegliere **Esporta Dati**.  
  
     Viene aperto Blocco note in cui è visualizzato un nuovo file contenente i dati esportati da **PeopleTrax**.  
  
8.  Chiudere Blocco note e successivamente l'applicazione **PeopleTrax**.  
  
9. Arrestare il profiler.  Digitare il comando seguente:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. Utilizzare il comando seguente per reimpostare le variabili di ambiente:  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. I dati di profilatura vengono archiviati nel file con estensione vsp. Analizzare i risultati utilizzando uno dei metodi seguenti:  
  
    -   Aprire il file vsp nell'IDE di Visual Studio.  
  
         —oppure—  
  
    -   Generare un file con valori delimitati da virgole \(con estensione csv\) utilizzando lo strumento da riga di comando VSPerfReport.exe.  Per generare rapporti da utilizzare al di fuori dell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], utilizzare il comando seguente:  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## Vedere anche  
 [Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)   
 [Visualizzazioni dei report degli strumenti per la profilatura](../profiling/performance-report-views.md)