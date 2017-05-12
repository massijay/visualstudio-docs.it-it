---
title: "Walkthrough: Creating a SharePoint Project Extension"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Walkthrough: Creating a SharePoint Project Extension
  Questa procedura dettagliata illustra come creare un'estensione per i progetti SharePoint.  È possibile utilizzare un'estensione di progetto per rispondere a eventi a livello di progetto come quando un progetto viene aggiunta, eliminazione, o viene rinominato.  È inoltre possibile aggiungere proprietà personalizzate o rispondere a un evento di modifica di un valore di proprietà.  A differenza delle estensioni di elemento di progetto, le estensioni di progetto non possono essere associate a un particolare tipo di progetto SharePoint.  Quando si crea un'estensione di progetto, questa viene caricata quando si apre in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] un qualsiasi tipo di progetto SharePoint.  
  
 In questa procedura dettagliata si creerà una proprietà booleana personalizzata che viene aggiunta a qualsiasi progetto SharePoint creato in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Quando impostata su **True**, la nuova proprietà aggiunge o associa al progetto una cartella di risorse denominata Images.  Quando impostata su **False**, la cartella Images viene rimossa, se esiste.  Per ulteriori informazioni, vedere [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'estensione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per progetti SharePoint che eseguono le operazioni seguenti:  
  
    -   Aggiunta di una proprietà di progetto personalizzata alla finestra Proprietà.  La proprietà si applica a qualsiasi progetto SharePoint.  
  
    -   Utilizzo del modello a oggetti del progetto SharePoint per aggiungere a un progetto una cartella mappata.  
  
    -   Utilizzo del modello a oggetti di automazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(DTE\) per eliminare una cartella mappata dal progetto.  
  
-   Compilazione di un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly dell'estensione della proprietà di progetto.  
  
-   Debug e test della proprietà di progetto.  
  
## Prerequisiti  
 Per completare la procedura dettagliata, nel computer di sviluppo devono essere presenti i componenti elencati di seguito:  
  
-   Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Campo [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  In questa procedura dettagliata viene utilizzato il modello **VSIX Project** di [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] per creare un pacchetto VSIX allo scopo di distribuire l'estensione della proprietà di progetto.  Per ulteriori informazioni, vedere [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## Creazione dei progetti  
 Per completare questa procedura dettagliata è necessario creare due progetti:  
  
-   Un progetto VSIX per creare il pacchetto VSIX allo scopo di distribuire l'estensione di progetto.  
  
-   Un progetto Libreria di classi che implementa l'estensione di progetto.  
  
 Iniziare la procedura dettagliata creando i progetti.  
  
#### Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Sulla barra dei menu, scegliere **Il file**, **Nuova**, **Project**.  
  
3.  Nella finestra di dialogo **Nuovo progetto**, espandere i nodi **Visual Basic** o **Visual C\#** quindi selezionare il nodo **Extensibility**.  
  
    > [!NOTE]  
    >  Questo nodo è disponibile solo se si installa Visual Studio SDK.  Per ulteriori informazioni, vedere la sezione precedente relativa ai prerequisiti.  
  
4.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di.NET Framework e quindi scegliere il modello **Progetto VSIX**.  
  
5.  Nella casella **Nome**, immettere **ProjectExtensionPackage**quindi scegliere il pulsante **OK**.  
  
     Il progetto **ProjectExtensionPackage** visualizzato in **Esplora soluzioni**.  
  
#### Per creare il progetto di estensione  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo della soluzione, scegliere **Aggiungi**quindi scegliere **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Nei progetti [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo se la casella di controllo **Mostra sempre soluzione** è selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Nella finestra di dialogo **Nuovo progetto**, espandere i nodi **Visual Basic** o **Visual C\#** quindi scegliere **Finestre**.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di.NET Framework e quindi scegliere il modello di progetto **Libreria di classi**.  
  
4.  Nella casella **Nome**, immettere **ProjectExtension**quindi scegliere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **ProjectExtension** alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## Configurazione del progetto  
 Prima di scrivere il codice per creare l'estensione di progetto, aggiungere al progetto di estensione file di codice e riferimenti all'assembly.  
  
#### Per configurare il progetto  
  
1.  Aggiungere un file di codice denominato **CustomProperty** al progetto ProjectExtension.  
  
2.  Aprire il menu di scelta rapida del progetto **ProjectExtension** quindi scegliere **Aggiungi riferimento**.  
  
3.  Nella finestra di dialogo **Gestione riferimenti – CustomProperty**, selezionare il nodo **Framework** quindi selezionare la casella di controllo accanto agli assembly System.Windows.Forms e System.ComponentModel.Composition.  
  
4.  Scegliere il nodo **Estensioni**, selezionare la casella di controllo accanto agli assembly EnvDTE e Microsoft.VisualStudio.SharePoint quindi scegliere il pulsante **OK**.  
  
5.  In **Esplora soluzioni**, nella cartella **Riferimenti** per il progetto **ProjectExtension**, scegliere **EnvDTE**.  
  
6.  Nella finestra **Proprietà**, modificare la proprietà **Incorpora tipi di interoperabilità** in **False**.  
  
## Definizione della nuova proprietà di progetto SharePoint  
 Creare una classe che definisce l'estensione di progetto e il comportamento della nuova proprietà di progetto.  Per definire la nuova estensione di progetto, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Implementare questa interfaccia ogni volta che si desidera definire un'estensione di un progetto SharePoint.  Inoltre, aggiungere l'oggetto <xref:System.ComponentModel.Composition.ExportAttribute> alla classe.  Questo attributo consente a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di individuare e caricare l'implementazione di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Passare il tipo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> al costruttore dell'attributo.  
  
#### Per definire la nuova proprietà di progetto SharePoint  
  
1.  Incollare il codice seguente nel file di codice CustomProperty.  
  
     [!code-csharp[SPExt_ProjectExtension#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_projectextension/cs/projectextension/customproperty.cs#1)]
     [!code-vb[SPExt_ProjectExtension#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_projectextension/vb/projectextension/customproperty.vb#1)]  
  
## Compilazione della soluzione  
 A questo punto occorre compilare la soluzione per garantire che non vi siano errori di compilazione.  
  
#### Per compilare la soluzione  
  
1.  Sulla barra dei menu, scegliere **Compilazione**, **Compila soluzione**.  
  
## Creazione di un pacchetto VSIX per distribuire l'estensione della proprietà di progetto  
 Per distribuire l'estensione di progetto, utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX.  Anzitutto, configurare il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto VSIX.  Successivamente, creare il pacchetto VSIX compilando la soluzione.  
  
#### Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il file source.extension.vsixmanifest quindi scegliere il pulsante **Apri**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file nella finestra di progettazione del manifesto.  Le informazioni visualizzate nella scheda **Metadati** vengono visualizzati anche in **Estensioni e aggiornamenti**. Tutti i pacchetti VSIX richiedono il file extension.vsixmanifest.  Per ulteriori informazioni su questo file, vedere [Informazioni di riferimento sullo schema dell'estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nella casella **Nome prodotto**, immettere **Proprietà di progetto personalizzata**.  
  
3.  Nella casella **Autore**, immettere **Contoso**.  
  
4.  Nella casella **Descrizione**, immettere **Una proprietà di progetto personalizzata di SharePoint che passa il mapping della cartella di risorse denominata images al progetto**.  
  
5.  Scegliere la scheda **Asset** quindi scegliere il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** visualizzato.  
  
6.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde all'elemento `MEFComponent` del file extension.vsixmanifest.  Questo elemento specifica il nome di un assembly dell'estensione nel pacchetto VSIX.  Per ulteriori informazioni, vedere [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nell'elenco **Alimentazione**, scegliere il pulsante di opzione **Progetto nella soluzione corrente**.  
  
8.  Nell'elenco **Project**, scegliere **ProjectExtension**.  
  
     Questo valore identifica il nome dell'assembly che si compila il progetto.  
  
9. Scegliere **OK** per chiudere la finestra di dialogo **Aggiungi nuovo asset**.  
  
10. Sulla barra dei menu, scegliere **Il file**, **Salva tutto** quando si completa e chiudere la finestra di progettazione del manifesto.  
  
11. Sulla barra dei menu, scegliere **Compilazione**, **Compila soluzione**quindi assicurarsi che il progetto venga compilato senza errori.  
  
12. In **Esplora soluzioni**, aprire il menu di scelta rapida del progetto **ProjectExtensionPackage** e scegliere il pulsante **Apri cartella in Esplora file**.  
  
13. In **Esplora file**, aprire la cartella di output di compilazione per il progetto ProjectExtensionPackage e verificare che la cartella contiene un file denominato ProjectExtensionPackage.vsix.  
  
     Per impostazione predefinita, la cartella dell'output di compilazione è ..  \\bin\\Debug sotto la cartella che contiene il file di progetto.  
  
## Test della proprietà di progetto  
 È ora possibile testare la proprietà di progetto personalizzata.  È più facile eseguire il debug e il test della nuova estensione di proprietà di progetto in un'istanza sperimentale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Questa istanza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene creata quando si esegue un progetto VSIX o altro progetto di estensibilità.  Dopo aver eseguito il debug del progetto, è possibile installare l'estensione nel sistema e quindi continuare a eseguire il debug e il test in un'istanza normale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Per eseguire il debug e il test dell'estensione in un'istanza sperimentale di Visual Studio  
  
1.  Riavviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative e aprire la soluzione ProjectExtensionPackage.  
  
2.  Avviare una compilazione di debug del progetto scegliendo la chiave **F5** o, sulla barra dei menu, scegliente **Debug**, **Avvia debug**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i file di estensione vengono installati in %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ project property \\ 1,0 e viene avviata un'istanza sperimentale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  Nell'istanza sperimentale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare un progetto SharePoint per una soluzione farm e utilizzare i valori predefiniti per gli altri valori nella procedura guidata.  
  
    1.  Sulla barra dei menu, scegliere **Il file**, **Nuova**, **Project**.  
  
    2.  Nella parte superiore della finestra di dialogo **Nuovo progetto**, scegliere **.NET Framework 3.5** nell'elenco delle versioni di.NET Framework.  
  
         Le estensioni degli strumenti di SharePoint richiedono alcune funzionalità di questa versione [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  Nel nodo **Modelli**, espandere il nodo **Visual Basic** o **Visual C\#**, selezionare il nodo **SharePoint** quindi selezionare il nodo **2010**.  
  
    4.  Scegliere il modello **Progetto SharePoint 2010** quindi immettere **ModuleTest** come nome del progetto.  
  
4.  In **Esplora soluzioni**, selezionare il nodo del progetto **ModuleTest**.  
  
     Una nuova proprietà personalizzata denominata **Map Images Folder** verrà visualizzata nella finestra **Proprietà** con il valore predefinito **False**.  
  
5.  Modificare il valore di questa proprietà su **True**.  
  
     Una cartella di risorse denominata Images verrà aggiunta al progetto SharePoint.  
  
6.  Modificare il valore di questa proprietà su **False**.  
  
     Se si sceglie il pulsante **Sì** nella finestra di dialogo **Eliminare la cartella Immagini?**, la cartella di risorse denominata images verrà eliminato dal progetto SharePoint.  
  
7.  Chiudere l'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## Vedere anche  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  