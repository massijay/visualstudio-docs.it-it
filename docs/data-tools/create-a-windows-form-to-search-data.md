---
title: "Procedura: creazione di un Windows Form per la ricerca di dati | Microsoft Docs"
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
  - "dati [Visual Studio], parametrizzazione di query"
  - "dati [Visual Studio], ricerca"
  - "parametri, visualizzazione di dati filtrati"
  - "Windows Form, visualizzazione di dati"
  - "Windows Form, ricerca di dati"
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 28
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: creazione di un Windows Form per la ricerca di dati
Uno scenario applicativo comune prevede la visualizzazione dei dati selezionati in un form,  ad esempio gli ordini per un determinato cliente o i dettagli di un ordine specifico.  In questo scenario un utente immette informazioni in un form, quindi viene eseguita una query che usa come parametro l'input dell'utente. Questo significa che i dati vengono selezionati in base a una query con parametri.  La query restituisce solo i dati che soddisfano i criteri immessi dall'utente.  Questa procedura dettagliata illustra come creare una query che restituisca i clienti di una determinata città e come modificare l'interfaccia utente in modo che gli utenti possano immettere il nome di una città e fare clic su un pulsante per eseguire la query.  
  
 L'uso di query con parametri rende più efficiente il funzionamento dell'applicazione, consentendo al database di eseguire in modo ottimale le operazioni di filtro rapido dei record.  La richiesta invece di un'intera tabella del database, il relativo trasferimento in rete e l'uso della logica dell'applicazione per trovare i record desiderati possono comportare una riduzione della velocità e dell'efficienza dell'applicazione.  
  
 È possibile aggiungere query con parametri a qualsiasi oggetto TableAdapter \(e controlli in modo che vengano accettati valori di parametri e venga eseguita la query\) mediante la [Finestra di dialogo Generatore di criteri per la ricerca](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  Per aprire la finestra di dialogo, scegliere **Aggiungi query** nel menu **Dati** o da qualsiasi smart tag di TableAdapter.  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un nuovo progetto **Applicazione Windows**.  
  
-   Creazione e configurazione dell'origine dati nell'applicazione con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Impostazione del tipo di visualizzazione degli elementi nella [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creazione di controlli per la visualizzazione dei dati mediante il trascinamento di elementi dalla finestra **Origini dati** in un form.  
  
-   Aggiunta di controlli per la visualizzazione dei dati nel form.  
  
-   Inserimento dei dati mancanti nella [Finestra di dialogo Generatore di criteri per la ricerca](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
-   Immissione dei parametri nel form ed esecuzione della query con parametri.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione dell'applicazione Windows  
 Il primo passaggio consiste nella creazione di un'**applicazione Windows**.  L'assegnazione di un nome al progetto è facoltativa in questo passaggio, ma al progetto verrà ugualmente assegnato un nome per poterlo salvare in seguito.  
  
#### Per creare il nuovo progetto Applicazione Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Assegnare al progetto il nome `WindowsSearchForm`.  
  
3.  Selezionare **Applicazione Windows** e fare clic su **OK**.  Per altre informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **WindowsSearchForm** viene creato e aggiunto a **Esplora soluzioni**.  
  
## Creazione dell'origine dati  
 Questo passaggio consente di creare un'origine dati da un database usando la **Configurazione guidata origine dati**.  Per creare la connessione, è necessario avere accesso al database di esempio Northwind.  Per informazioni sull'impostazione del database di esempio Northwind, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
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
  
8.  Selezionare la tabella **Customers**, quindi fare clic su **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella **Customers** viene visualizzata nella finestra **Origini dati**.  
  
## Creazione del form  
 È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.  
  
#### Per creare controlli associati a dati nel form  
  
1.  Espandere il nodo **Customers** nella finestra **Origini dati**.  
  
2.  Trascinare il nodo **Customers** dalla finestra **Origini dati** al form.  
  
     Sul form vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
## Aggiunta della parametrizzazione \(funzionalità di ricerca\) alla query  
 È possibile aggiungere una clausola WHERE alla query originale usando la [Finestra di dialogo Generatore di criteri per la ricerca](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
#### Per creare una query con parametri e controlli per l'immissione dei parametri  
  
1.  Selezionare il controllo <xref:System.Windows.Forms.DataGridView> e quindi scegliere **Aggiungi query** dal menu **Dati**.  
  
2.  Digitare `FillByCity` nell'area **Nuovo nome query** della [Finestra di dialogo Generatore di criteri per la ricerca](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
3.  Aggiungere `WHERE City = @City` alla query nell'area **Testo della query**.  
  
     La query dovrebbe essere simile alla seguente:  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Nelle origini dati Access e OleDb viene usato il punto interrogativo \(?\) per indicare i parametri, quindi la clausola WHERE risulterebbe simile a `WHERE City = ?`.  
  
4.  Fare clic su **OK** per chiudere la finestra di dialogo **Generatore di criteri per la ricerca**.  
  
     Al form viene aggiunto un elemento **FillByCityToolStrip**.  
  
## Verifica dell'applicazione  
 Quando l'applicazione viene eseguita, il form viene aperto ed è pronto ad accettare il parametro come input.  
  
#### Per eseguire il test dell'applicazione  
  
1.  Premere F5 per eseguire l'applicazione.  
  
2.  Digitare London nella casella di testo **City**, quindi fare clic su **FillByCity**.  
  
     La griglia dei dati viene popolata con i clienti che soddisfano i criteri di parametrizzazione.  In questo esempio nella griglia dei dati vengono visualizzati solo i clienti nella cui colonna **City** è presente un valore **London**.  
  
## Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un form con parametri.  È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Aggiunta di controlli per la visualizzazione di dati correlati.  Per altre informazioni, vedere [Procedura: visualizzare dati correlati in un'applicazione Windows Form](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
-   Modifica del set di dati per aggiungere o rimuovere oggetti di database.  Per altre informazioni, vedere [Procedura: modificare un dataset](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cenni preliminari sul componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)   
 [Cenni preliminari sul controllo BindingNavigator](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)