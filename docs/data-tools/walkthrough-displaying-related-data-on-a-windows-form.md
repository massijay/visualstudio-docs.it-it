---
title: "Procedura dettagliata: visualizzazione di dati correlati in un Windows Form | Microsoft Docs"
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
  - "dati [Visual Studio], visualizzazione su Windows Form"
  - "dati [Visual Studio], master-dettagli"
  - "visualizzazione di dati su form, procedure dettagliate"
  - "visualizzazione di dati di tabelle"
  - "visualizzazione di informazioni di tabelle"
  - "visualizzazione di tabelle, dati correlati"
  - "Master-Details (elenchi), visualizzazione su Windows Form"
  - "Windows Form, visualizzazione di dati"
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura dettagliata: visualizzazione di dati correlati in un Windows Form
In molti scenari di applicazioni può essere necessario usare dati provenienti da più tabelle, spesso anche correlate,  ovvero usare relazioni padre\-figlio.  Può ad esempio essere necessario creare un form in cui la selezione del record di un cliente determini la visualizzazione degli ordini relativi.  Per visualizzare i record correlati nel form è necessario impostare la proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> dell'oggetto figlio <xref:System.Windows.Forms.BindingSource> sull'oggetto <xref:System.Windows.Forms.BindingSource> \(non sulla tabella figlio\) e impostare la proprietà <xref:System.Windows.Forms.BindingSource.DataMember%2A> dell'oggetto figlio <xref:System.Windows.Forms.BindingSource> sulla relazione dati che collega le tabelle padre e figlio.  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un progetto **Applicazione Windows**.  
  
-   Creazione e configurazione di un set di dati nell'applicazione in base alle tabelle `Customers` e `Orders` del database Northwind mediante la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Aggiunta di controlli per visualizzare i dati della tabella `Customers`.  
  
-   Aggiunta di controlli per visualizzare le voci della tabella `Orders` in base al `Customer` selezionato.  
  
-   Test dell'applicazione selezionando diversi clienti e verificando che vengano visualizzati gli ordini corretti per il cliente selezionato.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  Per installare database di esempio, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione del progetto  
 Il primo passaggio consiste nella creazione di un'**applicazione Windows**.  
  
#### Per creare il progetto Applicazione Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Assegnare al progetto il nome `RelatedDataWalkthrough`.  
  
3.  Selezionare **Applicazione Windows** e fare clic su **OK**.  Per altre informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **RelatedDataWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.  
  
## Creazione dell'origine dati  
 In questo passaggio viene creato un set di dati in base alle tabelle `Customers` e `Orders` del database di esempio Northwind.  
  
#### Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         \-oppure\-  
  
    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi\/Modifica connessione**.  
  
5.  Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati riservati, quindi scegliere **Avanti**.  
  
6.  Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti**.  
  
7.  Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.  
  
8.  Selezionare le tabelle **Customers** e **Orders**, quindi scegliere **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella **Customers** viene visualizzata nella finestra **Origini dati**.  
  
## Creazione di controlli per visualizzare i dati della tabella Customers  
  
#### Per creare controlli che consentano di visualizzare i dati del cliente \(record padre\)  
  
1.  Nella finestra **Origini dati** selezionare la tabella **Customers**, quindi fare clic sulla freccia a discesa.  
  
2.  Scegliere **Dettagli** dal menu.  
  
3.  Trascinare il nodo **Customers** principale dalla finestra **Origini dati** alla parte superiore del **Form1**.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
## Creazione di controlli per visualizzare i dati della tabella Orders  
 ![Finestra Origini dati con visualizzazione delle relazioni](~/docs/data-tools/media/datasources2.gif "DataSources2")  
  
#### Per creare controlli che consentano di visualizzare gli ordini di ciascun cliente \(record figlio\)  
  
-   Nella finestra **Origini dati** espandere il nodo **Customers** e selezionare l'ultima colonna della tabella **Customers**, che rappresenta un nodo **Orders** espandibile, e trascinarlo nella parte superiore di **Form1**.  
  
     Al form viene aggiunto un oggetto <xref:System.Windows.Forms.DataGridView> e alla barra dei componenti vengono aggiunti un nuovo oggetto <xref:System.Windows.Forms.BindingSource> \(`OrdersBindingSource`\) e un TableAdapter \(`OrdersTableAdapter`\).  
  
    > [!NOTE]
    >  Aprire la [Finestra Proprietà](../ide/reference/properties-window.md) e selezionare **OrdersBindingSource**.  Esaminare le proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> per stabilire come è configurata l'associazione per la visualizzazione dei record correlati.  La proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> è impostata su `CustomersBindingSource` \(elemento <xref:System.Windows.Forms.BindingSource> della tabella padre\), anziché sulla tabella `Orders`.  La proprietà <xref:System.Windows.Forms.BindingSource.DataMember%2A> è impostata su `FK_Orders_Customers`, ovvero il nome dell'oggetto <xref:System.Data.DataRelation> che mette in correlazione tra loro le tabelle.  
  
## Verifica dell'applicazione  
  
#### Per eseguire il test dell'applicazione  
  
1.  Premere F5 per eseguire l'applicazione.  
  
2.  Selezionare diversi clienti mediante **CustomersBindingNavigator** per verificare che in <xref:System.Windows.Forms.DataGridView> vengano visualizzati gli ordini corretti.  
  
## Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un form master\-dettagli.  È possibile apportare un miglioramento a questa procedura dettagliata, ovvero:  
  
-   Filtrare i record `Customers` aggiungendo la parametrizzazione alla tabella `Customers`.  A questo scopo, selezionare un controllo che visualizza i dati della tabella `Customers`, fare clic sullo smart tag e scegliere **Aggiungi query**.  Completare la [Finestra di dialogo Generatore di criteri per la ricerca](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  Per altre informazioni, vedere [Procedura: aggiungere una query con parametri a un'applicazione Windows Form](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: visualizzare dati correlati in un'applicazione Windows Form](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [Cenni preliminari sul componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)   
 [Cenni preliminari sul controllo BindingNavigator](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)