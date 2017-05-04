---
title: "Debug di soluzioni SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.WebConfigModificationDialog"
  - "VS.SharePointTools.Project.DebuggingNotEnabled"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, debug"
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Debug di soluzioni SharePoint
  È possibile eseguire il debug di soluzioni SharePoint utilizzando il debugger di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Quando si inizia il debug, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] distribuisce i file di progetto al server SharePoint, quindi apre un'istanza del sito di SharePoint nel browser.  Nelle sezioni seguenti viene illustrato come eseguire il debug delle applicazioni di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Abilitazione del debug](#EnableDebug)  
  
-   [Debug con F5 e processo di distribuzione](#Deployment)  
  
-   [Funzionalità del progetto SharePoint](#Features)  
  
-   [Debug di flussi di lavoro](#Workflow)  
  
-   [Debug di ricevitori di eventi di funzionalità](#FeatureEvents)  
  
-   [Abilitazione delle informazioni di debug avanzate](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a> Abilitazione del debug  
 Quando si esegue per la prima volta il debug di una soluzione SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], in una finestra di dialogo viene visualizzato un avviso in cui è specificato che il file web.config non è configurato per abilitare il debug. Tale file viene creato quando si installa il server SharePoint.  Per ulteriori informazioni, vedere [Utilizzo dei file Web.config](http://go.microsoft.com/fwlink/?LinkID=149266)\). La finestra di dialogo consente di scegliere se eseguire il progetto senza il debug o se modificare il file web.config per abilitare il debug.  Se si sceglie la prima opzione, il progetto viene eseguito normalmente.  Se si sceglie la seconda opzione, il file web.config viene configurato per:  
  
-   Attivare lo stack di chiamate \(`CallStack="true"`\)  
  
-   Disabilitare gli errori personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(`<customErrors mode="Off" />`\)  
  
-   Abilitare il debug di compilazione \(`<compilation debug="true">`\)  
  
 Di seguito è riportato il file web.config risultante:  
  
```  
  
<configuration>  
    ...  
    <SharePoint>  
        <SafeMode MaxControls="200"  
            CallStack="true"  
            DirectFileDependencies="10"  
            TotalFileDependencies="50"  
            AllowPageLevelTrace="false">  
            ...  
        </SafeMode>  
    ...  
    </SharePoint>  
    <system.web>  
        ...  
        <customErrors mode="Off" />  
        ...  
        <compilation debug="true">  
        ...  
        </compilation>  
        ...  
    </system.web>  
    ...  
</configuration>  
```  
  
 Per annullare le modifiche e disabilitare il debug, modificare il seguente codice [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] nel file web.config:  
  
-   Disattivare lo stack di chiamate \(`CallStack="false"`\)  
  
-   Abilitare gli errori personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(`<customErrors mode="On" />`\)  
  
-   Disabilitare il debug di compilazione \(`<compilation debug="false">`\)  
  
##  <a name="Deployment"></a> Debug con F5 e processo di distribuzione  
 Quando si esegue il progetto SharePoint nella modalità di debug, il processo di distribuzione di SharePoint effettua le attività seguenti:  
  
1.  Esegue i comandi precedenti alla distribuzione personalizzabili.  
  
2.  Crea un file del pacchetto della soluzione Web \(con estensione wsp\) mediante i comandi [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Il file con estensione wsp include tutti i file e le funzionalità necessari.  Per ulteriori informazioni, vedere [Panoramica delle soluzioni](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3.  Se la soluzione SharePoint è una soluzione della farm, ricicla il pool di applicazioni [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] per l'[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] del sito specificato.  Questo passaggio rilascia i file bloccati dal processo di lavoro [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)].  
  
4.  Se è già presente una versione precedente del pacchetto, ritrae la versione precedente dei file e delle funzionalità nel file con estensione wsp.  Questo passaggio disattiva le funzionalità, disinstalla il pacchetto della soluzione, quindi lo elimina dal server SharePoint.  
  
5.  Installa la versione corrente dei file e delle funzionalità nel file con estensione wsp.  Questo passaggio aggiunge e installa la soluzione nel server SharePoint.  
  
6.  Installa l'assembly per i flussi di lavoro.  È possibile modificare il percorso tramite la proprietà *Assembly Location*.  
  
7.  Attiva la funzionalità del progetto in SharePoint se l'ambito è Sito o Web.  Le funzionalità negli ambiti Farm e WebApplication non sono attivate.  
  
8.  Associa il flusso di lavoro alla libreria, all'elenco o al sito di SharePoint selezionati nella **Personalizzazione guidata SharePoint**.  
  
    > [!NOTE]  
    >  Questa associazione si verifica solo se nella procedura guidata è stata selezionata l'opzione **Associa flusso di lavoro automaticamente**.  
  
9. Esegue i comandi successivi alla distribuzione personalizzabili.  
  
10. Attribuisce il debugger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al processo [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] \(w3wp.exe\).  Se il tipo di progetto consente di modificare la proprietà *Sandboxed Solution* ed il suo valore è impostato a **true**, allora il debugger viene connesso a un processo diverso \(SPUCWorkerProcess.exe\).  Per ulteriori informazioni, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Avvia il debugger di JavaScript se la soluzione SharePoint è una soluzione della farm.  
  
12. Visualizza la libreria, l'elenco o la pagina del sito appropriato nel browser.  
  
 Dopo il completamento di ogni attività, nella finestra di output di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene visualizzato un messaggio di stato.  Se non è possibile completare un'attività, nella finestra Elenco errori di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene visualizzato un messaggio di errore.  
  
##  <a name="Features"></a> Funzionalità del progetto SharePoint  
 Una funzionalità è un'unità di funzionalità modulare e portatile che semplifica la modifica dei siti attraverso le relative definizioni.  Inoltre è un pacchetto di elementi di [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] \(WSS\) che può essere attivato per un ambito specifico e che consente agli utenti di raggiungere un particolare obiettivo o effettuare una determinata attività.  I modelli vengono distribuiti come funzionalità.  
  
 Quando si esegue un progetto in modalità di debug, il processo di distribuzione crea una cartella nella directory delle *funzionalità* in %COMMONPROGRAMFILES%\\Microsoft Shared\\web server extensions\\14\\TEMPLATE\\FEATURES.  I nomi della funzionalità hanno il formato *project name*\_Feature*x*, ad esempio TestProject\_Feature1.  
  
 La cartella della soluzione nella directory delle caratteristiche contiene un file di *definizione della caratteristica* e un file di *definizione del flusso di lavoro*.  Nel file di definizione della funzionalità \(Feature.xml\) vengono descritti i file contenuti nella funzionalità del progetto.Nel file di definizione del progetto \(Elements.xml\) viene descritto il modello di progetto.  Elements.xml è disponibile in **Esplora soluzioni**, tuttavia Feature.xml viene generato durante la creazione del pacchetto della soluzione.  Per ulteriori informazioni su questi file, vedere [Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
##  <a name="Workflow"></a> Debug di flussi di lavoro  
 Quando si esegue il debug di progetti flusso di lavoro, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il modello di flusso di lavoro \(a seconda del tipo\) a una libreria o a un elenco.  Successivamente, il modello di flusso di lavoro può essere avviato manualmente oppure aggiungendo o aggiornando un elemento.  Per eseguire il debug del flusso di lavoro è quindi possibile utilizzare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!NOTE]  
>  Se si aggiungono riferimenti ad altri assembly, assicurarsi che tali assembly siano installati nella Global Assembly Cache \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\).  In caso contrario, si verificherà un errore nella soluzione flusso di lavoro.  Per informazioni sull'installazione degli assembly, vedere [Avviare manualmente un flusso di lavoro per un documento o un elemento](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
 Tuttavia, il flusso di lavoro non viene avviato dal processo di distribuzione,  ma deve essere avviato dal sito Web di SharePoint.  È anche possibile avviare il flusso di lavoro utilizzando un'applicazione client, ad esempio Microsoft Office Word 2010, oppure utilizzando codice separato sul lato server.  Utilizzare uno degli approcci specificati in **Personalizzazione guidata SharePoint**.  
  
 Ad esempio, se si è specificato che il flusso di lavoro può essere avviato manualmente, avviarlo direttamente dall'elemento contenuto nella libreria o nell'elenco.  Per ulteriori informazioni su come avviare un flusso di lavoro manualmente, vedere [Avviare manualmente un flusso di lavoro su un elemento del documento](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
##  <a name="FeatureEvents"></a> Debug di ricevitori di eventi di funzionalità  
 Per impostazione predefinita, quando si esegue un'applicazione di SharePoint di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le funzionalità vengono attivate automaticamente sul server SharePoint.  Tuttavia, questa operazione causa dei problemi quando si esegue il debug dei ricevitori di eventi di funzionalità, perché quando una funzionalità viene attivata da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], viene eseguita in un processo diverso dal debugger.  Di conseguenza, alcune funzionalità di debug, ad esempio i punti di interruzione, non funzioneranno correttamente.  
  
 Per disabilitare l'attivazione automatica della funzionalità in SharePoint e consentire un debug corretto dei ricevitori di eventi di funzionalità, impostare il valore della proprietà **Configurazione distribuzione attiva** del progetto su **Nessuna attivazione** prima di eseguire il debug.  Successivamente, dopo aver avviato il debug della propria applicazione di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], attivare manualmente la funzionalità in SharePoint.  Per attivare la funzionalità, fare clic sul menu **Azioni sito** in SharePoin, scegliere **Impostazioni sito**, selezionare il collegamento **Gestisci funzionalità sito**, quindi fare clic sul pulsante **Attiva** accanto alla funzionalità e riprendere normalmente il debug.  
  
##  <a name="EnhancedDebug"></a> Abilitazione delle informazioni di debug avanzate  
 A causa delle interazioni a volte complesse tra il processo di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(devenv.exe\), il processo host di SharePoint di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(vssphost4.exe\), SharePoint e il livello WCF, la diagnosi degli errori che si verificano durante la compilazione, la distribuzione e altre operazioni può risultare difficile.  Per risolvere tali errori, è possibile abilitare le informazioni di debug avanzate.  A tal fine, individuare la seguente chiave del Registro di sistema di Windows:  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools\]  
  
 Se il valore "EnableDiagnostics" **REG\_DWORD** non esiste, è necessario crearlo manualmente.  Impostare il valore "EnableDiagnostics" a " 1".  
  
 Con l'impostazione del valore di questa chiave su 1, si ottiene la visualizzazione delle informazioni sulla traccia dello stack nella finestra **Output** ogni volta che si verificano errori del sistema del progetto durante l'esecuzione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per disabilitare le informazioni di debug avanzate, impostare EnableDiagnostics di nuovo a 0, oppure eliminare il valore.  
  
 Per ulteriori informazioni su altre chiavi del Registro di sistema di SharePoint, vedere [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Risoluzione dei problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  