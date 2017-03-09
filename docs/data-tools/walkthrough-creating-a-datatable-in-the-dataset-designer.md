---
title: "Procedura dettagliata: creazione di una DataTable in Progettazione DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], Progettazione DataSet"
  - "Progettazione DataSet, creazione di tabelle di dati"
  - "DataTable (oggetti), creazione"
  - "tabelle [Visual Studio], creazione"
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura dettagliata: creazione di una DataTable in Progettazione DataSet
In questa procedura dettagliata viene illustrata la creazione di una <xref:System.Data.DataTable> \(senza un TableAdapter\) mediante **Progettazione DataSet**.  Per informazioni su come creare tabelle di dati che includano oggetti TableAdapter, vedere [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
 Di seguito vengono elencate le attività illustrate nella procedura dettagliata:  
  
-   Creazione di un nuovo progetto Applicazione Windows  
  
-   Aggiunta di un nuovo dataset all'applicazione  
  
-   Aggiunta di una nuova tabella dati al dataset  
  
-   Aggiunta di colonne alla tabella di dati  
  
-   Impostazione della chiave primaria per la tabella  
  
## Creazione di una nuova applicazione Windows  
  
#### Per creare un nuovo progetto di applicazione Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Scegliere un linguaggio di programmazione nel riquadro **Tipi progetto**.  
  
3.  Selezionare **Applicazione Windows** nel riquadro **Modelli**.  
  
4.  Assegnare al progetto il nome `DataTableWalkthrough`, quindi scegliere **OK**.  
  
     Il progetto verrà aggiunto a **Esplora soluzioni** e nella finestra di progettazione verrà visualizzato **Form1**.  
  
## Aggiunta di un nuovo dataset all'applicazione  
  
#### Per aggiungere un nuovo elemento dataset al progetto  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo Aggiungi nuovo elemento.  
  
2.  Scegliere **DataSet** nella casella **Modelli**.  
  
3.  Scegliere **Aggiungi**.  
  
     Un file denominato **DataSet1.xsd** verrà aggiunto al progetto e aperto in **Progettazione DataSet**.  
  
## Aggiunta di una nuova tabella di dati al dataset  
  
#### Per aggiungere una nuova tabella dati al dataset  
  
1.  Trascinare una **DataTable** dalla scheda **DataSet** della **Casella degli strumenti** in **Progettazione DataSet**.  
  
     Una tabella denominata **DataTable1** viene aggiunta al dataset.  
  
    > [!NOTE]
    >  Per creare una tabella dati che includa un TableAdapter, vedere [Procedura dettagliata: creazione di un oggetto TableAdapter con più query](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Fare clic sulla barra del titolo della **DataTable1** e rinominarla `Music`.  
  
## Aggiunta di colonne alla tabella di dati  
  
#### Per aggiungere colonne alla tabella dati  
  
1.  Fare clic con il pulsante destro del muse sulla tabella **Music**.  Scegliere **Aggiungi**, quindi **Colonna**.  
  
2.  Assegnare alla colonna il nome `SongID`.  
  
3.  Nella finestra **Proprietà** impostare la proprietà <xref:System.Data.DataColumn.DataType%2A> su <xref:System.Int16?displayProperty=fullName>.  
  
4.  Ripetere la procedura e aggiungere le seguenti colonne:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## Impostazione della chiave primaria per la tabella  
 Tutte le tabelle dati dovrebbero avere una chiave primaria.  Una chiave primaria identifica in modo univoco un record specifico in una tabella dati.  
  
#### Per impostare la chiave primaria della tabella dati  
  
-   Fare clic con il pulsante destro del mouse sulla colonna **SongID**, quindi fare clic su **Imposta chiave primaria**.  
  
     Un'icona della chiave viene visualizzata accanto alla colonna **SongID**.  
  
## Salvataggio del progetto  
  
#### Per salvare il progetto DataTableWalkthrough  
  
-   Scegliere **Salva tutto** dal menu **File**.  
  
## Passaggi successivi  
 Una volta completata la creazione della tabella, è possibile eseguire una delle seguenti azioni:  
  
|Per|Vedere|  
|---------|------------|  
|Creare un form per immettere dati|[Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Aggiungere dati alla tabella|[Aggiunta di dati a una DataTable](../Topic/Adding%20Data%20to%20a%20DataTable.md).|  
|Visualizzare dati in una tabella|[Visualizzazione dei dati in DataTable](../Topic/Viewing%20Data%20in%20a%20DataTable.md).|  
|Modificare dati|[Modifiche di DataTable](../Topic/DataTable%20Edits.md)|  
|Eliminare una riga da una tabella|[Eliminazione di DataRow](../Topic/DataRow%20Deletion.md)|  
  
## Vedere anche  
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)