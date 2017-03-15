---
title: "Associazione di controlli WPF ai dati in Visual Studio | Microsoft Docs"
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
  - "dati [WPF], visualizzazione"
  - "associazione dati, WPF"
  - "visualizzazione di dati, WPF"
  - "WPF [WPF], dati"
  - "associazione dati WPF [Visual Studio]"
  - "WPF (finestra di progettazione), associazione dati"
  - "WPF, associazione dati in Visual Studio"
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associazione di controlli WPF ai dati in Visual Studio
È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)].  Per creare questi controlli associati a dati, è possibile trascinare gli elementi dalla finestra **Origini dati** a [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  In questo argomento vengono descritte alcune delle più comuni attività, strumenti e classi che è possibile utilizzare per creare applicazioni [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] associate a dati.  
  
 Per informazioni generali sulla creazione dei controlli associati a dati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vedere [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Per altre informazioni sull'associazione di dati con [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)], vedere [Cenni preliminari sull'associazione dati](../Topic/Data%20Binding%20Overview.md).  
  
## Attività coinvolte nell'associazione di controlli WPF a dati  
 Nella tabella seguente vengono elencate le attività che possono essere eseguite trascinando gli elementi dalla finestra **Origini dati** a [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  
  
|Attività|Altre informazioni|  
|--------------|------------------------|  
|Creare nuovi controlli associati a dati.<br /><br /> Associare controlli esistenti a dati.|[Procedura: associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)|  
|Creare controlli che visualizzano i dati correlati in una relazione padre\-figlio: quando l'utente seleziona un record di dati padre in un controllo, un altro controllo visualizza i dati figlio correlati per il record selezionato.|[Procedura: visualizzare dati correlati nelle applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)|  
|Creare una *tabella di ricerca* che consente di visualizzare le informazioni contenute in una tabella in base al valore di un campo della chiave esterna in un'altra tabella.|[Procedura: creare tabelle di ricerca nelle applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Associare un controllo a un'immagine di un database.|[Procedura: associare controlli alle immagini di un database](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## Destinazioni di rilascio valide  
 È possibile trascinare gli elementi della finestra **Origini dati** solo in destinazioni di rilascio valide in [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  Esistono due tipi principali di destinazioni di rilascio valide: contenitori e controlli.  Un contenitore è un elemento dell'interfaccia utente che in genere contiene i controlli.  Una griglia e una finestra, ad esempio, sono contenitori.  
  
## Codice e XAML generati  
 Quando si trascina un elemento dalla finestra **Origini dati** in [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che definisce un nuovo controllo associato a dati \(o associa un controllo esistente all'origine dati\).  Per alcune origini dati, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera anche il codice nel file code\-behind che inserisce i dati nell'origine dati.  
  
 Nella tabella seguente vengono elencati [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e il codice generati da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per ogni tipo di origine dati nella finestra **Origini dati**.  
  
|Origine dati|Generazione di XAML per l'associazione di un controllo all'origine dati|Generazione di codice per l'inserimento dei dati nell'origine dati|  
|------------------|-----------------------------------------------------------------------------|------------------------------------------------------------------------|  
|Set di dati|Sì|Sì|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Sì|Sì|  
|Servizio|Sì|No|  
|Oggetto|Sì|No|  
  
### Dataset  
 Quando si trascina una tabella o una colonna dalla finestra **Origini dati** alla finestra di progettazione, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che esegue le operazioni seguenti:  
  
-   Aggiunge il dataset e un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento.  <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nel dataset.  
  
-   Crea un'associazione dati per un controllo.  Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento.  Se si trascina l'elemento in un contenitore, XAML crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento.  Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] apporta inoltre le modifiche seguenti al file code\-behind:  
  
-   Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] contenente il controllo.  Il gestore dell'evento inserisce i dati nella tabella, recupera l'oggetto <xref:System.Windows.Data.CollectionViewSource> dalle risorse del contenitore, quindi imposta come elemento corrente il primo elemento di dati.  Se un gestore eventi <xref:System.Windows.FrameworkElement.Loaded> è già presente, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aggiunge questo codice al gestore eventi esistente.  
  
### Entity Data Model  
 Quando si trascina un'entità o una proprietà di entità dalla finestra **Origini dati** alla finestra di progettazione, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che esegue le operazioni seguenti:  
  
-   Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento.  <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'entità.  
  
-   Crea un'associazione dati per un controllo.  Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associa il controllo all'elemento.  Se si trascina l'elemento in un contenitore, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento.  Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.  
  
 Visual Studio apporta inoltre le modifiche seguenti al file code\-behind:  
  
-   Aggiunge un nuovo metodo che restituisce una query per l'entità trascinata nella finestra di progettazione \(o per l'entità contenente la proprietà trascinata nella finestra di progettazione\).  Il nome del nuovo metodo è Get*NomeEntità*Query, dove *NomeEntità* è il nome dell'entità.  
  
-   Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] contenente il controllo.  Il gestore dell'evento chiama il metodo Get*NomeEntità*Query per inserire i dati nell'entità, recupera <xref:System.Windows.Data.CollectionViewSource> dalle risorse del contenitore e quindi imposta come elemento corrente il primo elemento di dati.  Se un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> è già presente, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aggiunge questo codice al gestore dell'evento esistente.  
  
### Servizi  
 Quando si trascina un oggetto servizio o una proprietà dalla finestra **Origini dati** alla finestra di progettazione, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che crea un controllo associato a dati \(o associa un controllo esistente all'oggetto o alla proprietà\).  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], tuttavia, non genera il codice che inserisce i dati nell'oggetto servizio del proxy.  È necessario scrivere questo codice manualmente.  Per un esempio che illustra come eseguire questa operazione, vedere [Procedura dettagliata: associazione di controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 Visual Studio genera XAML che esegue le operazioni seguenti:  
  
-   Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento.  <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto restituito dal servizio.  
  
-   Crea un'associazione dati per un controllo.  Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associa il controllo all'elemento.  Se si trascina l'elemento in un contenitore, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento.  Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.  
  
### Oggetti  
 Quando si trascina un oggetto o una proprietà dalla finestra **Origini dati** alla finestra di progettazione, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che crea un controllo associato a dati \(o associa un controllo esistente all'oggetto o alla proprietà\).  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], tuttavia, non genera il codice per inserire i dati nell'oggetto.  È necessario scrivere questo codice manualmente.  
  
> [!NOTE]
>  Le classi personalizzate devono essere pubblicate e devono avere un costruttore senza parametri predefinito.  Le classi annidate non possono avere un 'punto' nella sintassi.  Per altre informazioni, vedere [Classi XAML e personalizzate per WPF](../Topic/XAML%20and%20Custom%20Classes%20for%20WPF.md).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che esegue quanto riportato di seguito:  
  
-   Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento.  <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto.  
  
-   Crea un'associazione dati per un controllo.  Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento.  Se si trascina l'elemento in un contenitore, XAML crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento.  Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.  
  
## Vedere anche  
 [Procedura: associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Procedura: creare tabelle di ricerca nelle applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Procedura: visualizzare dati correlati nelle applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Associazione di controlli WPF a un Entity Data Model](http://msdn.microsoft.com/data/jj574514.aspx)   
 [Procedura dettagliata: associazione di controlli WPF a un dataset](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Procedura dettagliata: associazione di controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)   
 [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)