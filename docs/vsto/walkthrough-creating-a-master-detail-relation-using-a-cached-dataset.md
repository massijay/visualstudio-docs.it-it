---
title: "Procedura dettagliata: creazione di una relazione master-dettagli mediante un DataSet memorizzato nella cache"
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
  - "memorizzazione di dati nella cache [sviluppo per Office in Visual Studio], relazione Master-Details"
  - "master-details (tabelle) [sviluppo per Office in Visual Studio], procedure dettagliate"
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Procedura dettagliata: creazione di una relazione master-dettagli mediante un DataSet memorizzato nella cache
  In questa procedura dettagliata viene illustrata la creazione di una relazione master\-dettagli su un foglio di lavoro e la memorizzazione nella cache dei dati per utilizzare la soluzione offline.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In particolare, vengono illustrate le seguenti operazioni:  
  
-   Aggiunta di controlli a un foglio di lavoro.  
  
-   Impostazione di un DataSet da memorizzare nella cache in un foglio di lavoro.  
  
-   Aggiunta di codice per abilitare lo scorrimento dei record.  
  
-   Test del progetto.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso al database di esempio Northwind di SQL Server.  Il database può essere sul computer di sviluppo o su un computer server.  
  
-   Autorizzazioni per leggere il database SQL Server o scrivere in esso.  
  
## Creazione di un nuovo progetto  
 In questo passaggio verrà creato un progetto Cartella di lavoro di Excel.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto Cartella di lavoro di Excel con il nome **My Master\-Detail** utilizzando Visual Basic o C\#.  Verificare che l'opzione **Crea nuovo documento** sia selezionata.  Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 La nuova cartella di lavoro di Excel viene aperta nella finestra di progettazione di Visual Studio e il progetto My Master\-Detail viene aggiunto in **Esplora soluzioni**.  
  
## Creazione dell'origine dati  
 Utilizzare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.  
  
#### Per creare l'origine dati  
  
1.  Se la finestra **Origini dati** non è visibile, vengono visualizzati da, sulla barra dei menu, scegliente **Visualizza**, **Altre finestre**, **Origini dati**.  
  
2.  Scegliere **Aggiungi nuova origine dati** per avviare **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** e scegliere **Avanti**.  
  
4.  Selezionare una connessione dati al database di SQL Server di esempio Northwind oppure aggiungere una nuova connessione tramite il pulsante **Nuova connessione**.  
  
5.  Dopo aver selezionato o creato una connessione, scegliere **Avanti**.  
  
6.  Deselezionare l'opzione per salvare la connessione, se selezionata, quindi scegliere **Avanti**.  
  
7.  Espandere il nodo **Tabelle** nella finestra **Oggetti di database**.  
  
8.  Selezionare la tabella **Orders** e la tabella **Order Details**.  
  
9. Fare clic su **Fine**.  
  
 La procedura guidata aggiungerà le due tabelle alla finestra **Origini dati**.  Inoltre, aggiungerà un DataSet tipizzato al progetto visualizzato in **Esplora soluzioni**.  
  
## Aggiunta di controlli al foglio di lavoro  
 In questo passaggio, verranno aggiunti al primo foglio di lavoro un intervallo denominato, un oggetto elenco e due pulsanti.  Aggiungere in primo luogo l'intervallo denominato e l'oggetto elenco dalla finestra **Origini dati**, in modo che vengano associati automaticamente all'origine dati.  Quindi, aggiungere i pulsanti dalla **Casella degli strumenti**.  
  
#### Per aggiungere un intervallo denominato e un oggetto elenco  
  
1.  Verificare che la cartella di lavoro **My Master\-Detail.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con **Foglio1** visualizzare.  
  
2.  Aprire la finestra **Origini dati** ed espandere il nodo **Orders**.  
  
3.  Selezionare la colonna **OrderID**, quindi fare clic sulla freccia a discesa visualizzata.  
  
4.  Selezionare **NamedRange** nell'elenco a discesa, quindi trascinare la colonna **OrderID** nella cella **A2**.  
  
     Un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `OrderIDNamedRange` viene creato nella cella **A2**.  Contemporaneamente, al progetto sono aggiunti un oggetto <xref:System.Windows.Forms.BindingSource> denominato `OrdersBindingSource`, un adattatore per la tabella e un'istanza dell'oggetto <xref:System.Data.DataSet>.  Il controllo è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associata all'istanza di <xref:System.Data.DataSet>.  
  
5.  Scorrere l'elenco verso il basso, oltre le colonne al di sotto della tabella **Orders**.  Alla fine dell'elenco è presente la tabella **Order Details**; la tabella è posizionata in questo punto in quanto elemento figlio della tabella **Orders**.  Selezionare questa tabella **Order Details**, non quella situata allo stesso livello della tabella **Orders** e fare clic sulla freccia a discesa visualizzata.  
  
6.  Selezionare **ListObject** nell'elenco a discesa, quindi trascinare la tabella **OrderDetails** nella cella **A6**.  
  
7.  Un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato **Order\_DetailsListObject** viene creato nella cella **A6** e viene associato all'oggetto <xref:System.Windows.Forms.BindingSource>.  
  
#### Per aggiungere due pulsanti  
  
1.  Dalla scheda **Controlli comuni** della **Casella degli strumenti**, aggiungere un controllo <xref:System.Windows.Forms.Button> alla cella **A3** del foglio di lavoro.  
  
     Il nome di questo pulsante sarà `Button1`.  
  
2.  Aggiungere un altro controllo <xref:System.Windows.Forms.Button> alla cella **B3** del foglio di lavoro.  
  
     Il nome di questo pulsante sarà `Button2`.  
  
 Contrassegnare quindi il DataSet per la memorizzazione nella cache all'interno del documento.  
  
## Memorizzazione del DataSet nella cache  
 Contrassegnare il DataSet per la memorizzazione nella cache rendendolo pubblico e impostando la proprietà **CacheInDocument**.  
  
#### Per memorizzare il DataSet nella cache  
  
1.  Selezionare **NorthwindDataSet** nella barra dei componenti.  
  
2.  Nella finestra **Proprietà**, modificare la proprietà **Modifiers** impostandola su **Public**.  
  
     I DataSet devono essere di tipo pubblico prima che sia abilitata la memorizzazione nella cache.  
  
3.  Modificare la proprietà **CacheInDocument** impostandola su **True**.  
  
 Il passaggio successivo è costituito dall'aggiunta di testo ai pulsanti, e, in C\#, dall'aggiunta di codice per agganciare i gestori eventi.  
  
## Inizializzazione dei controlli  
 Impostare il testo del pulsante e aggiungere gestori eventi durante l'evento <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>.  
  
#### Per inizializzare i dati e i controlli  
  
1.  Fare clic con il pulsante destro del mouse su **Sheet1.vb** o **Sheet1.cs** in **Esplora soluzioni** e scegliere **Visualizza codice** dal menu di scelta rapida.  
  
2.  Aggiungere il codice riportato di seguito al metodo `Sheet1_Startup` per impostare il testo per i pulsanti.  
  
     [!code-csharp[Trin_VstcoreDataExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#15)]
     [!code-vb[Trin_VstcoreDataExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#15)]  
  
3.  Solo per C\#, aggiungere gestori eventi per gli eventi click al metodo `Sheet1_Startup`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#16)]  
  
## Aggiunta di codice per attivare lo scorrimento dei record  
 Aggiungere il codice al gestore eventi <xref:System.Windows.Forms.Control.Click> di ciascun pulsante per scorrere i record.  
  
#### Per scorrere i record  
  
1.  Aggiungere un gestore eventi per l'evento <xref:System.Windows.Forms.Control.Click> di `Button1` e aggiungere il codice riportato di seguito per spostarsi all'indietro da un record a un altro:  
  
     [!code-csharp[Trin_VstcoreDataExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#17)]
     [!code-vb[Trin_VstcoreDataExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#17)]  
  
2.  Aggiungere un gestore eventi per l'evento <xref:System.Windows.Forms.Control.Click> di `Button2` e aggiungere il codice riportato di seguito per spostarsi in avanti da un record a un altro:  
  
     [!code-csharp[Trin_VstcoreDataExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#18)]
     [!code-vb[Trin_VstcoreDataExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#18)]  
  
## Verifica dell'applicazione  
 A questo punto è possibile eseguire il test della cartella di lavoro per accertarsi che i dati siano visualizzati nel modo previsto e che sia possibile utilizzare la soluzione offline.  
  
#### Per eseguire il test della memorizzazione nella cache dei dati  
  
1.  Premere **F5**.  
  
2.  Verificare che nell'intervallo denominato e nell'oggetto elenco siano inseriti dati derivanti dall'origine dati.  
  
3.  Scorrere alcuni record facendo clic sui pulsanti.  
  
4.  Salvare la cartella di lavoro, quindi chiudere la cartella di lavoro e Visual Studio.  
  
5.  Disabilitare la connessione al database.  Scollegare il cavo di rete dal computer se il database è situato su un server oppure arrestare il servizio Microsoft SQL Server se il database si trova sul computer di sviluppo.  
  
6.  Aprire Excel e quin**My Master\-Detail.xlsx** aperto directory \\ bin \(\\ my master\-detail \\ bin in Visual Basic o \\ il my master\-detail \\ bin \\ debug in c\).  
  
7.  Scorrere alcuni record per verificare che il foglio di lavoro funzioni normalmente in modalità offline.  
  
8.  Riconnettersi al database.  Ricollegare il computer alla rete se il database è situato su un server oppure avviare il servizio Microsoft SQL Server se il database si trova sul computer di sviluppo.  
  
## Passaggi successivi  
 In questa procedura dettagliata sono illustrate le informazioni di base sulla creazione di una relazione master\-dettagli su un foglio di lavoro e la memorizzazione nella cache di un DataSet.  Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Distribuzione della soluzione.  Per ulteriori informazioni, vedere [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)"\>  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Memorizzazione di dati nella cache](../vsto/caching-data.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  