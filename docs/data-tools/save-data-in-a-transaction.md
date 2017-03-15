---
title: "Procedura dettagliata: salvataggio di dati in una transazione | Microsoft Docs"
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
  - "dati [Visual Studio], salvataggio in una transazione"
  - "salvataggio di dati"
  - "System.Transactions (spazio dei nomi)"
  - "Transactions (spazio dei nomi)"
  - "transazioni, salvataggio di dati"
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: salvataggio di dati in una transazione
Questa procedura dettagliata illustra come salvare dati in una transazione usando lo spazio dei nomi <xref:System.Transactions>.  Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.  
  
## Prerequisiti  
 La procedura dettagliata richiede l'accesso al database di esempio Northwind.  Per informazioni sull'impostazione del database di esempio Northwind, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione di un'applicazione Windows  
 Il primo passaggio consiste nella creazione di un'**applicazione Windows**.  
  
#### Per creare il nuovo progetto Windows  
  
1.  In Visual Studio creare un nuovo **Progetto** dal menu **File**.  
  
2.  Assegnare al progetto il nome SavingDataInATransactionWalkthrough.  
  
3.  Selezionare **Applicazione Windows** e fare clic su **OK**.  Per altre informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **SavingDataInATransactionWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.  
  
## Creazione di un'origine dati del database  
 In questo passaggio viene usata la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) per creare un'origine dati basata sulle tabelle `Customers` e `Orders` del database di esempio Northwind.  
  
#### Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         \-oppure\-  
  
    -   Selezionare **Nuova connessione** per avviare la finestra di dialogo **Aggiungi\/Modifica connessione** e creare una connessione al database Northwind.  
  
5.  Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati riservati, quindi scegliere **Avanti**.  
  
6.  Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti**.  
  
7.  Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.  
  
8.  Selezionare le tabelle `Customers` e `Orders`, quindi fare clic su **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle `Customers` e `Orders` vengono visualizzate nella finestra **Origini dati**.  
  
## Aggiunta di controlli al form  
 È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.  
  
#### Per creare controlli associati a dati nel Windows Form  
  
-   Espandere il nodo **Customers** nella finestra **Origini dati**.  
  
-   Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.  
  
     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
-   Trascinare il nodo **Orders** correlato \(il nodo della tabella figlio correlato al di sotto della colonna **Fax**, non il nodo **Orders** principale\) nel form sotto l'oggetto **CustomersDataGridView**.  
  
     Nel form verrà visualizzato un oggetto <xref:System.Windows.Forms.DataGridView>.  Nella barra dei componenti vengono visualizzati gli oggetti [OrdersTableAdapter](../data-tools/tableadapter-overview.md) e <xref:System.Windows.Forms.BindingSource>.  
  
## Aggiunta di un riferimento all'assembly System.Transactions  
 Le transazioni usano lo spazio dei nomi <xref:System.Transactions>.  Un riferimento di progetto all'assembly system.transactions non viene aggiunto per impostazione predefinita. Pertanto, è necessario aggiungerlo manualmente.  
  
#### Per aggiungere un riferimento al file DLL System.Transactions.  
  
1.  Dal menu **Progetto**  scegliere **Aggiungi riferimento**.  
  
2.  Selezionare **System.Transactions** \(nella scheda **.NET**\) e fare clic su **OK**.  
  
     Al progetto viene aggiunto un riferimento a **System.Transactions**.  
  
## Modifica del codice nel pulsante SaveItem di BindingNavigator  
 Per impostazione predefinita, per la prima tabella rilasciata nel form, viene aggiunto il codice all'evento `click` del pulsante di salvataggio nell'oggetto <xref:System.Windows.Forms.BindingNavigator>.  È necessario aggiungere manualmente il codice per aggiornare eventuali tabelle aggiuntive.  Per questa procedura dettagliata, è stato effettuato il refactoring del codice di salvataggio del gestore eventi Click del pulsante di salvataggio e sono stati creati altri metodi per fornire una funzionalità di aggiornamento specifica a seconda dell'esigenza di eliminare o aggiungere una riga.  
  
#### Per modificare il codice di salvataggio autogenerato  
  
1.  Fare doppio clic sul pulsante **Salva** nell'oggetto **CustomersBindingNavigator** \(il pulsante con l'icona del disco floppy\).  
  
2.  Sostituire il metodo `CustomersBindingNavigatorSaveItem_Click` con il codice seguente:  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
 L'ordine di riconciliazione delle modifiche ai dati correlati è il seguente:  
  
-   Eliminare i record figlio \(in questo caso, eliminare i record dalla tabella `Orders`\)  
  
-   Eliminare i record padre \(in questo caso, eliminare i record dalla tabella `Customers`\)  
  
-   Inserire i record padre \(in questo caso, inserire i record nella tabella `Customers`\)  
  
-   Inserire i record figlio \(in questo caso, inserire i record nella tabella `Orders`\)  
  
#### Per eliminare gli ordini esistenti  
  
-   Aggiungere il metodo `DeleteOrders` seguente in **Form1**:  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-cs[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### Per eliminare i clienti esistenti  
  
-   Aggiungere il metodo `DeleteCustomers` seguente in **Form1**:  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-cs[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### Per aggiungere nuovi clienti  
  
-   Aggiungere il metodo `AddNewCustomers` seguente in **Form1**:  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-cs[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### Per aggiungere nuovi ordini  
  
-   Aggiungere il metodo `AddNewOrders` seguente in **Form1**:  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-cs[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## Esecuzione dell'applicazione  
  
#### Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
## Vedere anche  
 [Transazioni e concorrenza](../Topic/Transactions%20and%20Concurrency.md)   
 [Transazioni distribuite Oracle](../Topic/Oracle%20Distributed%20Transactions.md)   
 [Procedura: salvare dati utilizzando una transazione](../data-tools/save-data-by-using-a-transaction.md)   
 [Integrazione di System.Transactions con SQL Server](../Topic/System.Transactions%20Integration%20with%20SQL%20Server.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)