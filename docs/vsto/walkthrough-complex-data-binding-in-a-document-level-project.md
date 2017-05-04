---
title: "Procedura dettagliata: associazione dati complessa in un progetto a livello di documento | Microsoft Docs"
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
  - "dati complessi [sviluppo per Office in Visual Studio]"
  - "dati [sviluppo per Office in Visual Studio], associazione dati"
  - "associazione dati [sviluppo per Office in Visual Studio], più colonne"
  - "associazione dati su più colonne [sviluppo per Office in Visual Studio]"
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Procedura dettagliata: associazione dati complessa in un progetto a livello di documento
  In questa procedura dettagliata vengono illustrate le nozioni di base sull'associazione dati complessa in un progetto a livello di documento.  È possibile associare più celle di un foglio di lavoro di Microsoft Office Excel ai campi presenti nel database Northwind di SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di un'origine dati al progetto Cartella di lavoro.  
  
-   Aggiunta di controlli con associazione a dati a un foglio di lavoro.  
  
-   Salvataggio nel database delle modifiche apportate ai dati.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un server in cui sia presente il database di esempio di SQL Server Northwind.  
  
-   Autorizzazioni per leggere il database SQL Server o scrivere in esso.  
  
## Creazione di un nuovo progetto  
 Il primo passaggio consiste nella creazione di un progetto cartella di lavoro di Excel.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **My Complex Data Binding**.  Nella procedura guidata, scegliere **Crea un nuovo documento**.  
  
     Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     La nuova cartella di lavoro di Excel viene aperta nella finestra di progettazione di Visual Studio e il progetto My Complex Data Binding viene aggiunto in **Esplora soluzioni**.  
  
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
  
8.  Selezionare la casella di controllo accanto alla tabella **Employees**.  
  
9. Fare clic su **Fine**.  
  
 La procedura guidata aggiungerà la tabella **Employees** alla finestra **Origini dati**.  Inoltre, aggiungerà un DataSet tipizzato al progetto visualizzato in **Esplora soluzioni**.  
  
## Aggiunta di controlli al foglio di lavoro  
 Quando viene aperta la cartella di lavoro, in un foglio di lavoro verrà visualizzata la tabella **Employees**.  Gli utenti potranno apportare modifiche ai dati e salvare quindi tali modifiche nel database facendo clic su un pulsante.  
  
 Per associare automaticamente il foglio di lavoro alla tabella, è possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> al foglio di lavoro dalla finestra **Origini dati**.  Per consentire all'utente di salvare le modifiche, aggiungere un controllo <xref:System.Windows.Forms.Button> dalla **Casella degli strumenti**.  
  
#### Per aggiungere un oggetto elenco  
  
1.  Verificare che la cartella di lavoro **My Complex Data Binding.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con **Foglio1** visualizzare.  
  
2.  Aprire la finestra **Origini dati** e selezionare il nodo **Employees**.  
  
3.  Fare clic sulla freccia a discesa visualizzata.  
  
4.  Selezionare **ListObject** nell'elenco a discesa.  
  
5.  Trascinare la tabella **Employees** nella cella **A6**.  
  
     Un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `EmployeesListObject` viene creato nella cella **A6**.  Contemporaneamente vengono aggiunti al progetto un oggetto <xref:System.Windows.Forms.BindingSource> denominato `EmployeesBindingSource`, un adattatore per la tabella e un'istanza dell'oggetto <xref:System.Data.DataSet>.  Il controllo è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associata all'istanza di <xref:System.Data.DataSet>.  
  
#### Per aggiungere un pulsante  
  
1.  Dalla scheda **Controlli comuni** della **Casella degli strumenti**, aggiungere un controllo <xref:System.Windows.Forms.Button> alla cella **A4** del foglio di lavoro.  
  
 Il passaggio successivo consiste nell'aggiunta di testo al pulsante quando il foglio di lavoro viene aperto.  
  
## Inizializzazione del controllo  
 Aggiungere testo al pulsante nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>.  
  
#### Per inizializzare il controllo  
  
1.  Fare clic con il pulsante destro del mouse su **Sheet1.vb** o **Sheet1.cs** in **Esplora soluzioni** e scegliere **Visualizza codice** dal menu di scelta rapida.  
  
2.  Aggiungere il codice riportato di seguito al metodo `Sheet1_Startup` per impostare il testo per b`utton`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#8)]  
  
3.  Solo per C\#, aggiungere un gestore eventi per l'evento <xref:System.Windows.Forms.Control.Click> al metodo `Sheet1_Startup`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#9)]  
  
 Aggiungere ora il codice per la gestione dell'evento <xref:System.Windows.Forms.Control.Click> del pulsante.  
  
## Salvataggio delle modifiche nel database  
 Le eventuali modifiche apportate ai dati sono limitate al solo DataSet locale finché non vengono salvate nuovamente in modo esplicito nel database.  
  
#### Per salvare le modifiche nel database  
  
1.  Aggiungere un gestore eventi per l'evento <xref:System.Windows.Forms.Control.Click> di b`utton` e aggiungere il codice riportato di seguito per eseguire il commit nel database di tutte le modifiche apportate nel dataset.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#10)]  
  
## Verifica dell'applicazione  
 A questo punto è possibile testare la cartella di lavoro per verificare che i dati vengano visualizzati nel modo previsto e che sia possibile modificare i dati contenuti nell'oggetto elenco.  
  
#### Per eseguire il test dell'associazione dati  
  
-   Premere F5.  
  
     All'apertura della cartella di lavoro, verificare che il controllo ListObject contenga i dati della tabella **Employees**.  
  
#### Per modificare i dati  
  
1.  Fare clic sulla cella **B7**, che dovrà contenere il nome **Davolio**.  
  
2.  Digitare il nome Anderson e premere INVIO.  
  
#### Per modificare l'intestazione di una colonna  
  
1.  Fare clic sulla cella che contiene l'intestazione di colonna **LastName**.  
  
2.  Digitare Last Name, includendo uno spazio tra le due parole, quindi premere INVIO.  
  
#### Per salvare i dati  
  
1.  Scegliere **Salva** nel foglio di lavoro.  
  
2.  Uscire da Excel.  Scegliere **No** quando viene visualizzata la richiesta di salvare le modifiche apportate.  
  
3.  Premere F5 per eseguire nuovamente il progetto.  
  
     Nel controllo ListObject vengono inseriti i dati della tabella **Employees**.  
  
4.  Il nome presente nella cella **B7** è ancora Anderson a causa della modifica apportata ai dati e salvata nel database.  L'intestazione di colonna **LastName** è stata riportata alla forma originale senza spazi in quanto tale intestazione non è associata al database e le modifiche apportate al foglio di lavoro non sono state salvate.  
  
#### Per aggiungere nuove righe  
  
1.  Selezionare una cella all'interno del controllo ListObject.  
  
     Nella parte inferiore dell'elenco viene visualizzata una nuova riga, nella cui prima cella è contenuto un asterisco \(**\***\).  
  
2.  Aggiungere le informazioni riportate di seguito nella riga vuota.  
  
    |EmployeeID|LastName|FirstName|Titolo|  
    |----------------|--------------|---------------|------------|  
    |10|Ito|Shu|Sales Manager|  
  
#### Per eliminare le righe  
  
-   Fare clic con il pulsante destro del mouse sul numero 16 \(riga 16\) all'estremità sinistra del foglio di lavoro, quindi scegliere **Elimina**.  
  
#### Per ordinare le righe all'interno del controllo ListObject  
  
1.  Selezionare una cella all'interno del controllo ListObject.  
  
     In ciascuna intestazione di colonna vengono visualizzati pulsanti a forma di freccia.  
  
2.  Fare clic sul pulsante freccia nell'intestazione di colonna **Last Name**.  
  
3.  Scegliere **Ordinamento crescente**.  
  
     Le righe vengono ordinate alfabeticamente in base ai cognomi.  
  
#### Per filtrare le informazioni  
  
1.  Selezionare una cella all'interno del controllo ListObject.  
  
2.  Fare clic sul pulsante freccia nell'intestazione di colonna **Title**.  
  
3.  Scegliere **Sales Representative**.  
  
     Nel controllo ListObject vengono visualizzate solo le righe che contengono **Sales Representative** nella colonna **Title**.  
  
4.  Fare nuovamente clic sul pulsante freccia nell'intestazione di colonna **Title**.  
  
5.  Fare clic su **\(Tutto\)**.  
  
     Il filtro viene rimosso e vengono visualizzate tutte le righe.  
  
## Passaggi successivi  
 In questa procedura dettagliata sono illustrati i concetti di base sull'associazione di una tabella di un database a un controllo ListObject.  Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Memorizzazione dei dati nella cache per l'utilizzo offline.  Per ulteriori informazioni, vedere [Procedura: memorizzare dati nella cache per l'utilizzo offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Distribuzione della soluzione.  Per ulteriori informazioni, vedere [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
-   Creazione di una relazione master\-dettagli tra un campo e una tabella.  Per ulteriori informazioni, vedere [Procedura dettagliata: creazione di una relazione master-dettagli mediante un DataSet memorizzato nella cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Procedura dettagliata: associazione dati semplice in un progetto a livello di documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  