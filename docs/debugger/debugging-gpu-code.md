---
title: "Debug del codice GPU | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug del codice GPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile eseguire il debug del codice C\+\+ in esecuzione nell'unità di elaborazione grafica \(GPU\).  Il supporto del debug di GPU in Visual Studio include il rilevamento di race condition, l'avvio di processi e la connessione a essi e l'integrazione nelle finestre di debug.  
  
## Piattaforme supportate  
 Il debug è supportato in [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] e [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)].  Per eseguire il debug nell'emulatore software, è necessario disporre di [!INCLUDE[win8](../debugger/includes/win8_md.md)] o [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)].  Per eseguire il debug nell'hardware, è necessario installare i driver per la scheda grafica.  Non tutti i fornitori di hardware implementano tutte le funzionalità del debugger.  Vedere la documentazione del fornitore per eventuali limitazioni.  
  
> [!NOTE]
>  I fornitori di hardware indipendenti che desiderano supportare il debug della GPU in Visual Studio devono creare una DLL che implementi l'interfaccia di VSD3DDebug e faccia riferimento ai propri driver.  
  
## Configurazione del debug della GPU  
 Il debugger non può interrompere sia il codice della CPU sia quello della GPU nell'esecuzione della stessa app.  Per impostazione predefinita, il debugger interrompe il codice della CPU.  Per eseguire il debug del codice della GPU, utilizzare uno dei due passaggi seguenti:  
  
-   Nell'elenco **Tipo di debug** sulla barra degli strumenti **Standard** scegliere **Solo GPU**.  
  
-   In **Esplora soluzioni** scegliere **Proprietà** dal menu di scelta rapida del progetto.  Nella finestra di dialogo **Pagine delle proprietà**, selezionare **Debug** e **Solo GPU** nell'elenco **Tipo di debugger**.  
  
## Avvio e associazione di applicazioni  
 È possibile utilizzare i comandi di debug di Visual Studio per avviare e interrompere il debug della GPU.  Per ulteriori informazioni, vedere [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md).  È inoltre possibile associare il debugger della GPU a un processo in esecuzione, ma solo se tale processo esegue codice della GPU.  Per ulteriori informazioni, vedere [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## Esegui Tile corrente fino al cursore ed Esegui fino al cursore  
 Quando si esegue il debug nella GPU, sono disponibili due opzioni per l'esecuzione fino alla posizione del cursore.  I controlli per entrambe le opzioni sono disponibili nel menu di scelta rapida dell'editor di codice.  
  
1.  Con il comando **Esegui fino al cursore** l'app viene eseguita finché non raggiunge la posizione del cursore, quindi si interrompe.  Ciò non implica che il thread corrente venga eseguito fino al cursore, ma piuttosto che il primo thread che raggiunge il punto del cursore genera l'interruzione.  Vedere [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)  
  
2.  Con il comando **Esegui Tile corrente fino al cursore** l'app viene eseguita finché tutti thread nel tile corrente non raggiungono il cursore, quindi si interrompe.  
  
## Debug di Windows  
 L'utilizzo di alcune finestre di debug consente di esaminare, contrassegnare e bloccare i thread della GPU.  Per ulteriori informazioni, vedere:  
  
-   [Utilizzo della finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)  
  
-   [Utilizzo della finestra Attività](../debugger/using-the-tasks-window.md)  
  
-   [Procedura: utilizzare la finestra Espressione di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md)  
  
-   [Debug di thread e processi](../debugger/debug-threads-and-processes.md) \(barra degli strumenti Posizione di debug\)  
  
-   [Procedura: utilizzare la finestra Thread GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## Eccezioni di sincronizzazione dei dati  
 Il debugger può identificare diverse condizioni di sincronizzazione dei dati durante l'esecuzione.  Quando viene rilevata una condizione, il debugger attivo lo stato di interruzione.  Sono disponibili due opzioni: **Interrompi** o **Continua**.  Tramite la finestra di dialogo **Eccezioni** è possibile configurare il debugger affinché rilevi o meno tali condizioni nonché quali condizioni causano l'interruzione.  Per ulteriori informazioni, vedere [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md).  È inoltre possibile utilizzare la finestra di dialogo **Opzioni** per specificare che il debugger deve ignorare le eccezioni se i dati scritti non modificano il valore dei dati.  Per ulteriori informazioni, vedere [Generale, Debug, finestra di dialogo Opzioni](../debugger/general-debugging-options-dialog-box.md).  
  
## Risoluzione dei problemi  
  
### Specifica di un acceleratore  
 I punti di interruzione nel codice della GPU vengono raggiunti solo se il codice è in esecuzione nell'acceleratore [accelerator::direct3d\_ref](../Topic/accelerator::direct3d_ref%20Data%20Member.md) \(REF\).  Se non si specifica un acceleratore nel codice, l'acceleratore REF viene automaticamente selezionato come **Tipo acceleratore debug** nelle proprietà del progetto.  Se il codice seleziona in modo esplicito un acceleratore, l'acceleratore REF non viene utilizzato durante il debug e i punti di interruzione non vengono raggiunti a meno che l'hardware della GPU non supporti il debug.  È possibile risolvere questo problema scrivendo il codice in modo da utilizzare l'acceleratore REF durante il debug.  Per ulteriori informazioni, vedere le proprietà del progetto, [Utilizzo degli oggetti accelerator e accelerator\_view](/visual-cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) e [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### Punti di interruzione condizionali  
 I punti di interruzione condizionali nel codice della GPU sono supportati, ma non è possibile valutare tutte le espressioni nel dispositivo.  Quando un'espressione non può essere valutata nel dispositivo, essa viene valutata nel debugger.  È probabile che il debugger sia più lento del dispositivo.  
  
### Errore: Problema di configurazione con il tipo di acceleratore di debug selezionato.  
 Questo errore si verifica quando è presente un'incoerenza tra le impostazioni del progetto e la configurazione del PC in cui si esegue il debug.  Per ulteriori informazioni, vedere [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### Errore: Il driver di debug per il tipo di acceleratore di debug selezionato non è installato nel computer di destinazione.  
 Questo errore si verifica se si esegue il debug in un computer remoto.  Il debugger non è in grado di determinare se i driver sono installati nel computer remoto fino al runtime.  I driver sono disponibili tramite il produttore della scheda grafica.  
  
### Errore: Timeout Detection and Recovery \(TDR\) deve essere disabilitato nel sito remoto.  
 È possibile che i calcoli di C\+\+ AMP superino l'intervallo predefinito impostato tramite il processo Timeout Detection and Recovery \(TDR\) di Windows.  In tal caso, il calcolo viene annullato e i dati vengono persi.  Per ulteriori informazioni, vedere [Gestione di TDR in C\+\+ AMP](http://go.microsoft.com/fwlink/p/?LinkId=249154).  
  
## Vedere anche  
 [Procedura dettagliata: Debug di un'applicazione C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)   
 [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Avviare il debug della GPU in Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=255381)