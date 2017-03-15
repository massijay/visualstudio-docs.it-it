---
title: "Procedura dettagliata: connessione ai dati in un file di database lodale (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "dati [Visual Studio], connessione a SQL Express"
  - "dati [Visual Studio], locali"
  - "database, connessione"
  - "dati locali, SQL Express"
  - "SQL Express, connessione"
  - "SQL Express, procedure dettagliate"
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura dettagliata: connessione ai dati in un file di database lodale (Windows Form)
È possibile visualizzare i dati in modo semplice e rapido da un file di database locale nell'applicazione creando un dataset e aggiungendo controlli associati a dati all'applicazione.  In questa procedura dettagliata verranno visualizzati i dati del file di database locale creato seguendo i passaggi descritti in [Procedura dettagliata: creazione di un file di database locale in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md).  Dopo aver creato un progetto Windows Form, verrà stabilità la connessione al database e verrà indicato di visualizzare i dati della tabella Customers in una griglia dati del form dell'applicazione.  
  
 Quando si crea un database in Visual Studio 2013, il motore LocalDB di SQL Server Express viene utilizzato per accedere a un file di database \(con estensione mdf\) in SQL Server 2012.  Nelle versioni precedenti di Visual Studio il motore di SQL Server Express viene utilizzato per accedere a un file di database \(con estensione mdf\).  Vedere [Cenni preliminari sui dati locali](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
 In questa procedura dettagliata sono incluse le attività seguenti:  
  
-   [Creazione e configurazione di un dataset](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Aggiunta di controlli con associazione a dati](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario accedere al database SampleDatabase.mdf creato completando la procedura descritta in [Procedura dettagliata: creazione di un file di database locale in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Creazione e configurazione di un dataset  
  
#### Per creare e configurare un dataset  
  
1.  Creare un progetto Windows Form e denominarlo ConnectLocalData.  
  
     Vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)  
  
2.  Se la finestra **Origini dati** non è visualizzata, scegliere la combinazione di tasti MAIUSC\-ALT\-D oppure sulla barra dei menu scegliere **Visualizza**, **Altre finestre** e **Mostra origini dati**.  
  
3.  Nella finestra **Origini dati** scegliere il collegamento **Aggiungi nuova origine dati**.  
  
     In **Configurazione guidata origine dati** scegliere **Avanti** due volte per accettare le impostazioni predefinite.  
  
4.  Nella pagina **Seleziona connessione dati** scegliere **Nuova connessione**.  
  
     Verrà visualizzata la finestra di dialogo **Scegli origine dati**.  
  
5.  Nell'elenco **Origine dati** scegliere **File di database Microsoft SQL Server**, quindi scegliere **Continua**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi connessione**.  
  
6.  Nella casella **Nome file di database** specificare il file creato completando la [Procedura dettagliata: creazione di un file di database locale in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md) oppure scegliere il pulsante **Sfoglia** e quindi individuare il file desiderato.  
  
     Per impostazione predefinita, il file si trova in Utenti\\*AccountUtente*\\Documenti\\Visual Studio *Versione*\\Projects\\SampleDatabaseWalkthrough\\SampleDatabaseWalkthrough.  
  
7.  In **Accesso al server** accettare i valori predefiniti, scegliere **OK**, quindi scegliere **Avanti**.  
  
    > [!NOTE]
    >  Quando si creano connessioni a un file di database locale, è possibile scegliere di creare una copia del database nel progetto o di eseguire la connessione al file di database esistente nella posizione attuale.  Vedere [Procedura: gestire file di dati locali nel progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  Nella finestra di dialogo visualizzata scegliere **Sì** per copiare il file di database nel progetto.  
  
9. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.  
  
10. Nella pagina **Seleziona oggetti di Database** espandere il **Tabelle** nodo, seleziona il **clienti** e **ordini** caselle di controllo e quindi scegliere il **Fine** pulsante.  
  
     Il dataset **SampleDatabaseDataSet** viene aggiunto al progetto e le tabelle **Customers** e **Orders** vengono visualizzate nella finestra **Origini dati**.  
  
##  <a name="BKMK_AddCtrls"></a> Aggiunta di controlli con associazione a dati  
  
#### Per aggiungere controlli con associazione a dati  
  
1.  Spostare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.  
  
     Sul form vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
2.  Per eseguire l'applicazione e visualizzare i dati aggiunti nella procedura dettagliata precedente, premere F5.  
  
3.  Scegliere l'icona di aggiunta gialla \(![Pulsante Aggiungi in Windows Form](../data-tools/media/addrecord.png "AddRecord")\), aggiungere un record cliente e quindi salvare le modifiche scegliendo l'icona del disco \(![Pulsante Salva in Windows Form](../data-tools/media/saveinwf.png "SaveInWF")\).  
  
4.  Per eliminare il record appena creato, selezionarlo e quindi scegliere l'icona di eliminazione rossa \(![Pulsante Elimina in Windows Form](../data-tools/media/deleterecord.png "DeleteRecord")\).  
  
## Passaggi successivi  
 È possibile creare o modificare gli oggetti nel dataset se si apre l'origine dati in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  È possibile inoltre aggiungere logica di convalida agli eventi <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> delle tabelle dati presenti nel dataset.  Vedere [Convalida dei dati nei dataset](../data-tools/validate-data-in-datasets.md).  
  
## Vedere anche  
 [Cenni preliminari sui dati locali](../data-tools/local-data-overview.md)   
 [Procedura: gestire file di dati locali nel progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)