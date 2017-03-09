---
title: "Procedura dettagliata: visualizzazione di dati in un Windows Form | Microsoft Docs"
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
  - "associazione dati, Windows Form"
  - "visualizzazione di dati su form, procedure dettagliate"
  - "form, visualizzazione di dati"
  - "Windows (applicazioni), visualizzazione di dati"
  - "Windows Form, visualizzazione di dati"
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura dettagliata: visualizzazione di dati in un Windows Form
Uno degli scenari più comuni nello sviluppo delle applicazioni è la visualizzazione dei dati di un form in un'applicazione per Windows.  Per visualizzare dati in un form è possibile trascinare gli elementi dalla [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md) nel form.  Questa procedura dettagliata consente di creare un form semplice in cui vengono visualizzati i dati di una tabella in più controlli.  In questo esempio viene usata la tabella `Customers` del database di esempio Northwind.  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un nuovo progetto **Applicazione Windows**.  
  
-   Creazione e configurazione di un set di dati con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Selezione del controllo da creare nel form durante il trascinamento di elementi dalla finestra **Origini dati**.  Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creazione di un controllo associato a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** nel form.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione dell'applicazione Windows  
 Il primo passaggio consiste nella creazione di un progetto **Applicazione Windows**.  
  
#### Per creare il nuovo progetto Applicazione Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Assegnare al progetto il nome `DisplayingDataonaWindowsForm`.  
  
3.  Selezionare **Applicazione Windows** e fare clic su **OK**.  Per altre informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **DisplayingDataonaWindowsForm** verrà creato e aggiunto a **Esplora soluzioni**.  
  
## Creazione dell'origine dati  
 Questo passaggio crea un set di dati usando la **Configurazione guidata origine dati** basata sulla tabella `Customers` nel database di esempio Northwind.  Per creare la connessione, è necessario avere accesso al database di esempio Northwind.  Per informazioni sull'impostazione del database di esempio Northwind, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
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
  
## Impostazione dei controlli da creare  
 Per questa procedura dettagliata i dati verranno visualizzati in singoli controlli nel layout **Dettagli**.  L'alternativa è costituita dal layout predefinito **Griglia** che consente di visualizzare i dati in un controllo <xref:System.Windows.Forms.DataGridView>.  
  
#### Per impostare il tipo di visualizzazione degli elementi della finestra Origini dati  
  
1.  Espandere il nodo **Customers** nella finestra **Origini dati**.  
  
2.  Modificare il tipo di rilascio della tabella **Customers** in **Dettagli**selezionando **Dettagli** dall'elenco a discesa nel nodo **Customers**.  Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Modificare il tipo di visualizzazione della colonna **CustomerID** in un'etichetta selezionando **Etichetta** nell'elenco dei controlli sul nodo **CustomerID**.  
  
## Creazione del form  
 Creare i controlli associati a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** nel form.  
  
#### Per creare controlli associati a dati nel form  
  
-   Trascinare il nodo **Customers** principale dalla finestra **Origini dati** al form.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
## Verifica dell'applicazione  
  
#### Per eseguire l'applicazione  
  
-   Premere F5.  
  
-   Usare il controllo <xref:System.Windows.Forms.BindingNavigator> per spostarsi all'interno dei record.  
  
## Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un Windows Form associato a dati.  È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Aggiunta di funzionalità di ricerca al form.  Per altre informazioni, vedere [Procedura: aggiungere una query con parametri a un'applicazione Windows Form](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Aggiungere funzionalità per l'invio di aggiornamenti al database.  Per altre informazioni, vedere [Procedura dettagliata: salvataggio di dati in un database \(a tabella singola\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md).  
  
-   Aggiunta della tabella `Orders` al set di dati selezionando **Configura il Dataset con la procedura guidata** nella finestra **Origini dati**.  Sarà quindi possibile aggiungere controlli che visualizzano dati correlati trascinando il nodo **Orders** \(posto sotto la colonna **Fax** nella tabella **Customers**\) nel form.  Per altre informazioni, vedere [Procedura: visualizzare dati correlati in un'applicazione Windows Form](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)