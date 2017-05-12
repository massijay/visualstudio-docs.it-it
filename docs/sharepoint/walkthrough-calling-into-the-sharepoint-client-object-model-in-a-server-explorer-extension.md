---
title: "Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: 100
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension
  In questa procedura dettagliata viene illustrato come chiamare il modello a oggetti del client di SharePoint da un'estensione per il nodo **Connessioni di SharePoint** in **Esplora server**.  Per ulteriori informazioni su come utilizzare il modello a oggetti del client di SharePoint, vedere [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'estensione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] che estende il nodo **Connessioni di SharePoint** di **Esplora server** nei modi seguenti:  
  
    -   L'estensione aggiunge un nodo **Raccolta web part** sotto ogni nodo del sito di SharePoint in **Esplora server**.  In questo nuovo nodo sono contenuti nodi figlio che rappresentano ogni web part nella relativa raccolta sul sito.  
  
    -   L'estensione definisce un nuovo tipo di nodo che rappresenta un'istanza di Web part.  Questo nuovo tipo di nodo è la base dei nodi figlio sotto il nuovo nodo **Raccolta web part**.  Il nuovo tipo di nodo di Web part visualizza le informazioni nella finestra **Proprietà** sul Web part che il nodo.  
  
-   Compilazione di un pacchetto Visual Studio Extension \(VSIX\) per distribuire l'estensione.  
  
-   Debug e test dell'estensione.  
  
> [!NOTE]  
>  L'estensione che si crea in questa procedura dettagliata assomiglia all'estensione che si crea in [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  Nella procedura dettagliata utilizza il modello a oggetti del server SharePoint, ma questa procedura dettagliata eseguire le stesse attività tramite il modello a oggetti del client.  
  
## Prerequisiti  
 Per completare la procedura dettagliata, nel computer di sviluppo devono essere presenti i componenti elencati di seguito:  
  
-   Edizioni supportate di Windows, SharePoint e Visual Studio.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK.  In questa procedura dettagliata viene utilizzato il modello **VSIX Project** di SDK per creare un pacchetto VSIX e distribuire l'estensione.  Per ulteriori informazioni, vedere [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Per completare la procedura dettagliata è consigliabile conoscere i concetti riportati di seguito:  
  
-   Utilizzo del modello a oggetti del client di SharePoint.  Per ulteriori informazioni, vedere l'articolo relativo al [modello a oggetti del client gestito](http://go.microsoft.com/fwlink/?LinkId=177797) \(la pagina potrebbe essere in inglese\).  
  
-   Web part in SharePoint.  Per ulteriori informazioni, vedere l'articolo relativo alla [panoramica delle web part](http://go.microsoft.com/fwlink/?LinkId=177803) \(la pagina potrebbe essere in inglese\).  
  
## Creazione dei progetti  
 Per completare questa procedura dettagliata è necessario creare due progetti:  
  
-   Un progetto vsix per creare il pacchetto VSIX per distribuire l'estensione **Esplora server**.  
  
-   Un progetto libreria di classi che implementa l'estensione **Esplora server**.  
  
 Iniziare la procedura dettagliata creando i progetti.  
  
#### Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Sulla barra dei menu, scegliere **Il file**, **Nuova**, **Project**.  
  
3.  Nella finestra di dialogo **Nuovo progetto**, espandere i nodi **Visual Basic** o **Visual C\#** quindi scegliere **Extensibility**.  
  
    > [!NOTE]  
    >  Il nodo **Extensibility** è disponibile solo se si installa Visual Studio SDK.  Per ulteriori informazioni, vedere la sezione precedente relativa ai prerequisiti.  
  
4.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di.NET Framework.  
  
     Le estensioni degli strumenti di SharePoint richiedono alcune funzionalità di questa versione di .NET Framework.  
  
5.  Scegliere il modello **Progetto VSIX**.  
  
6.  Nella casella **Nome**, il tipo **WebPartNode**quindi selezionare il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **WebPartNode** a **Esplora soluzioni**.  
  
#### Per creare il progetto di estensione  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo della soluzione, scegliere **Aggiungi**quindi scegliere **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo quando la casella di controllo **Mostra sempre soluzione** viene selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Nella finestra di dialogo  **Nuovo progetto**, espandere i nodi **Visual Basic** o **Visual C\#** quindi scegliere **Finestre**.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di.NET Framework.  
  
4.  Nell'elenco di modelli di progetto, scegliere **Libreria di classi**.  
  
5.  Nella casella **Nome**, immettere **WebPartNodeExtension**quindi scegliere il pulsante **OK**.  
  
     In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il progetto **WebPartNodeExtension** viene aggiunto alla soluzione e viene aperto il file di codice predefinito Class1.  
  
6.  Eliminare il file di codice Class1 dal progetto.  
  
## Configurazione del progetto di estensione  
 Prima di scrivere codice per creare l'estensione, è necessario aggiungere file di codice e riferimenti al progetto e aggiornare lo spazio dei nomi predefinito.  
  
#### Per configurare il progetto  
  
1.  Nel progetto **WebPartNodeExtension**, aggiungere due file di codice denominato SiteNodeExtension e WebPartNodeTypeProvider.  
  
2.  Aprire il menu di scelta rapida del progetto WebPartNodeExtension quindi scegliere **Aggiungi riferimento**.  
  
3.  Nella finestra di dialogo **Gestione riferimenti – WebPartNodeExtension**, selezionare il nodo **Framework** quindi selezionare le caselle di controllo per gli assembly System.Windows.Forms e System.ComponentModel.Composition.  
  
4.  Scegliere il nodo **Estensioni**, selezionare la casella di controllo per ognuno degli assembly e quindi scegliere il pulsante **OK** :  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Aprire il menu di scelta rapida del progetto **WebPartNodeExtension** quindi scegliere **Proprietà**.  
  
     Verrà aperta la finestra **Progettazione progetti**.  
  
6.  Scegliere la scheda **Application**.  
  
7.  Nella casella **Spazio dei nomi predefinito** \(C\#\) o casella **Spazio dei nomi radice** \(Visual Basic\), immettere **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## Creazione di icone per i nuovi nodi  
 Creare due icone per l'estensione **Esplora server** : un'icona per il nuovo nodo **Raccolta web part** e un'altra per ogni nodo figlio di Web part nel nodo **Raccolta web part**.  Più avanti in questa procedura, è necessario scrivere il codice che associa queste icone ai nodi.  
  
#### Per creare icone per i nodi  
  
1.  In **Progettazione progetti** per il progetto WebPartNodeExtension, scegliere la scheda **Risorse**.  
  
2.  Scegliere il collegamento **Il progetto non contiene un file di risorse predefinito. Fare clic qui per crearlo.**  
  
     In Visual Studio viene creato un file di risorse che viene aperto nella finestra di progettazione.  
  
3.  Nella parte superiore della finestra di progettazione, scegliere la freccia nel comando del menu **Aggiungi risorsa** quindi scegliere **Aggiungi nuova icona**.  
  
4.  Immettere **WebPartsNode** per il nuovo nome dell'icona e scegliere il pulsante **Aggiungi**.  
  
     La nuova icona viene aperta in **Editor immagini**.  
  
5.  Modificare la versione 16x16 dell'icona in modo che la relativa progettazione sia facilmente riconoscibile.  
  
6.  Aprire il menu di scelta rapida per la versione 32x32 dell'icona e scegliere **Elimina tipo di immagine**.  
  
7.  Ripetere i passaggi da 3 a 7 per aggiungere una seconda icona alle risorse del progetto e denominare questa icona **Web part**.  
  
8.  In **Esplora soluzioni**, nella cartella **Risorse** per il progetto **WebPartNodeExtension**, scegliere **WebPartsNode.ico**.  
  
9. Nella finestra **Proprietà**, aprire l'elenco **Operazione di compilazione** quindi scegliere **Risorsa incorporata**.  
  
10. Ripetere gli ultimi due passaggi per **WebPart.ico**.  
  
## Aggiunta del nodo Raccolta web part a Esplora server  
 Creare una classe che aggiunge il nuovo nodo **Raccolta web part** a ogni nodo del sito di SharePoint.  Per aggiungere il nuovo nodo, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Implementare questa interfaccia tutte le volte che si desidera estendere il comportamento di un nodo esistente in **Esplora server**, ad esempio aggiungendo un nuovo nodo figlio a un nodo.  
  
#### Per aggiungere il nodo Raccolta web part a Esplora server  
  
1.  Incollare il codice seguente nel file di codice **SiteNodeExtension** per il progetto **WebPartNodeExtension**.  
  
    > [!NOTE]  
    >  Dopo aver aggiunto questo codice, il progetto presenterà alcuni errori di compilazione.  che scompariranno quando si aggiunge codice nei passaggi successivi.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Definizione di un tipo di nodo che rappresenta una web part  
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una web part.  Visual Studio utilizza questo nuovo tipo di nodo per visualizzare i nodi figlio sotto il nodo **Raccolta web part**.  Ognuno di questi nodi figlio rappresenta una singola web part sul sito di SharePoint.  
  
 Per definire il nuovo tipo di nodo, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Implementare questa interfaccia tutte le volte che si desidera definire un nuovo tipo di nodo in **Esplora server**.  
  
#### Per definire il tipo di nodo di web part  
  
1.  Incollare il codice seguente nel file di codice **WebPartNodeTypeProvider** per il progetto **WebPartNodeExtension**.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Verifica  
 In questa fase della procedura dettagliata, tutto il codice per il nodo **Raccolta web part** si trova nel progetto.  Compilare il progetto **WebPartNodeExtension** assicurarsi che venga compilato senza errori.  
  
#### Per compilare il progetto  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del progetto **WebPartNodeExtension** quindi scegliere **Compilazione**.  
  
## Creazione di un pacchetto VSIX per distribuire l'estensione  
 Per distribuire l'estensione, utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX.  Innanzitutto, configurare il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto.  Successivamente creare il pacchetto VSIX compilando la soluzione.  
  
#### Per configurare il pacchetto VSIX  
  
1.  In **Esplora soluzioni**, nel progetto **WebPartNode**, aprire un file **source.extension.vsixmanifest** nell'editor del manifesto.  
  
     Il file source.extension.vsixmanifest è la base del file extension.vsixmanifest che tutti i pacchetti VSIX richiedono.  Per ulteriori informazioni su questo file, vedere [Informazioni di riferimento sullo schema dell'estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nella casella **Nome prodotto**, immettere **Nodo raccolta web part per Esplora server**.  
  
3.  Nella casella **Autore**, immettere **Contoso**.  
  
4.  Nella casella **Descrizione**, immettere **Aggiungere un nodo personalizzato della raccolta Web part al nodo Connessioni di SharePoint in Esplora server**.  
  
5.  Nella scheda **Asset** dell'editor, scegliere il pulsante **Nuova**.  
  
6.  Nella finestra di dialogo **Aggiungi nuovo asset**, nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde all'elemento `MefComponent` del file extension.vsixmanifest.  Questo elemento specifica il nome di un assembly dell'estensione nel pacchetto VSIX.  Per ulteriori informazioni, vedere [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nell'elenco **Alimentazione**, scegliere **Progetto nella soluzione corrente**.  
  
8.  Nell'elenco **Project**, scegliere **WebPartNodeExtension**quindi scegliere il pulsante **OK**.  
  
9. Sulla barra dei menu, scegliere **Compilazione**, **Compila soluzione**quindi assicurarsi che la soluzione venga compilato senza errori.  
  
10. Verificare che la cartella di output di compilazione per il progetto WebPartNode adesso contenga il file WebPartNode.vsix.  
  
     Per impostazione predefinita, la cartella dell'output di compilazione è ..  \\bin\\Debug sotto la cartella che contiene il file di progetto.  
  
## Test dell'estensione  
 Ora è possibile testare il nuovo nodo **Raccolta web part** in **Esplora server**.  Innanzitutto, avviare il debug del progetto di estensione in un'istanza sperimentale di Visual Studio.  Utilizzare quindi il nuovo nodo **Web part** l'istanza sperimentale di Visual Studio.  
  
#### Per avviare il debug dell'estensione  
  
1.  Riavviare Visual Studio con credenziali amministrative e aprire la soluzione **WebPartNode**.  
  
2.  Nel progetto WebPartNodeExtension, aprire il file di codice **SiteNodeExtension** e aggiungere un punto di interruzione alle prime righe di codice nei metodi `CreateWebPartNodes` e `NodeChildrenRequested`.  
  
3.  Scegliere il tasto F5 per avviare il debug.  
  
     In Visual Studio i file di estensione vengono installati in %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ estensione del nodo raccolta Web part a Esplora server \\ 1,0 e viene avviata un'istanza sperimentale di Visual Studio.  L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### Per testare l'estensione  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **Visualizza**, **Esplora server**.  
  
2.  Verificare che il sito di SharePoint che si desidera utilizzare per il test venga visualizzato sotto il nodo **Connessioni di SharePoint** in **Esplora server**.  Se non è elencato, seguire questi passaggi:  
  
    1.  Aprire il menu di scelta rapida per **Connessioni di SharePoint**quindi scegliere **Aggiungi connessione**.  
  
    2.  Nella finestra di dialogo **Aggiungi connessione SharePoint**, immettere l'url per il sito di SharePoint a cui si desidera connettersi e quindi scegliere il pulsante **OK**.  
  
         Per specificare il sito di SharePoint nel computer di sviluppo, digitare **http:\/\/localhost**.  
  
3.  Espandere il nodo della connessione al sito \(in cui è visualizzato l'url del sito\) e quindi espandere il nodo del sito figlio \(ad esempio, **Sito team**\).  
  
4.  Verificare che il codice nell'altra istanza di Visual Studio si interrompe al punto di interruzione impostato precedentemente nel metodo `NodeChildrenRequested` quindi scegliere il tasto F5 per continuare a eseguire il debug del progetto.  
  
5.  Nell'istanza sperimentale di Visual Studio, espandere il nodo **Raccolta web part**, visualizzato sotto il nodo del sito principale.  
  
6.  Verificare che il codice nell'altra istanza di Visual Studio si interrompe al punto di interruzione impostato precedentemente nel metodo `CreateWebPartNodes` quindi scegliere il tasto F5 per continuare a eseguire il debug del progetto.  
  
7.  Nell'istanza sperimentale di Visual Studio verificare che tutte le web part sul sito connesso vengano visualizzate nel nodo **Raccolta web part** in **Esplora server**.  
  
8.  Aprire il menu di scelta rapida per una Web part e quindi scegliere **Proprietà**.  
  
9. Nella finestra **Proprietà**, verificare che i dettagli relativi alla Web part vengano visualizzati.  
  
10. In **Esplora server**, aprire il menu di scelta rapida per lo stesso Web part e quindi scegliere **Avviso visivo**.  
  
     Nella finestra di messaggio visualizzata, scegliere il pulsante **OK**.  
  
## Disinstallazione dell'estensione da Visual Studio  
 Dopo aver completato il test dell'estensione, disinstallila da Visual Studio.  
  
#### Per disinstallare l'estensione  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
     La finestra di dialogo **Estensioni e aggiornamenti** viene aperto.  
  
2.  Nell'elenco di estensioni selezionare, **Nodo raccolta web part per Esplora server**quindi scegliere il pulsante **Disinstalla**.  
  
3.  Nella finestra di dialogo, scegliere il pulsante **Sì**.  
  
4.  Scegliere il pulsante **Riavvia ora** per completare la disinstallazione.  
  
     Viene disinstallato anche l'elemento di progetto.  
  
5.  Chiudere entrambe le istanze di Visual Studio \(l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione WebPartNode è aperta\).  
  
## Vedere anche  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  