---
title: "Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l&#39;associazione dati di ricerca | Microsoft Docs"
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
  - "associazione dati, controlli utente"
  - "LookupBindingPropertiesAttribute (classe), esempi"
  - "controlli utente [Visual Basic], creazione"
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l&#39;associazione dati di ricerca
Quando si visualizzano dati nei Windows Form, è possibile scegliere i controlli esistenti dalla Casella degli strumenti o creare controlli personalizzati se l'applicazione richiede funzionalità che non sono disponibili nei controlli standard.  In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  I controlli che implementano <xref:System.ComponentModel.LookupBindingPropertiesAttribute> possono contenere tre proprietà associabili ai dati.  Tali controlli sono simili a <xref:System.Windows.Forms.ComboBox>.  
  
 Per altre informazioni sulla creazione di controlli, vedere [Sviluppo di controlli Windows Form in fase di progettazione](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:  
  
|Uso degli attributi di data binding|  
|-----------------------------------------|  
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati.  Per altre informazioni, vedere [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati.  Per altre informazioni, vedere [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà.  Il processo è descritto in questa pagina di procedura dettagliata.|  
  
 Questa procedura dettagliata crea un controllo di ricerca che effettua l'associazione ai dati di due tabelle.  Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.  Il controllo di ricerca verrà associato al campo `CustomerID` dalla tabella `Orders`.  Userà questo valore per eseguire la ricerca di `CompanyName` dalla tabella `Customers`.  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Creare una nuova **applicazione Windows**.  
  
-   Aggiungere un nuovo **controllo utente** al progetto.  
  
-   Progettare visivamente il controllo utente.  
  
-   Implementare l'attributo `LookupBindingProperty`.  
  
-   Creare un dataset con [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Impostare la colonna **CustomerID** nella tabella **Orders** della finestra **Origini dati** per usare il nuovo controllo.  
  
-   Creare un form per visualizzare i dati nel controllo.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione di un'applicazione Windows  
 Il primo passaggio consiste nella creazione di un'**applicazione Windows**.  
  
#### Per creare il nuovo progetto Windows  
  
1.  In Visual Studio creare un nuovo **Progetto** dal menu **File**.  
  
2.  Assegnare al progetto il nome LookupControlWalkthrough.  
  
3.  Selezionare **Applicazione Windows** e fare clic su **OK**.  Per altre informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **LookupControlWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.  
  
## Aggiunta di un controllo utente al progetto  
 Dal momento che questa procedura dettagliata crea un controllo di ricerca da un **Controllo utente**, è necessario aggiungere un elemento **Controllo utente** al progetto **LookupControlWalkthrough**.  
  
#### Per aggiungere un controllo utente al progetto  
  
1.  Selezionare **Aggiungi controllo utente** dal menu **Progetto**.  
  
2.  Digitare `LookupBox` nell'area **Nome**, quindi fare clic su **Aggiungi**.  
  
     Il controllo **LookupBox** viene aggiunto a **Esplora soluzioni** e si apre nella finestra di progettazione.  
  
## Progettazione del controllo LookupBox  
  
#### Per progettare il controllo LookupBox  
  
-   Trascinare un oggetto <xref:System.Windows.Forms.ComboBox> dalla **Casella degli strumenti** nell'area di progettazione del controllo utente.  
  
## Aggiunta dell'attributo di data binding richiesto  
 Per controlli di ricerca che supportano il data binding, è possibile implementare l'attributo <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### Per implementare l'attributo LookupBindingProperties  
  
1.  Passare al controllo **LookupBox** per la visualizzazione del codice.  Scegliere **Codice** dal menu **Visualizza**.  
  
2.  Sostituire il codice nel controllo `LookupBox` con la stringa seguente:  
  
     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-cs[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]  
  
3.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
## Creazione di un'origine dati dal database  
 Questo passaggio crea un'origine dati usando la **Configurazione guidata origine dati** basata sulle tabelle `Customers` e `Orders` nel database di esempio Northwind.  Per creare la connessione, è necessario avere accesso al database di esempio Northwind.  Per informazioni sull'impostazione del database di esempio Northwind, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
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
  
8.  Selezionare le tabelle `Customers` e `Orders`, quindi fare clic su **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle `Customers` e `Orders` vengono visualizzate nella finestra **Origini dati**.  
  
## Impostazione della colonna CustomerID della tabella Orders per usare il controllo LookupBox  
 Nella finestra **Origini dati** è possibile impostare il controllo da creare prima di trascinare elementi nel form.  
  
#### Per impostare la colonna CustomerID da associare al controllo LookupBox  
  
1.  Aprire **Form1** nella finestra di progettazione.  
  
2.  Espandere il nodo **Customers** nella finestra **Origini dati**.  
  
3.  Espandere il nodo **Orders** \(nel nodo **Customers** sotto la colonna **Fax**\).  
  
4.  Fare clic sulla freccia a discesa nel nodo **Orders** e scegliere **Dettagli** dall'elenco di controllo.  
  
5.  Fare clic sulla freccia a discesa nella colonna **CustomerID** \(nel nodo **Orders**\) e scegliere **Personalizza**.  
  
6.  Selezionare **LookupBox** dall'elenco **Controlli associati** nella finestra di dialogo **Personalizzazione dell'interfaccia utente dati**.  
  
7.  Fare clic su **OK**.  
  
8.  Fare clic sulla freccia a discesa nella colonna **CustomerID** e scegliere **LookupBox**.  
  
## Aggiunta di controlli al form  
 È possibile creare i controlli associati ai dati trascinando elementi dalla finestra **Origini dati** in **Form1**.  
  
#### Per creare controlli associati ai dati nel Windows Form  
  
-   Trascinare il nodo **Orders** dalla finestra **Origini dati** nel Windows Form e verificare che il controllo **LookupBox** venga usato per visualizzare i dati nella colonna `CustomerID`.  
  
## Associazione del controllo per eseguire la ricerca di CompanyName dalla tabella Customers  
  
#### Per impostare le associazioni di ricerca  
  
-   Selezionare il nodo **Customers** principale nella finestra **Origini dati** e trascinarlo nella casella combinata **CustomerIDLookupBox** in **Form1**.  
  
     Viene in questo modo impostato il data binding per visualizzare `CompanyName` dalla tabella `Customers`, mantenendo al contempo il valore `CustomerID` della tabella `Orders`.  Per altre informazioni, vedere [Procedura: creare tabelle di ricerca nelle applicazioni Windows Form](../data-tools/create-lookup-tables-in-windows-forms-applications.md).  
  
## Esecuzione dell'applicazione  
  
#### Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
-   Spostarsi all'interno di alcuni record e verificare che `CompanyName` venga mostrato nel controllo `LookupBox`.  
  
## Vedere anche  
 [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)