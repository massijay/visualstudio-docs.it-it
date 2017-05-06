---
title: "Walkthrough: Extending Server Explorer to Display Web Parts"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Walkthrough: Extending Server Explorer to Display Web Parts
  In Visual Studio, è possibile utilizzare il nodo **Connessioni di SharePointEsplora server** per visualizzare i componenti dei siti di SharePoint.  Tuttavia, **Esplora server** non vengono visualizzati alcuni componenti per impostazione predefinita.  In questa procedura dettagliata, estese **Esplora server** in modo da visualizzare la raccolta Web part in ogni sito di SharePoint connesso.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che estende **Esplora server** nei modi seguenti:  
  
    -   L'estensione aggiunge un nodo **Raccolta web part** sotto ogni nodo del sito di SharePoint in **Esplora server**.  In questo nuovo nodo sono contenuti nodi figlio che rappresentano ogni web part nella relativa raccolta sul sito.  
  
    -   L'estensione definisce un nuovo tipo di nodo che rappresenta un'istanza di Web part.  Questo nuovo tipo di nodo è la base dei nodi figlio sotto il nuovo nodo **Raccolta web part**.  Il nuovo tipo di nodo di web part visualizza le informazioni nella finestra **Proprietà** relativa alla web part che rappresenta.  Il tipo di nodo include anche un elemento di menu di scelta rapida personalizzato che è possibile utilizzare come punto iniziale per eseguire altre attività correlate alla Web part.  
  
-   Creazione di due comandi di SharePoint personalizzati che l'assembly di estensioni chiama.  I comandi di SharePoint sono metodi che possono essere chiamati dagli assembly di estensioni per utilizzare le API nel modello a oggetti del server di SharePoint.  In questa procedura dettagliata verranno creati comandi per recuperare informazioni sulla web part dal sito locale di SharePoint nel computer di sviluppo.  Per ulteriori informazioni, vedere [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Compilazione di un pacchetto Visual Studio Extension \(VSIX\) per distribuire l'estensione.  
  
-   Debug e test dell'estensione.  
  
> [!NOTE]  
>  Per una versione alternativa di questa procedura dettagliata che utilizza il modello a oggetti del client di SharePoint anziché il modello a oggetti del server, vedere [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, nel computer di sviluppo devono essere presenti i componenti elencati di seguito:  
  
-   Edizioni supportate di Windows, SharePoint e Visual Studio.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK.  In questa procedura dettagliata viene utilizzato il modello **VSIX Project** di SDK per creare un pacchetto VSIX e distribuire l'elemento di progetto.  Per ulteriori informazioni, vedere [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Per completare la procedura dettagliata è consigliabile conoscere i concetti riportati di seguito:  
  
-   Utilizzo del modello a oggetti del server di SharePoint.  Per ulteriori informazioni, vedere l'articolo relativo all'[utilizzo del modello a oggetti lato server di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796) \(la pagina potrebbe essere in inglese\).  
  
-   Web part nelle soluzioni SharePoint.  Per ulteriori informazioni, vedere l'articolo relativo alla [panoramica delle web part](http://go.microsoft.com/fwlink/?LinkId=177803) \(la pagina potrebbe essere in inglese\).  
  
## Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario creare tre progetti:  
  
-   Un progetto VSIX per creare il pacchetto VSIX allo scopo di distribuire l'estensione.  
  
-   Un progetto Libreria di classi che implementa l'estensione.  Questo progetto deve essere destinato a .NET Framework 4,5.  
  
-   Un progetto Libreria di classi che definisce i comandi di SharePoint personalizzati.  Questo progetto deve essere destinato a .NET Framework 3.5.  
  
 Iniziare la procedura dettagliata creando i progetti.  
  
#### Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Sulla barra dei menu, scegliere **Il file**, **Nuova**, **Project**.  
  
3.  Nella finestra di dialogo  **Nuovo progetto**, espandere i nodi **Visual Basic** o **Visual C\#** quindi selezionare il nodo **Extensibility**.  
  
    > [!NOTE]  
    >  Il nodo **Extensibility** è disponibile solo se si installa Visual Studio SDK.  Per ulteriori informazioni, vedere la sezione precedente relativa ai prerequisiti.  
  
4.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di.NET Framework.  
  
5.  Scegliere il modello **Progetto VSIX**, denominare il progetto **WebPartNode**quindi scegliere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **WebPartNode** a **Esplora soluzioni**.  
  
#### Per creare il progetto di estensione  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo della soluzione, scegliere **Aggiungi**quindi scegliere **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo quando la casella di controllo **Mostra sempre soluzione** viene selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Nella finestra di dialogo **Nuovo progetto**, espandere il nodo **Visual C\#** o il nodo **Visual Basic** quindi il nodo **Finestre** di scelta.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di.NET Framework.  
  
4.  Nell'elenco di modelli di progetto, scegliere **Libreria di classi**, denominare il progetto **WebPartNodeExtension**quindi scegliere il pulsante **OK**.  
  
     In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il progetto **WebPartNodeExtension** viene aggiunto alla soluzione e viene aperto il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
#### Per creare il progetto di comandi di SharePoint  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo della soluzione, scegliere **Aggiungi**quindi scegliere **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo quando la casella di controllo **Mostra sempre soluzione** viene selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Nella finestra di dialogo  **Nuovo progetto**, espandere il nodo **Visual C\#** o il nodo **Visual Basic** quindi selezionare il nodo **Finestre**.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 3.5** nell'elenco delle versioni di.NET Framework.  
  
4.  Nell'elenco di modelli di progetto, scegliere **Libreria di classi**, denominare il progetto **WebPartCommands**quindi scegliere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **WebPartCommands** alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## Configurazione dei progetti  
 Prima di scrivere codice per creare l'estensione, è necessario aggiungere file di codice e i riferimenti ad assembly e configurare le impostazioni del progetto.  
  
#### Per configurare il progetto WebPartNodeExtension  
  
1.  Nel progetto WebPartNodeExtension, aggiungere quattro file di codice con i nomi seguenti:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Aprire il menu di scelta rapida del progetto **WebPartNodeExtension** quindi scegliere **Aggiungi riferimento**.  
  
3.  Nella finestra di dialogo **Gestione riferimenti – WebPartNodeExtension**, scegliere la scheda **Framework** quindi selezionare la casella di controllo per ognuno degli assembly seguenti:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Scegliere la scheda **Estensioni**, selezionare la casella di controllo per un assembly Microsoft.VisualStudio.SharePoint quindi scegliere il pulsante **OK**.  
  
5.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo del progetto **WebPartNodeExtension** quindi scegliere **Proprietà**.  
  
     Verrà aperta la finestra **Progettazione progetti**.  
  
6.  Scegliere la scheda **Application**.  
  
7.  Nella casella **Spazio dei nomi predefinito** \(C\#\) o casella **Spazio dei nomi radice** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), immettere **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### Per configurare il progetto WebPartCommands  
  
1.  Nel progetto WebPartCommands, aggiungere un file di codice denominato WebPartCommands.  
  
2.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo del progetto **WebPartCommands**, scegliere **Aggiungi**quindi scegliere **Elemento esistente**.  
  
3.  Nella finestra di dialogo **Aggiungi elemento esistente**, individuare la cartella che contiene file di codice per il progetto WebPartNodeExtension quindi i file di codice WebPartNodeInfo e WebPartCommandIds.  
  
4.  Scegliere la freccia accanto al pulsante **Aggiungi** quindi scegliere **Aggiungi come collegamento** dal menu visualizzato.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge i file di codice al progetto WebPartCommands come collegamenti.  Di conseguenza, i file di codice si trovano nel progetto WebPartNodeExtension, ma il codice nei file è compilato anche nel progetto WebPartCommands.  
  
5.  Aprire nuovamente il menu di scelta rapida del progetto **WebPartCommands** e scegliere **Aggiungi riferimento**.  
  
6.  Nella finestra di dialogo **Gestione riferimenti – WebPartCommands**, scegliere la scheda **Estensioni**, selezionare la casella di controllo per ognuno degli assembly e quindi scegliere il pulsante **OK** :  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  In **Esplora soluzioni**, aprire nuovamente il menu di scelta rapida del progetto **WebPartCommands** quindi scegliere **Proprietà**.  
  
     Verrà aperta la finestra **Progettazione progetti**.  
  
8.  Scegliere la scheda di **Application**.  
  
9. Nella casella **Spazio dei nomi predefinito** \(C\#\) o casella **Spazio dei nomi radice** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), immettere **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## Creazione di icone per i nuovi nodi  
 Creare due icone per l'estensione **Esplora server**: una per il nuovo nodo **Raccolta web part** e un'altra per ogni nodo di web part figlio presente sotto il nodo **Raccolta web part**.  Più avanti nella procedura dettagliata si scriverà codice che associa queste icone ai nodi.  
  
#### Per creare icone per i nodi  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del progetto **WebPartNodeExtension** quindi scegliere **Proprietà**.  
  
2.  Verrà aperta la finestra **Progettazione progetti**.  
  
3.  Scegliere la scheda **Risorse** e quindi scegliere **Questo progetto non contiene un file di risorse predefinito. Fare clic qui per creare un** collegamento.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea un file di risorse che viene aperto nella finestra di progettazione.  
  
4.  Nella parte superiore della finestra di progettazione, scegliere la freccia accanto al comando di menu **Aggiungi risorsa** quindi scegliere **Aggiungi nuova icona** dal menu visualizzato.  
  
5.  Nella finestra di dialogo **Aggiungi nuova risorsa**, denominare la nuova icona **WebPartsNode**quindi scegliere il pulsante **Aggiungi**.  
  
     La nuova icona viene aperta in **Editor immagini**.  
  
6.  Modificare la versione 16x16 dell'icona in modo che la relativa progettazione sia facilmente riconoscibile.  
  
7.  Aprire il menu di scelta rapida per la versione 32x32 dell'icona e scegliere **Elimina tipo di immagine**.  
  
8.  Ripetere i passaggi da 5 a 8 per aggiungere una seconda icona alle risorse del progetto e denominare questa icona **Web part**.  
  
9. In **Esplora soluzioni**, nella cartella **Risorse** per il progetto **WebPartNodeExtension**, aprire il menu di scelta rapida per **WebPartsNode.ico**.  
  
10. Nella finestra **Proprietà**, scegliere la freccia accanto a **Operazione di compilazione**quindi scegliere **Risorsa incorporata** nel menu visualizzato.  
  
11. Ripetere gli ultimi due passaggi per **WebPart.ico**.  
  
## Aggiunta del nodo Raccolta web part a Esplora server  
 Creare una classe che aggiunge il nuovo nodo **Raccolta web part** a ogni nodo del sito di SharePoint.  Per aggiungere il nuovo nodo, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Implementare questa interfaccia tutte le volte che si desidera estendere il comportamento di un nodo esistente in **Esplora server**, ad esempio aggiungendo il nodo figlio a un nodo.  
  
#### Per aggiungere il nodo Raccolta web part a Esplora server  
  
1.  Nel progetto WebPartNodeExtension, aprire il file di codice SiteNodeExtension e quindi incollare il codice seguente in.  
  
    > [!NOTE]  
    >  Dopo aver aggiunto questo codice, il progetto presenterà alcuni errori di compilazione, ma verranno risolti quando si aggiunge codice nei passaggi successivi.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Definizione di un tipo di nodo che rappresenta una web part  
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una web part.  Visual Studio utilizza questo nuovo tipo di nodo per visualizzare i nodi figlio sotto il nodo **Raccolta web part**.  Ogni nodo figlio rappresenta una singola Web part sul sito di SharePoint.  
  
 Per definire il nuovo tipo di nodo, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Implementare questa interfaccia tutte le volte che si desidera definire un nuovo tipo di nodo in **Esplora server**.  
  
#### Per definire il tipo di nodo di web part  
  
1.  Nel progetto WebPartNodeExtension, aprire il file di codice Webpartnodetypeprovider quindi incollare il codice seguente in.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Definizione della classe di dati della web part  
 Definire una classe che contiene i dati relativi a una singola web part sul sito di SharePoint.  Più avanti in questa procedura dettagliata, verrà creato un comando di SharePoint personalizzato che recupera i dati di ogni Web part sul sito e li assegna alle istanze di questa classe.  
  
#### Per definire la classe di dati della web part  
  
1.  Nel progetto WebPartNodeExtension, aprire il file di codice WebPartNodeInfo e quindi incollare il codice seguente in.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodeinfo.cs#3)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodeinfo.vb#3)]  
  
## Definizione degli ID per i comandi di SharePoint  
 Definire diverse stringhe che identificano i comandi personalizzati di SharePoint  che verranno implementati più avanti nella procedura dettagliata.  
  
#### Per definire gli ID dei comandi  
  
1.  Nel progetto WebPartNodeExtension, aprire il file di codice WebPartCommandIds quindi incollare il codice seguente in.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartcommandids.vb#4)]  
  
## Creazione di comandi personalizzati di SharePoint  
 Creare controlli personalizzati che effettuano chiamate nel modello a oggetti del server di SharePoint per recuperare i dati relativi alle Web part sul sito di SharePoint.  Ogni comando è un metodo che dispone di un oggetto <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> applicato.  
  
#### Per definire i comandi di SharePoint  
  
1.  Nel progetto WebPartCommands, aprire il file di codice WebPartCommands quindi incollare il codice seguente in.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartcommands/webpartcommands.vb#6)]  
  
## Verifica  
 In questa fase della procedura dettagliata, tutto il codice per il nodo **Raccolta web part** e i comandi di SharePoint si trovano nei progetti.  Compilare la soluzione per assicurarsi che entrambi i progetti vengano compilati senza errori.  
  
#### Per compilare la soluzione  
  
1.  Sulla barra dei menu, scegliere **Compilazione**, **Compila soluzione**.  
  
    > [!WARNING]  
    >  In questa fase, il progetto WebPartNode può avere un errore di compilazione dal file manifesto VSIX non dispone di un valore dell'autore.  L'errore andrà tramite quando si aggiunge un valore nei passaggi successivi.  
  
## Creazione di un pacchetto VSIX per distribuire l'estensione  
 Per distribuire l'estensione, utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX.  Innanzitutto, configurare il pacchetto VSIX modificando il file source.extension.vsixmanifest nel progetto VSIX.  Successivamente, creare il pacchetto VSIX compilando la soluzione.  
  
#### Per configurare il pacchetto VSIX  
  
1.  In **Esplora soluzioni**, doppio clic sul file, aprire il file **source.extension.vsixmanifest** nell'editor del manifesto.  
  
     Il file source.extension.vsixmanifest è la base del file extension.vsixmanifest che tutti i pacchetti VSIX richiedono.  Per ulteriori informazioni su questo file, vedere [Informazioni di riferimento sullo schema dell'estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nella casella **Nome prodotto**, immettere **Nodo raccolta web part per Esplora server**.  
  
3.  Nella casella **Autore**, immettere **Contoso**.  
  
4.  Nella casella **Descrizione**, immettere **Aggiungere un nodo personalizzato della raccolta Web part al nodo Connessioni di SharePoint in Esplora server. This extension uses a custom SharePoint command to call into the server object model.**  
  
5.  Scegliere la scheda **Asset** dell'editor e quindi scegliere il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** visualizzato.  
  
6.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde all'elemento `MefComponent` del file extension.vsixmanifest.  Questo elemento specifica il nome di un assembly dell'estensione nel pacchetto VSIX.  Per ulteriori informazioni, vedere [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nell'elenco **Alimentazione**, scegliere **Progetto nella soluzione corrente**.  
  
8.  Nell'elenco **Project**, scegliere **WebPartNodeExtension** quindi scegliere il pulsante **OK**.  
  
9. Nell'editor del manifesto, scegliere nuovamente il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** visualizzato.  
  
10. Nella casella **Tipo**, immettere **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Questo elemento specifica un'estensione personalizzata che si desidera includere nell'estensione di Visual Studio.  Per ulteriori informazioni, vedere [Elemento di risorsa \(schema VSX\)](http://msdn.microsoft.com/it-it/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. Nell'elenco **Alimentazione**, selezionare la voce di elenco **Progetto nella soluzione corrente**.  
  
12. Nell'elenco **Project**, scegliere **WebPartCommands**quindi scegliere il pulsante **OK**.  
  
13. Sulla barra dei menu, scegliere **Compilazione**, **Compila soluzione**quindi assicurarsi che la soluzione venga compilato senza errori.  
  
14. Verificare che la cartella di output di compilazione per il progetto WebPartNode adesso contenga il file WebPartNode.vsix.  
  
     Per impostazione predefinita, la cartella dell'output di compilazione è ..  \\bin\\Debug sotto la cartella che contiene il file di progetto.  
  
## Test dell'estensione  
 È ora possibile testare il nuovo nodo **Raccolta web part** in **Esplora server**.  Innanzitutto, avviare il debug dell'estensione in un'istanza sperimentale di Visual Studio.  Successivamente, utilizzare il nuovo nodo **Web part** nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Per avviare il debug dell'estensione  
  
1.  Riavviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative e aprire la soluzione WebPartNode.  
  
2.  Nel progetto WebPartNodeExtension, aprire il file di codice SiteNodeExtension e aggiungere un punto di interruzione alla prima riga di codice nei metodi `CreateWebPartNodes` e `NodeChildrenRequested`.  
  
3.  Scegliere il tasto F5 per avviare il debug.  
  
     In Visual Studio i file di estensione vengono installati in %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ estensione del nodo raccolta Web part a Esplora server \\ 1,0 e viene avviata un'istanza sperimentale di Visual Studio.  L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### Per testare l'estensione  
  
1.  Nell'istanza sperimentale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sulla barra dei menu, scegliere **Visualizza**, **Esplora server**.  
  
2.  Eseguire i passaggi seguenti se il sito di SharePoint che si desidera utilizzare per il test non viene visualizzato nel nodo **Connessioni di SharePoint** in **Esplora server**:  
  
    1.  In **Esplora server**, aprire il menu di scelta rapida per **Connessioni di SharePoint**quindi scegliere **Aggiungi connessione**.  
  
    2.  Nella finestra di dialogo **Aggiungi connessione SharePoint**, immettere l'url per il sito di SharePoint a cui si desidera connettersi e quindi scegliere il pulsante **OK**.  
  
         Per specificare il sito di SharePoint nel computer di sviluppo, immettere **http:\/\/localhost**.  
  
3.  Espandere il nodo della connessione al sito \(in cui è visualizzato l'url del sito\) e quindi espandere il nodo del sito figlio \(ad esempio, **Sito team**\).  
  
4.  Verificare che il codice nell'altra istanza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] si interrompe al punto di interruzione impostato precedentemente nel metodo `NodeChildrenRequested` quindi si sceglie F5 per continuare a eseguire il debug del progetto.  
  
5.  Nell'istanza sperimentale di Visual Studio, verificare che un nuovo nodo denominato **Raccolta web part** sotto il nodo del sito principale e quindi espandere il nodo **Raccolta web part**.  
  
6.  Verificare che il codice nell'altra istanza di Visual Studio si interrompe al punto di interruzione impostato precedentemente nel metodo `CreateWebPartNodes` quindi scegliere il tasto F5 per continuare a eseguire il debug del progetto.  
  
7.  Nell'istanza sperimentale di Visual Studio, verificare che tutte le Web part sul sito connesso vengano visualizzati nel nodo **Raccolta web part** in **Esplora server**.  
  
8.  In **Esplora server**, aprire il menu di scelta rapida per una Web part e quindi scegliere **Proprietà**.  
  
9. Nell'istanza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] che si sta eseguendo il debug, verificare che i dettagli relativi alla Web part vengano visualizzati nella finestra **Proprietà**.  
  
## Disinstallazione dell'estensione da Visual Studio  
 Dopo aver completato il test dell'estensione, disinstallare quest'ultima da Visual Studio.  
  
#### Per disinstallare l'estensione  
  
1.  Nell'istanza sperimentale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sulla barra dei menu, scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
     La finestra di dialogo **Estensioni e aggiornamenti** viene aperto.  
  
2.  Nell'elenco di estensioni selezionare, **Estensione nodo raccolta web part per Esplora server**quindi scegliere il pulsante **Disinstalla**.  
  
3.  Nella finestra di dialogo, scegliere il pulsante **Sì** per confermare che si desidera disinstallare l'estensione e quindi scegliere il pulsante **Riavvia ora** per completare la disinstallazione.  
  
4.  Chiudere entrambe le istanze di Visual Studio \(l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione WebPartNode è aperta\).  
  
## Vedere anche  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  