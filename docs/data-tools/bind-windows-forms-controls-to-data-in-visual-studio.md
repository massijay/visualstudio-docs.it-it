---
title: "Associazione di controlli Windows Form ai dati in Visual Studio | Microsoft Docs"
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
  - "dati [Windows Form], origini dati"
  - "dati [Windows Form], visualizzazione"
  - "origini dati, visualizzazione di dati"
  - "visualizzazione di dati su form"
  - "visualizzazione di dati, Windows Form"
  - "form, visualizzazione di dati"
  - "Windows Form, associazione dati"
  - "Windows Form, visualizzazione di dati"
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 37
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associazione di controlli Windows Form ai dati in Visual Studio
È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati a Windows Form.  Per creare tali controlli con associazione a dati, è possibile trascinare gli elementi dalla finestra **Origini dati** a Progettazione Windows Form in Visual Studio.  In questo argomento vengono descritte alcune delle attività, degli strumenti e delle classi più comuni che è possibile utilizzare per creare applicazioni Windows Form associate a dati.  
  
 Per informazioni generali sulla creazione dei controlli associati a dati in Visual Studio, vedere [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  Per ulteriori informazioni sull'associazione ai dati in Windows Form, vedere [Associazione ai dati di Windows Form](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
## Attività necessarie per la visualizzazione dei dati su un form di un'applicazione Windows  
 Nella tabella seguente vengono elencate le attività comuni correlate alla visualizzazione di dati in un form in un'applicazione Windows.  
  
|Task|Ulteriori informazioni|  
|----------|----------------------------|  
|Creare controlli associati a dati.<br /><br /> Associare controlli esistenti a dati.|[Procedura: associare controlli Windows Form ai dati](../data-tools/bind-windows-forms-controls-to-data.md)|  
|Creare controlli che visualizzano i dati correlati in una relazione padre\-figlio: quando l'utente seleziona un record di dati in un controllo, un altro controllo visualizza i dati correlati per il record selezionato.|[Procedura: visualizzare dati correlati in un'applicazione Windows Form](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)|  
|Creare una *tabella di ricerca*.  Una tabella di ricerca consente di visualizzare le informazioni contenute in una tabella in base al valore di un campo della chiave esterna in un'altra tabella.|[Procedura: creare tabelle di ricerca nelle applicazioni Windows Form](../data-tools/create-lookup-tables-in-windows-forms-applications.md)|  
|Formattare le modalità di visualizzazione dei dati mediante i controlli.|[Formatting and Advanced Binding Dialog Box](http://msdn.microsoft.com/it-it/42638120-9e6f-436b-985f-4036664230fd)|  
|Modificare il comportamento della didascalia smart della finestra **Origini dati**.|[Procedura: personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
|Aggiungere controlli che eseguono una query con parametri.|[Procedura: aggiungere una query con parametri a un'applicazione Windows Form](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)|  
|Impostare una colonna in modo che utilizzi un controllo immagine per visualizzare le immagini di un database.|[Procedura: associare controlli alle immagini di un database](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
|Filtrare o ordinare dati in un dataset.|[Procedura: filtrare e ordinare i dati in un'applicazione Windows Form](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
  
 Negli argomenti seguenti vengono forniti esempi di associazione di controlli Windows Form ai dati.  
  
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)  
 Viene illustrata una procedura dettagliata per l'esecuzione di query sui dati di un database e la visualizzazione dei dati in un Windows Form.  
  
 [Procedura dettagliata: visualizzazione di dati correlati in un Windows Form](../data-tools/walkthrough-displaying-related-data-on-a-windows-form.md)  
 Viene illustrata una procedura dettagliata per la visualizzazione di dati di due tabelle correlate e la visualizzazione dei dati in un Windows Form.  
  
 [Procedura: creazione di un Windows Form per la ricerca di dati](../data-tools/create-a-windows-form-to-search-data.md)  
 Viene illustrata una procedura dettagliata per la creazione di un Windows Form che esegue una ricerca in un database in base all'input dell'utente.  
  
 [Procedura dettagliata: creazione di una tabella di ricerca in un'applicazione Windows Form](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)  
 Vengono fornite istruzioni dettagliate per la visualizzazione dei dati contenuti in una tabella in base ai dati selezionati in un'altra tabella.  
  
 [Procedura dettagliata: passaggio di dati tra Windows Form](../data-tools/pass-data-between-forms.md)  
 Viene illustrata una procedura dettagliata per il passaggio di valori da un form all'altro in un'applicazione.  
  
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
 Vengono fornite istruzioni dettagliate per la creazione di un controllo personalizzato che può essere utilizzato nella finestra **Origini dati**.  
  
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
 Vengono fornite istruzioni dettagliate per la creazione di un controllo personalizzato che può essere utilizzato nella finestra **Origini dati**.  
  
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
 Vengono fornite istruzioni dettagliate per la creazione di un controllo personalizzato che può essere utilizzato nella finestra **Origini dati**.  
  
## Smart tag dei dati  
 Gli smart tag specifici per l'utilizzo di dati sono disponibili in molti controlli.  Quando a un form vengono aggiunti determinati controlli, sullo smart tag è disponibile un set di azioni possibili correlate ai dati.  
  
## Il componente BindingSource  
 Il componente <xref:System.Windows.Forms.BindingSource> ha due funzioni.  Fornisce un livello di astrazione per l'associazione dei controlli del form ai dati.  I controlli del form vengono associati al componente <xref:System.Windows.Forms.BindingSource>, anziché direttamente a un'origine dati.  
  
 E può inoltre gestire una raccolta di oggetti.  L'aggiunta di un tipo a <xref:System.Windows.Forms.BindingSource> determina la creazione di un elenco di quel tipo.  
  
 Per ulteriori informazioni sul componente <xref:System.Windows.Forms.BindingSource>, vedere:  
  
-   [Il componente BindingSource](../Topic/BindingSource%20Component.md)  
  
-   [Cenni preliminari sul componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
-   [Architettura del componente BindingSource](../Topic/BindingSource%20Component%20Architecture.md)  
  
## Controllo BindingNavigator  
 Questo componente fornisce un'interfaccia utente per l'esplorazione dei dati visualizzati in un'applicazione Windows.  Per ulteriori informazioni, vedere [Controllo BindingNavigator](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md).  
  
## Controllo DataGridView  
 Il controllo <xref:System.Windows.Forms.DataGridView> consente di visualizzare e modificare i dati tabulari da molti tipi diversi di origini dati.  È possibile associare i dati a un oggetto <xref:System.Windows.Forms.DataGridView> utilizzando la proprietà <xref:System.Windows.Forms.DataGridView.DataSource%2A>.  Per ulteriori informazioni, vedere [Cenni preliminari sul controllo DataGridView](../Topic/DataGridView%20Control%20Overview%20\(Windows%20Forms\).md).  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)