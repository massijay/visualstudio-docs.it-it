---
title: "How to: Publish a WPF Application with Visual Styles Enabled | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 3
caps.handback.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# How to: Publish a WPF Application with Visual Styles Enabled
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli stili di visualizzazione consentono ai controlli di modificare il loro aspetto in base al tema scelto dall'utente.  Per impostazione predefinita, gli stili di visualizzazione non sono abilitati per le applicazioni di Windows Presentation Foundation \(WPF\), pertanto è necessario abilitarle manualmente.  Tuttavia, attivare gli stili di visualizzazione per un'applicazione WPF e quindi pubblicare la soluzione genera un errore.  In questo argomento viene descritto come risolvere questo errore e il processo per pubblicare un'applicazione WPF con gli stili visivi attivati.  Per ulteriori informazioni sugli stili di visualizzazione, vedere [Visual Styles Overview](http://msdn.microsoft.com/it-it/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e).  Per ulteriori informazioni sui messaggi d'errore, vedere [Troubleshooting Specific Errors in ClickOnce Deployments](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Per correggere l'errore e pubblicare la soluzione, è necessario effettuare le attività seguenti:  
  
-   [Pubblicare la soluzione senza stili visivi attivati](#BKMK_publishsolwovs).  
  
-   [Creare un file manifesto](#BKMK_CreateManifest).  
  
-   [Importare il file manifesto nel file eseguibile della soluzione pubblicata.](#BKMK_embedmanifest).  
  
-   [Firma dei manifesti dell'applicazione e della distribuzione.](#BKMK_signappdeplyman).  
  
 Quindi, è possibile spostare i file pubblicati nella posizione da cui si desidera che gli utenti finali installino l'applicazione.  
  
##  <a name="BKMK_publishsolwovs"></a> Pubblicare la soluzione senza stili visivi attivati  
  
1.  Assicurarsi che il progetto non disponga di stili visivi attivati.  Innanzitutto, selezionare il file manifesto del progetto per il codice XML seguente.  Quindi, se il formato XML è presente, racchiudere XML in un tag di commento.  
  
     Gli stili di visualizzazione non sono attivati per impostazione predefinita.  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Le procedure riportate di seguito illustrano come aprire il file manifesto associato al progetto.  
  
    ###### Aprire il file manifesto in un progetto di Visual Basic.  
  
    1.  Dal menu, scegliere **Progetto**, *ProjectName***Proprietà**, dove *ProjectName* è il nome del progetto WPF.  
  
         Verranno visualizzate le pagine delle proprietà del progetto WPF.  
  
    2.  Nella scheda **Applicazione**, scegliere **Visualizza Impostazioni di Windows**.  
  
         Il file app.manifest verrà visualizzato nel **Code Editor**.  
  
    ###### Aprire il file manifesto in un progetto C\#  
  
    1.  Dal menu, scegliere **Progetto**, *ProjectName***Proprietà**, dove *ProjectName* è il nome del progetto WPF.  
  
         Verranno visualizzate le pagine delle proprietà del progetto WPF.  
  
    2.  Nella scheda **Applicazione**, prendere nota del nome visualizzato nel campo manifesto.  Si tratta del nome del manifesto associato al progetto.  
  
        > [!NOTE]
        >  Se nel campo manifesto vengono visualizzati **Incorpora manifesto con impostazioni predefinite** o **Crea applicazione senza manifesto**, gli stili di visualizzazione non sono abilitati.  Se il nome di un file manifesto viene visualizzato nel campo manifesto, procedere al passaggio successivo di questa procedura.  
  
    3.  In **Esplora soluzioni** selezionare **Mostra tutti i file** \(\).  
  
         Questo pulsante mostra tutti gli elementi di progetto, inclusi quelli che sono esclusi e quelli normalmente nascosti.  Il file manifesto verrà visualizzato come elemento di progetto.  
  
2.  Compilare e pubblicare la soluzione.  Per ulteriori informazioni sulla pubblicazione di una soluzione, vedere [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a> Creare un file manifesto  
  
1.  Incollare il codice XML riportato di seguito in un file del Blocco note.  
  
     Questo file XML descrive l'assembly contenente i controlli che supportano gli stili di visualizzazione.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  Nel Blocco note scegliere **Salva con nome** del menu **File**.  
  
3.  Nella finestra di dialogo **Salva con nome** selezionare **Tutti i file** nell'elenco a discesa **Salva come**.  
  
4.  Nella casella **Nome file**, denominare il file e aggiungere .manifest alla fine del nome file.  Ad esempio: themes.manifest.  
  
5.  Selezionare il pulsante **Sfoglia cartelle**, scegliere una cartella qualsiasi, quindi fare clic su **Salva**.  
  
    > [!NOTE]
    >  Le procedure restanti assumono che il nome del file sia themes.manifest e che il file venga salvato nella directory C:\\temp del computer.  
  
##  <a name="BKMK_embedmanifest"></a> Importare il file manifesto nel file eseguibile della soluzione pubblicata.  
  
1.  Aprire il **Prompt dei comandi di Visual Studio**.  
  
     Per ulteriori informazioni su come aprire il **Prompt dei Comandi di Visual Studio**, vedere [Prompt dei comandi](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md).  
  
    > [!NOTE]
    >  I passaggi restanti fanno le seguenti assunzioni riguardo alla soluzione:  
    >   
    >  -   Il nome della soluzione è MyWPFProject.  
    > -   La soluzione si trova nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
    >   
    >      La soluzione viene pubblicata nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
    > -   La versione più recente dei file dell'applicazione pubblicata si trova nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  Non è necessario utilizzare il nome o il percorso di directory descritto in precedenza.  Il nome e i percorsi descritti in precedenza vengono utilizzati solo per illustrare i passaggi necessari per pubblicare la soluzione.  
  
2.  Sul prompt dei comandi, modificare il percorso della directory contenente la versione più recente dei file pubblicati dell'applicazione.  Nell'esempio che segue viene illustrato questo passo.  
  
    ```  
    cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  Sul prompt dei comandi, eseguire il comando seguente per importare il file manifesto nel file eseguibile dell'applicazione.  
  
    ```  
    mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a> Firma dei manifesti dell'applicazione e della distribuzione.  
  
1.  Sul prompt dei comandi, eseguire il comando seguente per rimuovere l'estensione `.deploy` dal file eseguibile nella directory corrente.  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  In questo esempio si presuppone che un solo file abbia l'estensione `.deploy`.  Assicurarsi di rinominare tutti i file nella directory con l'estensione di file `.deploy`.  
  
2.  Sul prompt dei comandi, eseguire il comando seguente per firmare il manifesto dell'applicazione.  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  In questo esempio si presuppone che i manifest siano firmati tramite il file `.pfx` del progetto.  Se non si firma del manifesto, è possibile omettere il parametro `–cf` di questo esempio.  Se si firmano i manifesti con un certificato che richiede una password, specificare l'opzione `–password` \(`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`\).  
  
3.  Sul prompt dei comandi, eseguire il comando seguente per aggiungere l'estensione `.deploy` al nome del file rinominato in un passaggio precedente di questa procedura.  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  In questo esempio si presuppone che un solo file abbia l'estensione `.deploy`.  Assicurarsi di rinominare tutti i file nella directory che avevano precedentemente l'estensione di file `.deploy`.  
  
4.  Sul prompt dei comandi, eseguire il comando seguente per firmare il manifesto di distribuzione.  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  In questo esempio si presuppone che i manifest siano firmati tramite il file `.pfx` del progetto.  Se non si firma il manifesto, è possibile omettere il parametro `–cf` di questo esempio.  Se si firmano i manifesti con un certificato che richiede una password, specificare l'opzione `–password`, come da esempio:`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`.  
  
 Dopo avere eseguito queste operazioni, è possibile spostare i file pubblicati nella posizione da cui si desidera che gli utenti finali installino l'applicazione.  Se si desidera aggiornare spesso la soluzione, è possibile spostare i controlli in uno script ed eseguire lo script ogni volta che si pubblica una nuova versione.  
  
## Vedere anche  
 [Troubleshooting Specific Errors in ClickOnce Deployments](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Visual Styles Overview](http://msdn.microsoft.com/it-it/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Enabling Visual Styles](VS|Controls|~\controls\userex\cookbook.htm)   
 [Prompt dei comandi](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md)