---
title: "Procedura dettagliata: creazione di un dataset con Progettazione DataSet | Microsoft Docs"
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
  - "Progettazione DataSet, procedure dettagliate"
  - "dataset [Visual Basic], creazione"
  - "dataset [Visual Basic], procedure dettagliate"
  - "XML Schema, creazione di dataset"
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura dettagliata: creazione di un dataset con Progettazione DataSet
In questa procedura dettagliata verrà creato un dataset mediante **Progettazione DataSet**.  Verrà illustrato il processo di creazione di un nuovo progetto e di aggiunta di un nuovo elemento **DataSet** al progetto.  Verranno fornite informazioni sulle modalità di creazione di tabelle in base alle tabelle di un database senza l'utilizzo di una procedura guidata.  
  
 Di seguito vengono elencate le attività illustrate nella procedura dettagliata:  
  
-   Creazione di un nuovo progetto **Applicazione Windows**.  
  
-   Aggiunta di un elemento **DataSet** vuoto al progetto.  
  
-   Creazione e configurazione di un'origine dati nell'applicazione compilando un dataset con **Progettazione DataSet**.  
  
-   Creazione di una connessione al database Northwind in **Esplora server**.  
  
-   Creazione di tabelle con oggetti TableAdapter nel dataset in base alle tabelle del database.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario quanto segue:  
  
-   Accedere al database di esempio Northwind nella versione SQL Server o Access.  Per ulteriori informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione di un nuovo progetto di applicazione Windows  
  
#### Per creare un nuovo progetto di applicazione Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Scegliere un linguaggio di programmazione nel riquadro **Tipi progetto**.  
  
3.  Selezionare **Applicazione Windows** nel riquadro **Modelli**.  
  
4.  Assegnare al progetto il nome `DatasetDesignerWalkthrough`, quindi scegliere **OK**.  
  
     Il progetto verrà aggiunto a **Esplora soluzioni** e nella finestra di progettazione verrà visualizzato un nuovo form.  
  
## Aggiunta di un nuovo dataset all'applicazione  
  
#### Per aggiungere un nuovo elemento dataset al progetto  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Nella casella **Modelli** della finestra di dialogo **Aggiungi nuovo elemento** fare clic su **DataSet**.  
  
3.  Assegnare al dataset il nome `NorthwindDataset`, quindi scegliere **Aggiungi**.  
  
     Al progetto verrà aggiunto un file denominato **NorthwindDataset.xsd** che verrà aperto in **Progettazione DataSet**.  
  
## Creazione di una connessione dati in Esplora server  
  
#### Per creare una connessione al database Northwind  
  
1.  Scegliere **Esplora server** dal menu **Visualizza**.  
  
2.  In **Esplora server** fare clic sul pulsante **Connetti al database**.  
  
3.  Creare una connessione al database di esempio Northwind.  
  
    > [!NOTE]
    >  Per questa procedura dettagliata è possibile effettuare la connessione alla versione SQL Server o Access di Northwind.  
  
## Creazione delle tabelle nel dataset  
 In questa sezione verrà illustrato come aggiungere tabelle al dataset.  
  
#### Per creare la tabella Customers  
  
1.  Espandere la connessione dati creata in **Esplora server**, quindi espandere il nodo **Tabelle**.  
  
2.  Trascinare la tabella **Customers** da **Esplora server** in **Progettazione DataSet**.  
  
     Al dataset vengono aggiunti una tabella di dati **Customers** e un oggetto **CustomersTableAdapter**.  
  
#### Per creare la tabella Orders  
  
-   Trascinare la tabella **Orders** da **Esplora server** in **Progettazione DataSet**.  
  
     Al dataset vengono aggiunti una tabella dati **Orders**, un **OrdersTableAdapter** e una relazione dati tra le tabelle **Customers** e **Orders**.  
  
#### Per creare la tabella OrderDetails  
  
-   Trascinare la tabella **Order Details** da **Esplora server** in **Progettazione DataSet**.  
  
     Al dataset vengono aggiunti una tabella di dati **Order Details**, un oggetto **Order DetailsTableAdapter** e una relazione dati tra le tabelle **Orders** e **Order Details**.  
  
## Passaggi successivi  
  
### Per aggiungere funzionalità all'applicazione  
  
-   Salvare il dataset.  
  
-   Selezionare gli elementi nella finestra **Origini dati** e trascinarli in un form.  Per ulteriori informazioni, vedere [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Aggiungere altre query ai TableAdapter.  Per ulteriori informazioni, vedere [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Aggiungere logica di convalida agli eventi <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> delle tabelle dati nel dataset.  Per ulteriori informazioni, vedere [Convalida dei dati nei dataset](../data-tools/validate-data-in-datasets.md).  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)