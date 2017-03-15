---
title: "Procedura dettagliata: gestione di un&#39;eccezione di concorrenza | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "controllo della concorrenza, eccezioni"
  - "controllo della concorrenza, procedure dettagliate"
  - "concorrenza di dati, procedure dettagliate"
  - "dataset [Visual Basic], errori"
  - "gestione eccezioni, problemi di concorrenza"
  - "aggiornamento di dataset, errori"
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: gestione di un&#39;eccezione di concorrenza
Le eccezioni di concorrenza \(<xref:System.Data.DBConcurrencyException>\) vengono generate quando due utenti tentano di modificare gli stessi dati di un database contemporaneamente.  In questa procedura dettagliata verrà creata un'applicazione Windows che illustra l'intercettazione di un'eccezione <xref:System.Data.DBConcurrencyException> mediante l'individuazione della riga che ha causato l'errore e una strategia per la relativa gestione.  
  
 In questa procedura dettagliata vengono illustrati i seguenti passaggi:  
  
1.  Creazione di un nuovo progetto **Applicazione Windows**.  
  
2.  Creazione di un nuovo dataset basato sulla tabella Northwind `Customers`.  
  
3.  Creazione di un form contenente un oggetto <xref:System.Windows.Forms.DataGridView> per la visualizzazione dei dati.  
  
4.  Riempimento di un dataset con i dati contenuti nella tabella `Customers` del database Northwind.  
  
5.  Dopo aver compilato il dataset, utilizzo degli [Visual Database Tools](http://msdn.microsoft.com/it-it/6b145922-2f00-47db-befc-bf351b4809a1) in Visual Studio per accedere direttamente alla tabella di dati `Customers` e modificare un record.  
  
6.  Nel form, modifica del valore dello stesso record, aggiornamento del dataset e tentativo di scrivere le modifiche nel database con conseguente generazione di un errore di concorrenza.  
  
7.  Intercettazione dell'errore e successiva visualizzazione delle diverse versioni del record per consentire all'utente di scegliere se continuare e aggiornare il database oppure annullare l'aggiornamento.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario quanto segue:  
  
-   Accedere al database di esempio Northwind con l'autorizzazione per l'esecuzione degli aggiornamenti.  Per ulteriori informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Creazione di un nuovo progetto  
 La prima parte della procedura dettagliata consiste nella creazione di una nuova applicazione Windows.  
  
#### Per creare un nuovo progetto di applicazione Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Selezionare un linguaggio di programmazione nel riquadro **Tipi progetto**.  
  
3.  Selezionare **Applicazione Windows** nel riquadro **Modelli**.  
  
4.  Assegnare al progetto il nome `ConcurrencyWalkthrough`, quindi scegliere **OK**.  
  
     Il progetto verrà aggiunto a **Esplora soluzioni** e nella finestra di progettazione verrà visualizzato un nuovo form.  
  
## Creazione del dataset Northwind  
 In questa sezione verrà creato un dataset denominato `NorthwindDataSet`.  
  
#### Per creare il dataset NorthwindDataSet  
  
1.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
     Verrà visualizzata la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
2.  Selezionare **Database** nella pagina **Seleziona un tipo di origine dati**.  
  
3.  Selezionare una connessione al database di esempio Northwind dall'elenco delle connessioni disponibili oppure fare clic su **Nuova connessione** se la connessione non è disponibile nell'elenco delle connessioni.  
  
    > [!NOTE]
    >  Se si sta effettuando la connessione a un file del database locale, selezionare **No** quando viene chiesto se si desidera aggiungere il file al progetto.  
  
4.  Scegliere **Avanti** nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione**.  
  
5.  Espandere il nodo **Tabelle** e selezionare la tabella `Customers`.  Il nome predefinito del dataset dovrebbe essere `NorthwindDataSet`.  
  
6.  Scegliere **Fine** per aggiungere il dataset al progetto.  
  
## Creazione di un controllo DataGridView con associazione a dati  
 In questa sezione verrà creato un oggetto <xref:System.Windows.Forms.DataGridView> mediante il trascinamento dell'elemento **Customers** dalla finestra **Origini dati** sul Windows Form.  
  
#### Per creare un controllo DataGridView associato alla tabella Customers  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati** per aprire la finestra **Origini dati**.  
  
2.  Dalla finestra **Origini dati** espandere il nodo **NorthwindDataSet** e selezionare la tabella **Customers**.  
  
3.  Fare clic sulla freccia GIÙ sul nodo della tabella e selezionare **DataGridView** dall'elenco a discesa.  
  
4.  Trascinare la tabella in un'area vuota del form.  
  
     Al form associato all'oggetto <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato alla tabella `Customers` del dataset `NorthwindDataSet`, verranno aggiunti un controllo <xref:System.Windows.Forms.DataGridView> denominato `CustomersDataGridView` e un controllo <xref:System.Windows.Forms.BindingNavigator> denominato `CustomersBindingNavigator`.  
  
## Verifica  
 È ora possibile verificare il form per assicurarsi che funzioni come previsto fino a questo punto.  
  
#### Per eseguire il test del form  
  
1.  Premere F5 per eseguire l'applicazione.  
  
     Verrà visualizzato un form contenente un controllo <xref:System.Windows.Forms.DataGridView> compilato con dati provenienti dalla tabella `Customers`.  
  
2.  Scegliere **Termina debug** dal menu **Debug**.  
  
## Gestione degli errori di concorrenza  
 La gestione degli errori dipende dalle specifiche regole business che governano l'applicazione.  In questa procedura dettagliata, dopo che è stata generata una violazione di concorrenza, verrà utilizzata a scopo esemplificativo la strategia descritta di seguito per gestire l'errore di concorrenza.  
  
 Tramite l'applicazione verranno presentate all'utente tre versioni del record:  
  
-   Il record corrente nel database.  
  
-   Il record originale caricato nel dataset.  
  
-   Le modifiche proposte nel dataset.  
  
 L'utente sarà quindi in grado di sovrascrivere il database con la versione proposta oppure di annullare l'aggiornamento e aggiornare il dataset con i nuovi valori provenienti dal database.  
  
#### Per attivare la gestione degli errori di concorrenza  
  
1.  Creare un gestore errori personalizzato.  
  
2.  Visualizzare le opzioni all'utente.  
  
3.  Elaborare la risposta dell'utente.  
  
4.  Inviare nuovamente l'aggiornamento o reimpostare i dati nel dataset.  
  
### Aggiunta di codice per gestire le eccezioni di concorrenza  
 Quando viene generata un'eccezione in seguito a un tentativo di aggiornamento, generalmente si desidera rispondere all'eccezione utilizzando le informazioni da essa fornite.  
  
 In questa sezione verrà aggiunto del codice per tentare di aggiornare il database e di gestire qualsiasi eccezione <xref:System.Data.DBConcurrencyException> generata, come pure qualunque altra eccezione.  
  
> [!NOTE]
>  I metodi `CreateMessage` e `ProcessDialogResults` verranno aggiunti nei passaggi successivi della procedura dettagliata.  
  
##### Per aggiungere la gestione dell'errore di concorrenza  
  
1.  Aggiungere al metodo `Form1_Load` il seguente codice:  
  
     [!code-cs[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  Sostituire il metodo `CustomersBindingNavigatorSaveItem_Click` per chiamare il metodo `UpdateDatabase` in modo che rispecchi l'esempio seguente:  
  
     [!code-cs[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### Visualizzazione delle opzioni all'utente  
 Il codice sopra riportato consente di chiamare la routine `CreateMessage` per visualizzare all'utente le informazioni sull'errore.  Per questa procedura dettagliata verrà utilizzata una finestra di messaggio nella quale verranno visualizzate le diverse versioni del record, consentendo così all'utente di scegliere se sovrascrivere il record con le modifiche oppure annullare le modifiche apportate.  In seguito alla selezione di un'opzione \(mediante pressione di un pulsante\) nella finestra di messaggio, la risposta verrà passata al metodo `ProcessDialogResult`.  
  
##### Per creare il messaggio da visualizzare all'utente  
  
-   Creare il messaggio aggiungendo il codice che segue all'**editor di codice**.  Immettere questo codice sotto al metodo `UpdateDatabase`.  
  
     [!code-cs[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### Elaborazione della risposta dell'utente  
 Sarà inoltre necessario il codice per elaborare la risposta dell'utente alla finestra di messaggio.  L'utente potrà sovrascrivere il record corrente nel database con la modifica proposta o ignorare le modifiche locali e aggiornare la tabella dati con il record attualmente presente nel database.  Se l'utente sceglie sì, il metodo <xref:System.Data.DataTable.Merge%2A> viene chiamato con l'argomento *preserveChanges* impostato su `true`.  Di conseguenza l'aggiornamento verrà eseguito, poiché la versione originale del record corrisponderà ora al record del database.  
  
##### Per elaborare l'input dell'utente dalla finestra di messaggio  
  
-   Aggiungere il codice che segue al di sotto del codice aggiunto nella sezione precedente.  
  
     [!code-cs[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## Test  
 È ora possibile verificare il form per assicurarsi che funzioni correttamente.  Per simulare una violazione di concorrenza è necessario modificare i dati del database dopo aver riempito l'oggetto NorthwindDataSet.  
  
#### Per eseguire il test del form  
  
1.  Premere F5 per eseguire l'applicazione.  
  
2.  Una volta visualizzato il form, consentirne l'esecuzione e passare all'ambiente di sviluppo integrato \(IDE\) di Visual Studio.  
  
3.  Scegliere **Esplora server** dal menu **Visualizza**.  
  
4.  In **Esplora server** espandere la connessione utilizzata dall'applicazione, quindi il nodo **Tabelle**.  
  
5.  Fare clic con il pulsante destro del mouse sulla tabella **Customers** e selezionare **Mostra dati tabella**.  
  
6.  Nel primo record \(`ALFKI`\) modificare `ContactName` con `Maria Anders2`.  
  
    > [!NOTE]
    >  Passare a un'altra riga per eseguire il commit della modifica.  
  
7.  Passare al form in esecuzione del progetto `ConcurrencyWalkthrough`.  
  
8.  Nel primo record del form \(`ALFKI`\) modificare `ContactName` con `Maria Anders1`.  
  
9. Fare clic sul pulsante **Salva**.  
  
     Verrà generato l'errore di concorrenza e verrà visualizzata la finestra di messaggio.  
  
10. Se si sceglie **No** l'aggiornamento verrà annullato e il dataset verrà aggiornato con i valori correntemente presenti nel database, mentre se si sceglie **Sì** il valore proposto verrà scritto nel database.  
  
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