---
title: "Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l&#39;associazione dati semplice | Microsoft Docs"
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
  - "controlli personalizzati [Visual Studio], Origini dati (finestra)"
  - "Origini dati (finestra), controlli"
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l&#39;associazione dati semplice
Quando si visualizzano dati nei form delle applicazioni Windows, è possibile scegliere i controlli esistenti dalla **Casella degli strumenti** o creare controlli personalizzati se l'applicazione richiede funzionalità che non sono disponibili nei controlli standard.  In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  I controlli che implementano <xref:System.ComponentModel.DefaultBindingPropertyAttribute> possono contenere una proprietà associabile ai dati.  Tali controlli sono simili a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.  
  
 Per altre informazioni sulla creazione di controlli, vedere [Sviluppo di controlli Windows Form in fase di progettazione](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:  
  
|Uso degli attributi di data binding|  
|-----------------------------------------|  
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati.  Il processo è descritto in questa pagina di procedura dettagliata.|  
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati.  Per altre informazioni, vedere [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà.  Per altre informazioni, vedere [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Questa procedura dettagliata crea un controllo semplice che visualizza i dati di una singola colonna in una tabella.  Questo esempio usa la colonna `Phone` della tabella `Customers` del database di esempio Northwind.  Il controllo utente semplice visualizzerà il numero di telefono del cliente in un formato telefonico standard usando <xref:System.Windows.Forms.MaskedTextBox> e impostando la maschera su un numero di telefono.  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Creare una nuova **applicazione Windows**.  
  
-   Aggiungere un nuovo **controllo utente** al progetto.  
  
-   Progettare visivamente il controllo utente.  
  
-   Implementare l'attributo `DefaultBindingProperty`.  
  
-   Creare un dataset con [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Impostare la colonna **Telefono** nella finestra **Origini dati** per usare il nuovo controllo.  
  
-   Creare un form per visualizzare i dati nel controllo.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione di un'applicazione Windows  
 Il primo passaggio consiste nella creazione di un'**applicazione Windows**.  
  
#### Per creare il nuovo progetto Windows  
  
1.  In Visual Studio creare un nuovo **Progetto** dal menu **File**.  
  
2.  Assegnare al progetto il nome **SimpleControlWalkthrough**.  
  
3.  Selezionare **Applicazione Windows** e fare clic su **OK**.  Per altre informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **SimpleControlWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.  
  
## Aggiunta di un controllo utente al progetto  
 Dal momento che questa procedura dettagliata crea un controllo di data binding semplice da un **Controllo utente**, è necessario aggiungere un elemento **Controllo utente** al progetto **SimpleControlWalkthrough**.  
  
#### Per aggiungere un controllo utente al progetto  
  
1.  Scegliere **Aggiungi controllo utente** dal menu **Progetto** .  
  
2.  Digitare `PhoneNumberBox` nell'area Nome, quindi scegliere **Aggiungi**.  
  
     Il controllo **PhoneNumberBox** viene aggiunto a **Esplora soluzioni** e si apre nella finestra di progettazione.  
  
## Progettazione del controllo PhoneNumberBox  
 Questa procedura dettagliata estende l'oggetto <xref:System.Windows.Forms.MaskedTextBox> per creare il controllo `PhoneNumberBox`.  
  
#### Per progettare il controllo PhoneNumberBox  
  
1.  Trascinare un oggetto <xref:System.Windows.Forms.MaskedTextBox> dalla **Casella degli strumenti** nell'area di progettazione del controllo utente.  
  
2.  Selezionare lo smart tag sull'oggetto <xref:System.Windows.Forms.MaskedTextBox> appena trascinato e scegliere **Imposta maschera**.  
  
3.  Selezionare **Numero di telefono** nella finestra di dialogo **Maschera input** e fare clic su **OK** per impostare la maschera.  
  
## Aggiunta dell'attributo di data binding richiesto  
 Per controlli semplici che supportano il data binding, implementare l'attributo <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### Per implementare l'attributo DefaultBindingProperty  
  
1.  Passare al controllo `PhoneNumberBox` per la visualizzazione del codice.  Scegliere **Codice** dal menu **Visualizza**.  
  
2.  Sostituire il codice nel controllo `PhoneNumberBox` con la stringa seguente:  
  
     [!code-cs[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
## Creazione di un'origine dati dal database  
 Questo passaggio usa la **Configurazione guidata origine dati** per creare un'origine dati basata sulla tabella `Customers` contenuta nel database di esempio Northwind.  Per creare la connessione, è necessario avere accesso al database di esempio Northwind.  Per informazioni sull'impostazione del database di esempio Northwind, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         Oppure  
  
    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi\/Modifica connessione**.  
  
5.  Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati riservati, quindi scegliere **Avanti**.  
  
6.  Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti**.  
  
7.  Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.  
  
8.  Selezionare la tabella `Customers`, quindi fare clic su **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella `Customers` viene visualizzata nella finestra **Origini dati**.  
  
## Impostazione della colonna Telefono per usare il controllo PhoneNumberBox  
 Nella finestra **Origini dati** è possibile impostare il controllo da creare prima di trascinare elementi nel form.  
  
#### Per impostare la colonna Telefono allo scopo di eseguire l'associazione al controllo PhoneNumberBox  
  
1.  Aprire **Form1** nella finestra di progettazione.  
  
2.  Espandere il nodo **Customers** nella finestra **Origini dati**.  
  
3.  Fare clic sulla freccia a discesa nel nodo **Customers** e scegliere **Dettagli** dall'elenco di controllo.  
  
4.  Fare clic sulla freccia a discesa nella colonna **Telefono** e scegliere **Personalizza**.  
  
5.  Selezionare **PhoneNumberBox** dall'elenco **Controlli associati** nella finestra di dialogo **Personalizzazione dell'interfaccia utente dati**.  
  
6.  Fare clic sulla freccia a discesa nella colonna **Telefono** e scegliere **PhoneNumberBox**.  
  
## Aggiunta di controlli al form  
 È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.  
  
#### Per creare controlli associati a dati nel form  
  
-   Trascinare il nodo **Customers** principale dalla finestra **Origini dati** nel form e verificare che il controllo `PhoneNumberBox` sia usato per visualizzare i dati nella colonna `Phone`.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
## Esecuzione dell'applicazione  
  
#### Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
## Passaggi successivi  
 A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni.  Ecco alcuni dei passaggi più comuni:  
  
-   Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.  
  
-   Creazione di controlli che supportano scenari di associazioni di dati più complessi.  Per altre informazioni, vedere [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## Vedere anche  
 [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)