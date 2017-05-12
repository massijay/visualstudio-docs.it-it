---
title: "Procedura dettagliata: associazione dati semplice in un progetto a livello di documento"
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
  - "dati [sviluppo per Office in Visual Studio], associazione dati"
  - "associazione dati [sviluppo per Office in Visual Studio], cella di foglio di lavoro a campo di database"
  - "Database (campo) [sviluppo per Office in Visual Studio]"
  - "associazione dati semplice [sviluppo per Office in Visual Studio]"
  - "fogli di lavoro [sviluppo per Office in Visual Studio], associazione di cella di foglio di lavoro a campo di database"
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Procedura dettagliata: associazione dati semplice in un progetto a livello di documento
  In questa procedura dettagliata vengono illustrate le nozioni di base sull'associazione dati in un progetto a livello di documento.  Un singolo campo dati di un database SQL Server viene associato a un intervallo denominato in Microsoft Office Excel.  Nella procedura dettagliata viene inoltre illustrato come aggiungere controlli che consentono di scorrere tutti i record della tabella.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'origine dati per un progetto Excel.  
  
-   Aggiunta di controlli a un foglio di lavoro.  
  
-   Scorrimento dei record del database.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un server in cui sia presente il database di esempio di SQL Server Northwind.  
  
-   Autorizzazioni per leggere il database SQL Server o scrivere in esso.  
  
## Creazione di un nuovo progetto  
 In questo passaggio verrà creato un progetto cartella di lavoro di Excel.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **My Simple Data Binding**, utilizzando Visual Basic o C\#.  Verificare che l'opzione **Crea nuovo documento** sia selezionata.  Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 La nuova cartella di lavoro di Excel verrà aperta nella finestra di progettazione e il progetto My Simple Data Binding verrà aggiunto a **Esplora soluzioni**.  
  
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
  
8.  Selezionare la casella di controllo accanto alla tabella **Customers**.  
  
9. Fare clic su **Fine**.  
  
 La tabella **Customers** verrà aggiunta alla finestra **Origini dati** nella procedura guidata.  Inoltre, aggiungerà un DataSet tipizzato al progetto visualizzato in **Esplora soluzioni**.  
  
## Aggiunta di controlli al foglio di lavoro  
 Per questa procedura dettagliata sono necessari due intervalli denominati e quatto pulsanti nel primo foglio di lavoro.  Aggiungere innanzitutto i due intervalli denominati dalla finestra **Origini dati** in modo che vengano associati automaticamente all'origine dati.  Quindi, aggiungere i pulsanti dalla **Casella degli strumenti**.  
  
#### Per aggiungere i due intervalli denominati  
  
1.  Verificare che la cartella di lavoro **My Simple Data Binding.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con **Foglio1** visualizzare.  
  
2.  Aprire la finestra **Origini dati** ed espandere il nodo **Customers**.  
  
3.  Selezionare la colonna **CompanyName**, quindi fare clic sulla freccia a discesa visualizzata.  
  
4.  Selezionare **NamedRange** nell'elenco a discesa e trascinare la colonna **CompanyName** alla cella **A1**.  
  
     Un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `companyNameNamedRange` verrà creato nella cella **A1**.  Contemporaneamente, una classe <xref:System.Windows.Forms.BindingSource> denominata `customersBindingSource`, un adattatore di tabelle e un'istanza di <xref:System.Data.DataSet> verranno aggiunti al progetto.  Il controllo è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associata all'istanza di <xref:System.Data.DataSet>.  
  
5.  Selezionare la colonna **CustomerID** nella finestra **Origini dati**, quindi fare clic sulla freccia a discesa visualizzata.  
  
6.  Fare clic su **NamedRange** nell'elenco a discesa e trascinare la colonna **CustomerID** alla cella **B1**.  
  
7.  Un altro controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `customerIDNamedRange` verrà creato nella cella **B1** e associato a <xref:System.Windows.Forms.BindingSource>.  
  
#### Per aggiungere i quattro pulsanti  
  
1.  Dalla scheda **Controlli comuni** della **Casella degli strumenti**, aggiungere un controllo <xref:System.Windows.Forms.Button> alla cella **A3** del foglio di lavoro.  
  
     Il nome di questo pulsante sarà `Button1`.  
  
2.  Aggiungere gli altri tre pulsanti alle celle nell'ordine e con i nomi indicati di seguito:  
  
    |Cella|\(Nome\)|  
    |-----------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 Il passaggio successivo consiste nell'aggiungere testo ai pulsanti e, in C\#, nell'aggiungere i gestori eventi.  
  
## Inizializzazione dei controlli  
 Impostare il testo del pulsante e aggiungere i gestori eventi durante l'evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>.  
  
#### Per inizializzare i controlli  
  
1.  Fare clic con il pulsante destro del mouse su **Sheet1.vb** o **Sheet1.cs** in **Esplora soluzioni** e scegliere **Visualizza codice** dal menu di scelta rapida.  
  
2.  Aggiungere il codice riportato di seguito al metodo `Sheet1_Startup` per impostare il testo per ciascun pulsante.  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#2)]  
  
3.  Solo per C\#, aggiungere gestori eventi per gli eventi click al metodo `Sheet1_Startup`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#3)]  
  
 Aggiungere quindi il codice per gestire gli eventi <xref:System.Windows.Forms.Control.Click> dei pulsanti in modo che l'utente possa scorrere i record.  
  
## Aggiunta di codice per attivare lo scorrimento dei record  
 Aggiungere il codice al gestore eventi <xref:System.Windows.Forms.Control.Click> di ciascun pulsante per scorrere i record.  
  
#### Per spostarsi al primo record  
  
1.  Aggiungere un gestore eventi per l'evento <xref:System.Windows.Forms.Control.Click> del pulsante `Button1`, quindi aggiungere il codice riportato di seguito per spostarsi al primo record:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#4)]  
  
#### Per spostarsi al record precedente  
  
1.  Aggiungere un gestore eventi per l'evento <xref:System.Windows.Forms.Control.Click> del pulsante `Button2`, quindi aggiungere il codice riportato di seguito per spostarsi di una posizione indietro:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#5)]  
  
#### Per spostarsi al record successivo  
  
1.  Aggiungere un gestore eventi per l'evento <xref:System.Windows.Forms.Control.Click> del pulsante `Button3`, quindi aggiungere il codice riportato di seguito per avanzare di una posizione:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#6)]  
  
#### Per spostarsi all'ultimo record  
  
1.  Aggiungere un gestore eventi per l'evento <xref:System.Windows.Forms.Control.Click> del pulsante `Button4`, quindi aggiungere il codice riportato di seguito per spostarsi all'ultimo record:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#7)]  
  
## Verifica dell'applicazione  
 A questo punto è possibile eseguire il test della cartella di lavoro per assicurarsi che sia possibile scorrere i record del database.  
  
#### Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il primo record sia visualizzato nelle celle **A1** e **B1**.  
  
3.  Fare clic sul pulsante **\>** \(`Button3`\) e verificare che il record successivo sia visualizzato nelle celle **A1** e **B1**.  
  
4.  Fare clic sugli altri pulsanti di scorrimento per confermare la variazione prevista dei record.  
  
## Passaggi successivi  
 In questa procedura dettagliata sono state fornite le informazioni di base per l'associazione di un intervallo denominato a un campo di un database.  Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Memorizzazione dei dati nella cache per l'utilizzo offline.  Per ulteriori informazioni, vedere [Procedura: memorizzare dati nella cache per l'utilizzo offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Associazione di celle a più colonne di una tabella invece che a un solo campo.  Per ulteriori informazioni, vedere [Procedura dettagliata: associazione dati complessa in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Utilizzo di un controllo <xref:System.Windows.Forms.BindingNavigator> per scorrere i record.  Per ulteriori informazioni, vedere [Procedura: esplorare i dati con il controllo BindingNavigator Windows Form](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb).  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Procedura dettagliata: associazione dati complessa in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  