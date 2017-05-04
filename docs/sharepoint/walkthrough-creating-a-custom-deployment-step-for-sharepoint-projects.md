---
title: "Walkthrough: Creating a Custom Deployment Step for SharePoint Projects | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Walkthrough: Creating a Custom Deployment Step for SharePoint Projects
  Quando si distribuisce un progetto SharePoint, Visual Studio esegue una serie di passaggi di distribuzione in un ordine specifico.  Visual Studio include molti passaggi di distribuzione incorporati, tuttavia è possibile crearne di personalizzati.  
  
 In questa procedura dettagliata, verrà creato un passaggio di distribuzione personalizzato per aggiornare soluzioni in un server che esegue SharePoint.  Visual Studio include passaggi di distribuzione incorporati per molte attività, tali soluzioni di ritrazione o l'aggiunta, ma non include un passaggio di distribuzione per l'aggiornamento delle soluzioni.  Per impostazione predefinita, quando si distribuisce una soluzione SharePoint, tramite Visual Studio prima ritrae la soluzione \(se è già distribuito\) e quindi ridistribuisce l'intera soluzione.  Per ulteriori informazioni sui passaggi di distribuzione incorporati, vedere [Distribuzione, pubblicazione e aggiornamento dei pacchetti delle soluzioni SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che esegue due attività principali:  
  
    -   L'estensione definisce un passaggio di distribuzione personalizzato per aggiornare soluzioni SharePoint.  
  
    -   L'estensione crea un'estensione di progetto che definisce una nuova configurazione di distribuzione, un set di passaggi di distribuzione eseguito per un progetto specifico.  La nuova configurazione di distribuzione include il passaggio di distribuzione personalizzato e molti passaggi di distribuzione incorporati.  
  
-   Creazione di due comandi di SharePoint personalizzati che l'assembly di estensioni chiama.  I comandi di SharePoint sono metodi che possono essere chiamati dagli assembly di estensioni per utilizzare le API nel modello a oggetti del server di SharePoint.  Per ulteriori informazioni, vedere [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Compilazione di un pacchetto Visual Studio Extension \(VSIX\) per distribuire entrambi gli assembly.  
  
-   Test del nuovo passaggio di distribuzione.  
  
## Prerequisiti  
 Per completare la procedura dettagliata, nel computer di sviluppo devono essere presenti i componenti elencati di seguito:  
  
-   Edizioni supportate di Windows, SharePoint e Visual Studio.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK.  In questa procedura dettagliata viene utilizzato il modello **VSIX Project** di SDK per creare un pacchetto VSIX e distribuire l'estensione.  Per ulteriori informazioni, vedere [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Per completare la procedura dettagliata è consigliabile conoscere i concetti riportati di seguito:  
  
-   Utilizzo del modello a oggetti del server di SharePoint.  Per ulteriori informazioni, vedere l'articolo relativo all'[utilizzo del modello a oggetti lato server di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796) \(la pagina potrebbe essere in inglese\).  
  
-   Soluzioni SharePoint.  Per ulteriori informazioni, vedere [Cenni preliminari sulle soluzioni](http://go.microsoft.com/fwlink/?LinkId=169422) \(la pagina potrebbe essere in inglese\).  
  
-   Aggiornamento delle soluzioni SharePoint.  Per ulteriori informazioni, vedere l'articolo relativo all'[aggiornamento di una soluzione](http://go.microsoft.com/fwlink/?LinkId=177802) \(la pagina potrebbe essere in inglese\).  
  
## Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario creare tre progetti:  
  
-   Un progetto VSIX per creare il pacchetto VSIX allo scopo di distribuire l'estensione.  
  
-   Un progetto Libreria di classi che implementa l'estensione.  Questo progetto deve essere destinato a .NET Framework 4,5.  
  
-   Un progetto Libreria di classi che definisce i comandi di SharePoint personalizzati.  Questo progetto deve essere destinato a .NET Framework 3.5.  
  
 Iniziare la procedura dettagliata creando i progetti.  
  
#### Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Sulla barra dei menu, scegliere **Il file**, **Nuova**, **Project**.  
  
3.  Nella finestra di dialogo **Nuovo progetto**, espandere i nodi **Visual Basic** o **Visual C\#** quindi selezionare il nodo **Extensibility**.  
  
    > [!NOTE]  
    >  Il nodo **Extensibility** è disponibile solo se si installa Visual Studio SDK.  Per ulteriori informazioni, vedere la sezione precedente relativa ai prerequisiti.  
  
4.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di.NET Framework.  
  
5.  Scegliere il modello **Progetto VSIX**, denominare il progetto **UpgradeDeploymentStep**quindi scegliere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **UpgradeDeploymentStep** a **Esplora soluzioni**.  
  
#### Per creare il progetto di estensione  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo della soluzione UpgradeDeploymentStep, scegliere **Aggiungi**quindi scegliere **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo quando la casella di controllo **Mostra sempre soluzione** viene selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Nella finestra di dialogo **Nuovo progetto**, espandere i nodi **Visual Basic** o **Visual C\#** quindi selezionare il nodo **Finestre**.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di.NET Framework.  
  
4.  Scegliere il modello di progetto **Libreria di classi**, denominare il progetto **DeploymentStepExtension**quindi scegliere il pulsante **OK**.  
  
     In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il progetto **DeploymentStepExtension** viene aggiunto alla soluzione e viene aperto il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
#### Per creare il progetto di comandi di SharePoint  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo della soluzione UpgradeDeploymentStep, scegliere **Aggiungi**quindi scegliere **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo quando la casella di controllo **Mostra sempre soluzione** viene selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Nella finestra di dialogo **Nuovo progetto**, espandere **Visual C\#** o **Visual Basic**quindi selezionare il nodo **Finestre**.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 3.5** nell'elenco delle versioni di.NET Framework.  
  
4.  Scegliere il modello di progetto **Libreria di classi**, denominare il progetto **SharePointCommands**quindi scegliere il pulsante **OK**.  
  
     Visual Studio aggiunge il progetto **SharePointCommands** alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## Configurazione dei progetti  
 Prima di scrivere codice per creare il passaggio di distribuzione personalizzato, è necessario aggiungere file di codice e i riferimenti ad assembly e configurare i progetti.  
  
#### Per configurare il progetto DeploymentStepExtension  
  
1.  Nel progetto **DeploymentStepExtension**, aggiungere due file di codice con i nomi seguenti:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Aprire il menu di scelta rapida del progetto DeploymentStepExtension quindi scegliere **Aggiungi riferimento**.  
  
3.  Nella scheda **Framework**, selezionare la casella di controllo dell'assembly System.ComponentModel.Composition.  
  
4.  Nella scheda **Estensioni**, selezionare la casella di controllo per un assembly Microsoft.VisualStudio.SharePoint quindi scegliere il pulsante **OK**.  
  
#### Per configurare il progetto SharePointCommands  
  
1.  Nel progetto **SharePointCommands**, aggiungere un file di codice denominato Commands.  
  
2.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo del progetto **SharePointCommands** quindi scegliere **Aggiungi riferimento**.  
  
3.  Nella scheda **Estensioni**, selezionare le caselle di controllo per i seguenti assembly quindi fare clic sul pulsante **OK**  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## Definizione del passaggio di distribuzione personalizzato  
 Creare una classe che definisce il passaggio di distribuzione dell'aggiornamento.  Per definire il passaggio di distribuzione, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>.  Implementare questa interfaccia quando si desidera definire un passaggio di distribuzione personalizzato.  
  
#### Per definire il passaggio di distribuzione personalizzato  
  
1.  Nel progetto **DeploymentStepExtension**, aprire il file di codice UpgradeStep e quindi incollare il codice seguente in.  
  
    > [!NOTE]  
    >  Dopo aver aggiunto questo codice, il progetto presenterà alcuni errori di compilazione, ma verranno risolti quando si aggiunge codice nei passaggi successivi.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#1)]  
  
## Creazione di una configurazione di distribuzione che include il passaggio di distribuzione personalizzato  
 Creare un'estensione di progetto per la nuova configurazione di distribuzione, che include molti passaggi di distribuzione incorporati e il nuovo passaggio di distribuzione di aggiornamento.  Crea questa estensione, aiutate gli sviluppatori di SharePoint a utilizzare il passaggio di distribuzione di aggiornamento nei progetti SharePoint.  
  
 Per creare la configurazione di distribuzione, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Implementare questa interfaccia quando si desidera creare un'estensione di progetto SharePoint.  
  
#### Per creare la configurazione di distribuzione  
  
1.  Nel progetto **DeploymentStepExtension**, aprire il file di codice DeploymentConfigurationExtension quindi incollare il codice seguente in.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## Creazione di comandi personalizzati di SharePoint  
 Creare due controlli personalizzati che effettuano chiamate nel modello a oggetti del server di SharePoint.  Un comando determina se una soluzione è già distribuita, l'altro aggiorna una soluzione.  
  
#### Per definire i comandi di SharePoint  
  
1.  Nel progetto **SharePointCommands**, aprire il file di codice dei comandi e quindi incollare il codice seguente in.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#4)]  
  
## Verifica  
 In questa fase della procedura dettagliata, tutto il codice per il passaggio di distribuzione personalizzato e i comandi di SharePoint si trovano nei progetti.  Compilare questi ultimi per assicurarsi che vengano compilati senza errori.  
  
#### Per compilare progetti  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del progetto **DeploymentStepExtension** quindi scegliere **Compilazione**.  
  
2.  Aprire il menu di scelta rapida del progetto **SharePointCommands** quindi scegliere **Compilazione**.  
  
## Creazione di un pacchetto VSIX per distribuire l'estensione  
 Per distribuire l'estensione, utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX.  Innanzitutto, configurare il pacchetto VSIX modificando il file source.extension.vsixmanifest nel progetto VSIX.  Successivamente creare il pacchetto VSIX compilando la soluzione.  
  
#### Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora soluzioni**, sotto il progetto **UpgradeDeploymentStep**, aprire il menu di scelta rapida per il file **source.extension.vsixmanifest** quindi scegliere **Apri**.  
  
     Visual Studio consente di aprire il file nell'editor del manifesto.  Il file source.extension.vsixmanifest è la base del file extension.vsixmanifest che tutti i pacchetti VSIX richiedono.  Per ulteriori informazioni su questo file, vedere [Informazioni di riferimento sullo schema dell'estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nella casella **Nome prodotto**, immettere **Aggiorna fase di distribuzione per progetti SharePoint**.  
  
3.  Nella casella **Autore**, immettere **Contoso**.  
  
4.  Nella casella **Descrizione**, immettere **Fornisce un passaggio di distribuzione personalizzato di aggiornamento che può essere utilizzato nei progetti SharePoint**.  
  
5.  Nella scheda **Asset** dell'editor, scegliere il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** visualizzato.  
  
6.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde all'elemento `MefComponent` del file extension.vsixmanifest.  Questo elemento specifica il nome di un assembly dell'estensione nel pacchetto VSIX.  Per ulteriori informazioni, vedere [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nell'elenco **Alimentazione**, scegliere **Progetto nella soluzione corrente**.  
  
8.  Nell'elenco **Project**, scegliere **DeploymentStepExtension**quindi scegliere il pulsante **OK**.  
  
9. Nell'editor del manifesto, scegliere nuovamente il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** visualizzato.  
  
10. Nell'elenco **Tipo**, immettere **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Questo elemento specifica un'estensione personalizzata che si desidera includere nell'estensione di Visual Studio.  Per ulteriori informazioni, vedere [Elemento di risorsa \(schema VSX\)](http://msdn.microsoft.com/it-it/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. Nell'elenco **Alimentazione**, scegliere **Progetto nella soluzione corrente**.  
  
12. Nell'elenco **Project**, scegliere **SharePointCommands**quindi scegliere il pulsante **OK**.  
  
13. Sulla barra dei menu, scegliere **Compilazione**, **Compila soluzione**quindi assicurarsi che la soluzione venga compilato senza errori.  
  
14. Verificare che la cartella di output di compilazione per il progetto UpgradeDeploymentStep adesso contenga il file UpgradeDeploymentStep.vsix.  
  
     Per impostazione predefinita, la cartella dell'output di compilazione è ..  \\bin\\Debug sotto la cartella che contiene il file di progetto.  
  
## Preparazione del test del passaggio di distribuzione dell'aggiornamento  
 Per testare il passaggio di distribuzione dell'aggiornamento, è necessario innanzitutto distribuire una soluzione di esempio al sito di SharePoint.  Innanzitutto, avviare il debug dell'estensione nell'istanza sperimentale di Visual Studio.  Creare una definizione e un'istanza di elenco da utilizzare per testare il passaggio di distribuzione e quindi distribuirle al sito di SharePoint.  Successivamente, modificare la definizione e l'istanza di elenco e ridistribuirle per illustrare il processo di distribuzione predefinito sovrascrive le soluzioni sul sito di SharePoint.  
  
 Più avanti in questa procedura dettagliata, verrà modificata la definizione e l'istanza di elenco e quindi le verrà migliorato mediante il sito di SharePoint.  
  
#### Per avviare il debug dell'estensione  
  
1.  Riavviare Visual Studio con credenziali amministrative e aprire la soluzione UpgradeDeploymentStep.  
  
2.  Nel progetto DeploymentStepExtension, aprire il file di codice UpgradeStep e aggiungere un punto di interruzione alla prima riga di codice nei metodi `Execute` e `CanExecute`.  
  
3.  Avviare il debug scegliendo il tasto F5 o, sulla barra dei menu, scegliente **Debug**, **Avvia debug**.  
  
4.  In Visual Studio i file di estensione vengono installati in %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ upgrade deployment step for SharePoint projects \\ 1,0 e viene avviata un'istanza sperimentale di Visual Studio.  Verificato il passaggio di distribuzione di aggiornamento in questa istanza di Visual Studio.  
  
#### Per creare progetto SharePoint con una definizione e un'istanza di elenco  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **Il file**, **Nuova**, **Project**.  
  
2.  Nella finestra di dialogo **Nuovo progetto**, espandere il nodo **Visual C\#** o il nodo **Visual Basic**, espandere il nodo **SharePoint** quindi selezionare il nodo **2010**.  
  
3.  Nella parte superiore della finestra di dialogo, verificare che **.NET Framework 3.5** venga visualizzato nell'elenco delle versioni di.NET Framework.  
  
     I progetti per [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] richiedono questa versione di .NET Framework.  
  
4.  Nell'elenco di modelli di progetto, scegliere **Progetto SharePoint 2010**, denominare il progetto **EmployeesListDefinition**quindi scegliere il pulsante **OK**.  
  
5.  In **Personalizzazione guidata SharePoint**, immettere l'url del sito che si desidera utilizzare per il debug.  
  
6.  In **Selezionare il livello di attendibilità per la soluzione SharePoint.**, scegliere il pulsante di opzione **Distribuisci come soluzione farm**.  
  
    > [!NOTE]  
    >  Il passaggio di distribuzione di aggiornamento non supporta le soluzioni create mediante sandbox.  
  
7.  Scegliere il pulsante **Fine**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il progetto EmployeesListDefinition.  
  
8.  Aprire il menu di scelta rapida del progetto EmployeesListDefinition, scegliere **Aggiungi**quindi scegliere **Nuovo elemento**.  
  
9. Nella finestra di dialogo **Aggiungi nuovo elemento \- EmployeesListDefinition**, espandere il nodo **SharePoint** quindi selezionare il nodo **2010**.  
  
10. Scegliere il modello di elemento **Elenco**, denominare l'elemento **Elenco dipendenti**quindi scegliere il pulsante **Aggiungi**.  
  
     La personalizzazione guidata SharePoint viene visualizzata  
  
11. Nella pagina **Scegli impostazioni elenco**, verificare le seguenti impostazioni e quindi scegliere il pulsante **Fine** :  
  
    1.  **Elenco dipendenti** visualizzato nella casella **Specifica il nome da visualizzare per l'elenco**.  
  
    2.  Il pulsante di opzione **Crea un elenco personalizzabile in base a:** viene scelto.  
  
    3.  **Il valore predefinito \(vuoto\)** viene scelto nell'elenco **Crea un elenco personalizzabile in base a:**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea l'elemento elenco dei dipendenti con una colonna titolo e un singolo svuota l'istanza e aprire la finestra di progettazione dell'elenco.  
  
12. Nella finestra di progettazione dell'elenco, nella scheda **Colonne**, scegliere la riga **Digitare un nome di colonna nuovo o esistente** quindi aggiungere le seguenti colonne nell'elenco **Nome visualizzato colonna** :  
  
    1.  Nome  
  
    2.  Società  
  
    3.  Telefono \(uff.\)  
  
    4.  Posta elettronica  
  
13. Salvare tutti i file e chiudere la finestra di progettazione dell'elenco.  
  
14. In **Esplora soluzioni**, espandere il nodo **Elenco dipendenti** quindi espandere il nodo figlio **Istanza di elenco dipendenti**.  
  
15. Nel file Elements.xml, sostituire il codice XML predefinito nel file con il codice XML seguente.  Questo XML modifica il nome dell'elenco a **Dipendenti** e aggiunge le informazioni per un dipendente che ha chiamato JIM Hance.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Salvare e chiudere il file Elements.xml.  
  
17. Aprire il menu di scelta rapida del progetto EmployeesListDefinition quindi scegliere **Apri** o **Proprietà**.  
  
     La finestra di progettazione proprietà viene aperto.  
  
18. Nella scheda **SharePoint**, deselezionare la casella di controllo **Ritrazione automatica dopo il debug** e salvare le proprietà.  
  
#### Per distribuire la definizione e l'istanza di elenco  
  
1.  In **Esplora soluzioni**, selezionare il nodo del progetto **EmployeesListDefinition**.  
  
2.  Nella finestra **Proprietà** assicurarsi che la proprietà **Configurazione distribuzione attiva** sia impostata su **Predefinita**.  
  
3.  Scegliere il tasto F5 o, sulla barra dei menu, scegliere **Debug**, **Avvia debug**.  
  
4.  Verificare che il progetto venga compilato correttamente, il web browser aprire al sito di SharePoint, che l'elemento **Elenchi** nella barra avvio veloce di includere il nuovo elenco **Dipendenti** e che l'elenco **Dipendenti** include la voce per JIM Hance.  
  
5.  Chiudere il browser.  
  
#### Per modificare e ridistribuire la definizione e l'istanza di elenco  
  
1.  Nel progetto EmployeesListDefinition, aprire il file Elements.xml che è un elemento figlio dell'elemento di progetto **Istanza di elenco dipendenti**.  
  
2.  Rimuovere l'elemento `Data` e i relativi figli per rimuovere la voce per Jim Hance dall'elenco.  
  
     Al termine, il file deve essere contenuto il seguente XML.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Salvare e chiudere il file Elements.xml.  
  
4.  Aprire il menu di scelta rapida per l'elemento di progetto **Elenco dipendenti** quindi scegliere **Apri** o **Proprietà**.  
  
5.  Nella finestra di progettazione dell'elenco, scegliere la scheda **Visualizzazioni**.  
  
6.  Nell'elenco **Colonne selezionate**, scegliere **Allegati**, quindi scegliere la chiave \< per spostarsi di colonna nell'elenco **Colonne disponibili**.  
  
7.  Ripetere il passaggio precedente per spostare la colonna **Telefono \(uff.\)** dall'elenco **Colonne selezionate** nell'elenco **Colonne disponibili**.  
  
     Tale azione consente di rimuovere questi campi dalla visualizzazione predefinita dell'elenco **Employees** sul sito di SharePoint.  
  
8.  Avviare il debug scegliendo il tasto F5 o, sulla barra dei menu, scegliente **Debug**, **Avvia debug**.  
  
9. Verificare che venga visualizzata la finestra di dialogo **Conflitti di distribuzione**.  
  
     Questa finestra di dialogo viene visualizzata quando Visual Studio tenta di distribuire una soluzione \(l'istanza di elenco\) a un sito di SharePoint a cui tale soluzione è già stata assegnata.  Questa finestra di dialogo non verrà visualizzata quando si esegue il passaggio di distribuzione di aggiornamento più avanti in questa procedura.  
  
10. Nella finestra di dialogo **Conflitti di distribuzione**, scegliere il pulsante di opzione **Risolvi automaticamente**.  
  
     Visual Studio consente di eliminare l'istanza di elenco sul sito di SharePoint, implementa l'elemento elenco nel progetto quindi aprire il sito di SharePoint.  
  
11. Nella sezione **Elenchi** la barra avvio veloce, scegliere l'elenco **Dipendenti** quindi verificare i seguenti informazioni:  
  
    -   Le colonne **Telefono \(ab.\)** e **Allegati** non vengono visualizzate in questa visualizzazione elenco.  
  
    -   L'elenco è vuoto.  Quando è stata utilizzata la configurazione di distribuzione **Predefinita** per ridistribuire la soluzione, l'elenco **Employees** è stato sostituito con il nuovo elenco vuoto nel progetto.  
  
## Test del passaggio di distribuzione  
 È ora possibile testare il passaggio di distribuzione dell'aggiornamento.  Innanzitutto, aggiungere un elemento all'istanza di elenco in SharePoint.  Modificare la definizione e l'istanza di elenco, migliorile sul sito di SharePoint e verificare che il passaggio di distribuzione dell'aggiornamento non sovrascriva il nuovo elemento.  
  
#### Per aggiungere manualmente un elemento all'elenco  
  
1.  Nella barra multifunzione del sito di SharePoint, nella scheda **Strumenti elenco**, scegliere la scheda **Elementi**.  
  
2.  Nel gruppo **Nuova**, scegliere **Nuovo elemento**.  
  
     In alternativa, è possibile scegliere il collegamento nell'elenco di elementi **Aggiungi nuovo elemento** stesso.  
  
3.  Nella finestra **Dipendenti – Nuovo elemento**, nella casella **Titolo**, immettere **Amministratore di funzionalità**.  
  
4.  Nella casella **Nome**, immettere **Andy**.  
  
5.  Nella casella **Società**, digitare **Contoso**.  
  
6.  Scegliere il pulsante **Salva**, verificare che il nuovo elemento venga visualizzato nell'elenco e quindi chiudere il browser.  
  
     Più avanti in questa procedura dettagliata, si utilizzerà questo elemento per verificare che il passaggio di distribuzione dell'aggiornamento non sovrascriva il contenuto di questo elenco.  
  
#### Per testare il passaggio di distribuzione dell'aggiornamento  
  
1.  Nell'istanza sperimentale di Visual Studio, in **Esplora soluzioni**, aprire il menu di scelta rapida del nodo del progetto **EmployeesListDefinition** quindi scegliere **Proprietà**.  
  
     L'editor o la finestra di progettazione delle proprietà viene aperto.  
  
2.  Nella scheda **SharePoint**, impostare la proprietà **Configurazione distribuzione attiva** a **Aggiorna**.  
  
     Questa configurazione di distribuzione personalizzata include il nuovo passaggio di distribuzione di aggiornamento.  
  
3.  Aprire il menu di scelta rapida per l'elemento di progetto **Elenco dipendenti** quindi scegliere **Proprietà** o **Apri**.  
  
     L'editor o la finestra di progettazione delle proprietà viene aperto.  
  
4.  Nella scheda **Visualizzazioni**, selezionare la colonna **Posta elettronica** quindi scegliere la chiave **\<** per spostarsi di colonna dall'elenco **Colonne selezionate** nell'elenco **Colonne disponibili**.  
  
     Tale azione consente di rimuovere questi campi dalla visualizzazione predefinita dell'elenco **Employees** sul sito di SharePoint.  
  
5.  Avviare il debug scegliendo il tasto F5 o, sulla barra dei menu, scegliente **Debug**, **Avvia debug**.  
  
6.  Verificare che il codice nell'altra istanza di Visual Studio venga interrotto nell'apposito punto impostato precedentemente nel metodo `CanExecute`.  
  
7.  Scegliere nuovamente il tasto F5 o, sulla barra dei menu, scegliere **Debug**, **Continua**.  
  
8.  Verificare che il codice si arresti nel punto di interruzione impostato precedentemente nel metodo `Execute`.  
  
9. Scegliere il tasto F5 o, sulla barra dei menu, scegliere **Debug**, **Continua** un'ora finale.  
  
     Il web browser aprire il sito di SharePoint.  
  
10. Nella sezione **Elenchi** dell'area avvio veloce, scegliere l'elenco **Dipendenti** quindi verificare i seguenti informazioni:  
  
    -   L'elemento che viene aggiunto in precedenza \(per Andy, l'amministratore di funzionalità\) è ancora nell'elenco.  
  
    -   Le colonne **Indirizzo di posta elettronica** e **Telefono \(uff.\)** non vengono visualizzate in questa visualizzazione elenco.  
  
     La configurazione di distribuzione **Aggiorna** modifica l'istanza dell'elenco **Employees** presente sul sito di SharePoint.  Se fosse stata utilizzata la configurazione di distribuzione **Predefinita** anziché la configurazione **Aggiorna**, sarebbe stato riscontrato un conflitto di distribuzione.  Visual Studio risolverebbe il conflitto sostituendo l'elenco **Dipendenti** e l'elemento per Andy, l'amministratore di funzionalità, verrebbe eliminato.  
  
## Pulizia del computer di sviluppo  
 Dopo aver completato il test del passaggio di distribuzione dell'aggiornamento, rimuovere l'istanza e la definizione di elenco dal sito di SharePoint, nonché l'estensione del passaggio di distribuzione da Visual Studio.  
  
#### Per rimuovere l'istanza di elenco dal sito di SharePoint  
  
1.  Aprire l'elenco **Dipendenti** nel sito di SharePoint, se l'elenco non è già aperto.  
  
2.  Nella barra multifunzione del sito di SharePoint, scegliere la scheda **Strumenti elenco** quindi scegliere la scheda **Elenco**.  
  
3.  Nel gruppo **Impostazioni**, selezionare l'elemento **Impostazioni elenco**.  
  
4.  In **Autorizzazioni e gestione**, scegliere il comando **Elimina l'elenco**, scegliere **OK** per confermare che si desidera spostare l'elenco nel cestino e quindi chiudere il browser.  
  
#### Per rimuovere la definizione di elenco dal sito di SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **Compilazione**, **Ritrai**.  
  
     Visual Studio ritrae la definizione di elenco dal sito di SharePoint.  
  
#### Per disinstallare l'estensione  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
     La finestra di dialogo **Estensioni e aggiornamenti** viene aperto.  
  
2.  Nell'elenco di estensioni selezionare, **Aggiorna fase di distribuzione per progetti SharePoint**quindi scegliere il comando **Disinstalla**.  
  
3.  Nella finestra di dialogo, scegliere **Sì** per confermare che si desidera disinstallare l'estensione quindi scegliere **Riavvia ora** per completare la disinstallazione.  
  
4.  Chiudere entrambe le istanze di Visual Studio \(l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione UpgradeDeploymentStep è aperta\).  
  
## Vedere anche  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  