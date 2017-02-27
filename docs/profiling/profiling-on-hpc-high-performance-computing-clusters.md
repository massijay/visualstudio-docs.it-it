---
title: "Profilatura su cluster HPC (High Performance Computing) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.hpc.wizard.exeoptions"
  - "vs.performance.hpc.wizard.summary"
  - "vs.performance.hpc.wizard.startoptions"
  - "vs.performance.hpc.wizard.intro"
  - "vs.performance.hpc.property.basic"
  - "vs.performance.hpc.wizard.application"
  - "vs.performance.hpc.wizard.clusteroptions"
  - "vs.performance.hpc.property.advanced"
helpviewer_keywords: 
  - "strumenti per la profilatura, HPC"
  - "HPC (profilatura)"
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Profilatura su cluster HPC (High Performance Computing)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile eseguire profili su nodi di calcolo di cluster Microsoft Windows HPC tramite il metodo di campionamento degli strumenti di profilatura di [!INCLUDE[vsPreExt](../profiling/includes/vspreext_md.md)] o [!INCLUDE[vsUltExt](../profiling/includes/vsultext_md.md)].  Per ulteriori informazioni su HPC, vedere [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393) nel sito Web Microsoft:  
  
## Prerequisiti  
 Per eseguire profili su un nodo di calcolo HPC, è necessario effettuare le operazioni seguenti:  
  
-   Installare Microsoft HPC Pack 2008 nello stesso computer di [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  Il computer non deve far parte del cluster HPC.  È possibile installare HPC Pack nell'[Area download Microsoft](http://go.microsoft.com/fwlink/?LinkID=177414).  
  
-   Installare [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] e la versione autonoma degli strumenti di profilatura sul nodo di calcolo HPC.  I programmi di installazione per [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e il profiler autonomo sono disponibili nel supporto di installazione [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)].  **Nota** è necessario riavviare il computer dopo avere installato [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e prima di installare gli Strumenti di profilatura.  
  
 Per installare [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] e gli strumenti di profilatura autonomi su un nodo di calcolo HPC attivo e abilitare la profilatura sul computer del cluster, attenersi alla seguente procedura:  
  
1.  Aprire la finestra del prompt dei comandi installata con HPC Pack.  
  
2.  Digitare i comandi seguenti in prompt dei comandi distinti:  
  
    1.  `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|Nome del nodo head del cluster.|  
|*%FxPath%*|Percorso del programma di installazione di [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)].  Sul supporto di installazione di [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] il percorso è: WCU\\dotNetFramework\\dotNetFx40\_Full\_x86\_x64.exe|  
|*%ProfilerPath%*|Percorso della versione autonoma del programma di installazione degli strumenti di profilatura.  Sul supporto di installazione di [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] il percorso è: Standalone Profiler\\x64\\vs\_profiler.exe|  
  
## Profilatura su un nodo di calcolo HPC  
 È possibile configurare una sessione di profilatura tramite la Creazione guidata sessione di prestazioni HPC per specificare informazioni sul cluster HPC e sulla destinazione.  Eventuali opzioni aggiuntive possono essere impostate nelle pagine delle proprietà della sessione di prestazioni.  Tramite gli strumenti di profilatura vengono distribuiti automaticamente i binari di destinazione necessari e viene avviato il profiler e l'applicazione HPC.  
  
#### Per eseguire il profilo su un nodo di calcolo HPC  
  
1.  Scegliere **Avvia Creazione guidata sessione di prestazioni** dal menu **Analizza**.  Se il comando non è disponibile, verificare che siano presenti i prerequisiti elencati sopra.  
  
2.  Nella prima pagina della creazione guidata scegliere **Avanti**.  
  
3.  Nella seconda pagina della creazione guidata selezionare l'applicazione che si desidera profilare.  
  
    -   Per profilare un progetto attualmente aperto in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], selezionare l'opzione **Uno o più progetti disponibili**, quindi selezionare il nome del progetto dall'elenco.  
  
    -   Per profilare un binario non incluso in un progetto aperto, selezionare l'opzione **Eseguibile \(file EXE\)**.  
  
4.  Scegliere **Avanti**.  
  
5.  Nella terza pagina della procedura guidata:  
  
    -   Se si profila un eseguibile non incluso in un progetto aperto, specificare il percorso del file binario in **Specificare il percorso completo dell'eseguibile**.  
  
    -   Se si profila un eseguibile non incluso in un progetto aperto, è possibile specificare qualsiasi argomento della riga di comando per passare al processo in **Argomenti della riga di comando**.  
  
    -   In **Cartella di lavoro remota** specificare il percorso della cartella utilizzata dalle istanze del processo sui singoli nodi di calcolo.  
  
    -   In **Percorso di distribuzione** specificare il percorso della directory utilizzata dal server HPC per la gestione temporanea di immagini per la distribuzione.  
  
6.  Scegliere **Avanti**.  
  
7.  Nella quarta pagina della creazione guidata effettuare le operazioni seguenti:  
  
    -   Nell'elenco **Nodo head** fare clic sul computer utilizzato come nodo head HPC nell'esecuzione della profilatura.  Il nodo head può essere "localhost", consentendo in tal modo di eseguire il profilo sul computer locale senza l'esigenza di un cluster.  
  
    -   Nell'elenco **Numero di processi** fare clic sul numero di istanze dell'applicazione da eseguire.  
  
    -   Nell'elenco **Opzioni profilo** selezionare la destinazione di profilatura.  
  
         Per profilare un processo specifico nel cluster, selezionare l'opzione **Esegui profilo su priorità**, quindi selezionare la priorità del processo dall'elenco a discesa.  
  
         Per profilare il processo o i processi eseguiti su un nodo specifico nel cluster HPC, selezionare l'opzione **Esegui profilo su nodo**, quindi selezionare il nodo dall'elenco a discesa.  
  
8.  Scegliere **Avanti**.  
  
9. Nella quinta pagina della procedura guidata, è possibile scegliere di avviare immediatamente il profiler e il processo di profilatura o di avviare la profilatura in un secondo momento tramite Esplora prestazioni.  
  
    -   Selezionare **Avvia profilo al termine della procedura guidata** per avviare la profilatura immediatamente oppure deselezionare la casella di controllo per avviare la profilatura manualmente.  
  
10. Scegliere **Fine**.  
  
## Impostazione delle proprietà del profilo HPC tramite le pagine delle proprietà della sessione di prestazioni  
 È possibile modificare le proprietà della sessione di prestazioni impostate nella creazione guidata profilo HPC nella pagina delle proprietà di avvio HPC della pagina delle proprietà della sessione di prestazioni.  Le opzioni aggiuntive vengono impostate nella pagina delle proprietà avanzate HPC.  
  
#### Per aprire le pagine delle proprietà della sessione di prestazioni  
  
1.  Se necessario, aprire il file della sessione di prestazioni \(con estensione psess\) in Esplora prestazioni.  Scegliere **Apri** dal menu **File**, quindi individuare il file.  
  
2.  In Esplora prestazioni fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni, quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo Pagine delle proprietà utilizzare uno dei metodi seguenti:  
  
    -   Fare clic su **Generale**, quindi selezionare **Raccolta su cluster HPC** per attivare il profilo HPC o deselezionare la casella di controllo per disabilitarlo.  
  
    -   Fare clic su **Proprietà avvio HPC** per modificare le proprietà di avvio dell'applicazione HPC.  
  
    -   Fare clic su **Proprietà avanzate HPC** per impostare opzioni aggiuntive  
  
### Proprietà di avvio HPC  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**Nodo head**|Specifica il computer utilizzato come nodo head HPC nell'esecuzione della profilatura.|  
|**Numero di processi**|Specifica il numero di istanze dell'applicazione da eseguire nell'applicazione profilata.|  
|**Esegui profilo su priorità**|Per profilare un processo specifico nel cluster, selezionare l'opzione **Esegui profilo su priorità**, quindi selezionare la priorità del processo dall'elenco a discesa.|  
|**Esegui profilo su nodo**|Per profilare il processo o i processi eseguiti su un nodo specifico nel cluster HPC, selezionare l'opzione **Esegui profilo su nodo**, quindi selezionare il nodo dall'elenco a discesa.|  
|**Cartella di lavoro remota**|Specifica il percorso della cartella utilizzata dalle istanze del processo sui singoli nodi di calcolo.|  
|**Percorso di distribuzione**|Specifica il percorso della directory utilizzata dal server HPC per la gestione temporanea di immagini per la distribuzione.|  
  
### Proprietà avanzate  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**Nome progetto**|Il nome del progetto o della soluzione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] corrente.|  
|**Esegui pulizia all'arresto del profiler**|Quando è true, rimuove i binari distribuiti alla directory di esecuzione.  File e directory creati dal programma utente non vengono rimossi in questo passaggio.  Se la directory di esecuzione e la directory di distribuzione sono state create dall'IDE, l'IDE stesso tenterà di rimuoverle, salvo che contengano file non distribuiti dall'IDE.|  
|**File aggiuntivi da distribuire**|Specifica un elenco di file aggiuntivi separati da punto e virgola da distribuire sul nodo di calcolo.  È possibile fare clic sul pulsante con i puntini di sospensione \(**...**\) per selezionare più file utilizzando una finestra di dialogo.|  
|**Comando Mpiexec**|Specifica l'applicazione che avvia l'applicazione MPI.  Il valore predefinito è **mpiexec.exe**.|  
|**Argomenti Mpiexec**|Specifica gli argomenti da passare al comando mpiexec.exe.|  
|**Nodi richiesti nel cluster**|Specifica il numero di nodi nel cluster su cui eseguire l'applicazione.|  
|**Distribuisci file CRT**|Quando è true, distribuisce il run\-time C\/C\+\+ nel cluster.|  
|**Script pre\-profilo**|Specifica il percorso e il nome file di uno script da eseguire sul computer di sviluppo locale prima dell'avvio della sessione di profilatura.|  
|**Argomenti script pre\-profilo**|Specifica gli argomenti da passare allo script pre\-profilo.|  
|**Script post\-profilo**|Specifica il percorso e il nome file di uno script da eseguire sul computer di sviluppo locale al termine della sessione di profilatura.|  
|**Argomenti script post\-profilo**|Specifica gli argomenti da passare allo script post\-profilo.|