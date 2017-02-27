---
title: "Procedura dettagliata: Profilatura dalla riga di comando tramite strumentazione | Microsoft Docs"
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
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Procedura dettagliata: Profilatura dalla riga di comando tramite strumentazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata viene descritto come profilare un'applicazione [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] autonoma per raccogliere dati relativi a numero e tempi delle chiamate tramite il metodo di strumentazione degli strumenti di profilatura.  Nel corso di questa procedura dettagliata si completeranno le seguenti attività:  
  
-   Utilizzare lo strumento da riga di comando [VSInstr](../profiling/vsinstr.md) per generare binari instrumentati.  
  
-   Utilizzare lo strumento [VSPerfCLREnv](../profiling/vsperfclrenv.md) per impostare le variabili di ambiente per raccogliere dati di profilatura .NET.  
  
-   Utilizzare lo strumento [VSPerfCmd](../profiling/vsperfcmd.md) per raccogliere dati di profilatura.  
  
-   Utilizzare lo strumento [VSPerfReport](../profiling/vsperfreport.md) per generare rapporti basati su file dei dati di profilatura.  
  
## Prerequisiti  
  
-   [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]  
  
-   Conoscenza di livello medio di C\#  
  
-   Conoscenza di livello medio dell'utilizzo degli strumenti della riga di comando  
  
-   Una copia di [Esempio PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md).  
  
-   Per utilizzare le informazioni fornite dalla profilatura, è preferibile che siano disponibili le informazioni sui simboli di debug.  Per ulteriori informazioni, vedere [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
## Profilatura da riga di comando mediante il metodo di strumentazione  
 La strumentazione è il metodo di profilatura secondo il quale le versioni speciali di binari profilati contengono funzioni controlli che raccolgono informazioni sugli intervalli all'ingresso e all'uscita da funzioni in un modulo instrumentato.  Poiché questo metodo è più invasivo rispetto al campionamento, implica un maggior sovraccarico.  I binari instrumentati sono inoltre di dimensioni maggiori rispetto a quelli di debug e di rilascio e non sono destinati alla distribuzione.  
  
> [!NOTE]
>  Non inviare binari instrumentati ai clienti.  I binari instrumentati possono contenere molti rischi.  I binari contengono informazioni che agevolano la decodifica dell'applicazione e presentano rischi per la sicurezza.  
  
#### Per profilare l'applicazione PeopleTrax utilizzando il metodo di strumentazione  
  
1.  Installare l'applicazione di esempio PeopleTrax e compilare la versione Release.  
  
2.  Aprire una finestra del prompt dei comandi e aggiungere la directory **Strumenti di profilatura** alla variabile di ambiente locale Path.  
  
3.  Impostare la directory di lavoro sulla directory che contiene i binari di PeopleTrax.  
  
4.  Creare una directory che conterrà i rapporti basati su file.  Digitare il comando seguente:  
  
    ```  
    md Reports  
    ```  
  
5.  Utilizzare lo strumento da riga di comando VSInstr per instrumentare i binari nell'applicazione.  Digitare i comandi seguenti in righe di comando distinte:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Nota** Per impostazione predefinita, VSInstr salva una copia di backup non instrumentata del file originale.  Il nome del file di backup ha l'estensione orig.  Ad esempio, la versione originale di "MyApp.exe" verrebbe salvata con il nome "MyApp.exe.orig".  
  
6.  Digitare il comando seguente per impostare le variabili di ambiente appropriate:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  Per avviare il profiler, digitare il comando seguente:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  Dopo avere avviato il profiler in modalità di traccia, eseguire la versione instrumentata del processo PeopleTrax.exe per raccogliere dati.  
  
     Verrà visualizzata la finestra dell'applicazione **PeopleTrax**.  
  
9. Fare clic su **Get People**.  
  
     La griglia di dati di PeopleTrax viene compilata.  
  
10. Scegliere **Esporta dati**.  
  
     Viene avviato Blocco note in cui viene visualizzato un nuovo file contenente un elenco di persone tratto dall'applicazione **PeopleTrax**.  
  
11. Chiudere Blocco note e successivamente l'applicazione **PeopleTrax**.  
  
12. Arrestare il profiler.  Digitare il comando seguente:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Digitare il comando seguente per reimpostare le variabili di ambiente:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Utilizzare lo strumento VSPerfReport per generare file di rapporto con valori separati da virgole \(con estensione csv\).  Tipo:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     È possibile analizzare i rapporti generati in un foglio di calcolo o utilizzare l'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per analizzare i dati di profilatura nel file Report.vsp.  Per ulteriori informazioni, vedere [Analisi dei dati degli strumenti per la profilatura](../profiling/analyzing-performance-tools-data.md).  
  
## Vedere anche  
 [Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)   
 [Visualizzazioni dei report degli strumenti per la profilatura](../profiling/performance-report-views.md)