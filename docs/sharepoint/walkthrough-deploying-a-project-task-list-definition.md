---
title: "Procedura dettagliata: distribuzione di una definizione di elenco attivit&#224; del progetto | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, distribuzione"
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Procedura dettagliata: distribuzione di una definizione di elenco attivit&#224; del progetto
  Questa procedura guidata mostra come utilizzare [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] per creare, personalizzare, sottoporre a debug e distribuire un elenco di SharePoint al fine di tenere traccia delle attività del progetto.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   [Creazione di un elenco di SharePoint](#CreatingListDef).  
  
-   [Creazione di un elenco di SharePoint](#CreatingListDef).  
  
-   [Aggiunta di un ricevitore di eventi](#AddEventRcvr).  
  
-   [Personalizzazione della funzionalità dell'elenco attività del progetto](#CustomizeFeature).  
  
-   [Compilazione e test dell'elenco attività del progetto](#BuildTest).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] o un'edizione di Visual Studio Application Lifecycle Management \(ALM\).  
  
##  <a name="CreatingListDef"></a> Creazione di un elenco di SharePoint  
 Creare un progetto di elenco di SharePoint e associare la definizione dell'elenco alle attività.  
  
#### Per creare un progetto di elenco di SharePoint  
  
1.  Aprire la finestra di dialogo **Nuovo progetto**, espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
2.  Nel pannello **Modelli**, selezionare il modello **Progetto SharePoint 2010**, assegnare il nome ProjectTaskList al progetto, quindi selezionare il pulsante **OK**.  
  
     Verrà visualizzata la **Personalizzazione guidata SharePoint**.  
  
3.  Specificare il sito di SharePoint locale utilizzato per il debug, scegliere il pulsante di opzione **Distribuisci come soluzione farm** quindi selezionare il pulsante **Fine**.  
  
4.  Aprire il menu di scelta rapida per il progetto, quindi scegliere **Aggiungi**, **Nuovo elemento**.  
  
5.  Nel riquadro **Modelli** scegliere il modello **Elenco**, quindi fare clic sul pulsante **Aggiungi**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
6.  Nella casella di **Specifica il nome da visualizzare per l'elenco**, immettere l'elenco delle attività del progetto.  
  
7.  Scegliere il pulsante di opzione **Crea un elenco non personalizzabile basato su un tipo di elenco esistente di** quindi, nel suo elenco, scegliere **Attività**quindi selezionare il pulsante **Fine**.  
  
     L'elenco, la funzionalità ed il pacchetto vengono visualizzati in **Esplora soluzioni**.  
  
##  <a name="AddEventRcvr"></a> Aggiunta di un ricevitore di eventi  
 Nell'elenco delle attività è possibile aggiungere un ricevitore di eventi che imposta automaticamente la scadenza e la descrizione dell'attività.  La procedura riportata di seguito consente di aggiungere un semplice gestore eventi all'istanza di elenco come un ricevitore di eventi.  
  
#### Per aggiungere un ricevitore di eventi  
  
1.  Aprire il menu di scelta rapida per il nodo del progetto, scegliere **Aggiungi** e quindi selezionare **Nuovo elemento**.  
  
2.  Nell'elenco dei modelli di SharePoint, selezionare il modello **Ricevitore di eventi** e denominarlo **ProjectTaskListEventReceiver**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
3.  Dalla pagina **Selezionare le impostazioni del ricevitore di eventi**, scegliere **Eventi degli elementi dell'elenco** come tipo di ricevitore di eventi nell'elenco **Selezionare il tipo di ricevitore di eventi desiderato**.  
  
4.  Nell'elenco di **Selezionare l'elemento da utilizzare come origine eventi**, scegliere **Attività**.  
  
5.  Nell'elenco di eventi da gestire, selezionare la casella di controllo accanto a **È stato aggiunto un elemento**, quindi scegliere il pulsante **Fine**.  
  
     Al progetto viene aggiunto un nuovo nodo del ricevitore di eventi con un file di codice denominato **ProjectTaskListEventReceiver**.  
  
6.  Aggiungere codice al metodo `ItemAdded` nel file di codice **ProjectTaskListEventReceiver**.  A ogni nuova attività aggiunta vengono assegnate una scadenza predefinita e una descrizione.  La scadenza predefinita è il primo luglio 2009.  
  
     [!code-csharp[SPProjectTaskList#1](../snippets/csharp/VS_Snippets_OfficeSP/spprojecttasklist/cs/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]
     [!code-vb[SPProjectTaskList#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spprojecttasklist/vb/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]  
  
##  <a name="CustomizeFeature"></a> Personalizzazione della funzionalità dell'elenco attività del progetto  
 Quando si crea una soluzione SharePoint, tramite Visual Studio vengono create automaticamente funzionalità per gli elementi del progetto predefiniti.  Le impostazioni dell'elenco attività del progetto possono essere personalizzate per il sito di SharePoint tramite la finestra di progettazione della funzionalità.  
  
#### Per personalizzare la funzionalità dell'elenco attività del progetto  
  
1.  In **Esplora soluzioni** espandere **Funzionalità**.  
  
2.  Aprire il menu di scelta rapida per **Funzionalità1**, quindi scegliere **Progettazione visualizzazioni**.  
  
3.  Nella casella **Titolo**, inserire **Project Task List Feature**.  
  
4.  Nell'elenco **Ambito** scegliere **Web**.  
  
5.  Nella finestra **Proprietà** inserire **1.0.0.0** come valore della proprietà **Versione**.  
  
##  <a name="CustomizePackage"></a> Personalizzazione del pacchetto dell'elenco attività del progetto  
 Quando si crea un progetto SharePoint, tramite Visual Studio vengono aggiunte automaticamente al pacchetto le funzionalità in cui sono contenuti gli elementi del progetto predefiniti.  Le impostazioni dell'elenco attività del progetto possono essere personalizzate per il sito di SharePoint tramite progettazione pacchetti.  
  
#### Per personalizzare il pacchetto dell'elenco attività del progetto  
  
1.  In **Esplorasoluzioni** aprire il menu di scelta rapida per **Pacchetto**, quindi scegliere **Progettazione visualizzazioni**.  
  
2.  Nella casella **Nome** inserire **ProjectTaskListPackage**.  
  
3.  Selezionare la casella di controllo **Reimposta server Web**.  
  
##  <a name="BuildTest"></a> Compilazione e test dell'elenco attività del progetto  
 Quando si esegue il progetto viene aperto il sito di SharePoint.  Tuttavia, è necessario spostarsi manualmente nel percorso dell'elenco attività.  
  
#### Per testare l'elenco attività del progetto  
  
1.  Premere il pulsante F5 per compilare e distribuire l'elenco di attività del progetto.  
  
     Verrà aperto il sito di SharePoint.  
  
2.  Scegliere la scheda **Home**.  
  
3.  Nell'intestazione laterale sinistra, scegliere il collegamento **Elenco attività di progetto**.  
  
     Viene visualizzata la pagina Elenco attività progetto.  
  
4.  Nella scheda **Elenco strumenti**, scegliere la scheda **Elementi**.  
  
5.  Nel gruppo **Elementi**, scegliere il pulsante **Nuovo elemento**.  
  
6.  Nella casella di testo **Titolo** inserire Attività1.  
  
7.  Scegliere il pulsante **Salva**.  
  
     Dopo aver aggiornato il sito, l'attività **Attività1** viene visualizzata con la scadenza del primo luglio 2009.  
  
8.  Scegliere **Attività1**.  
  
     Viene mostrata la visualizzazione dettagliata dell'attività e nella descrizione viene riportato "Questa è un'attività critica".  
  
##  <a name="Deploy"></a> Distribuzione dell'elenco attività del progetto  
 Dopo la compilazione e il test dell'elenco attività del progetto, è possibile distribuirlo nel *sistema locale* o in un *sistema remoto*.  Il sistema locale è lo stesso computer in cui è stata sviluppata la soluzione, mentre un sistema remoto è un altro computer.  
  
#### Per distribuire l'elenco attività del progetto nel sistema locale  
  
1.  Nella barra dei menu di Visual Studio, scegliere **Compilazione**, **Distribuisci soluzione**.  
  
     Il pool di applicazioni IIS viene riciclato da Visual Studio, vengono ritratte tutte le versioni esistenti della soluzione, viene copiato il file del pacchetto della soluzione \(con estensione wsp\) in SharePoint, quindi vengono attivate le relative funzionalità.  È ora possibile utilizzare la soluzione in SharePoint.  Per ulteriori informazioni sui passaggi di configurazione della distribuzione, vedere [Procedura: modificare una configurazione di distribuzione SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
#### Per distribuire l'elenco attività del progetto in un sistema remoto  
  
1.  Nella barra dei menu di Visual Studio, scegliere **Compilazione**, **Pubblica**.  
  
2.  Nella finestra di dialogo **Pubblica**, scegliere il pulsante di opzione **Pubblica su file system**.  
  
     È possibile modificare il percorso di destinazione nella finestra di dialogo **Pubblica** scegliendo il pulsante con i puntini di sospensione ![Icona con i puntini di sospensione](../sharepoint/media/ellipsisicon.png "Icona con i puntini di sospensione") e passando ad un'altra posizione.  
  
3.  Selezionare il pulsante **Pubblica**.  
  
     Viene creato un file .wsp per la soluzione.  
  
4.  Copiare il file con estensione wsp nel sistema SharePoint remoto.  
  
5.  Utilizzare il comando `Add-SPUserSolution` di PowerShell per installare il pacchetto nell'installazione remota di SharePoint. \(Per le soluzioni farm, utilizzare il comando `Add-SPSolution`\).  
  
     Ad esempio, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.  
  
6.  Utilizzare il comando `Install-SPUserSolution` di PowerShell per distribuire la soluzione. \(Per le soluzioni farm, utilizzare il comando `Install-SPSolution`\).  
  
     Ad esempio, `Install-SPUserSolution –Identity ProjectTaskList.wsp –Site http://NewSiteName`.  
  
     Per ulteriori informazioni sulla distribuzione remota, vedere [Utilizzo di soluzioni](http://go.microsoft.com/fwlink/?LinkId=217680) ed [Aggiunta e distribuzione di soluzioni con PowerShell in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).  
  
## Passaggi successivi  
 Per ulteriori informazioni su come personalizzare e distribuire le soluzioni SharePoint consultare gli argomenti seguenti:  
  
-   [Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [Windows PowerShell per SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  