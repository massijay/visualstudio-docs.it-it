---
title: "Procedura: associare controlli WPF ai dati in Visual Studio | Microsoft Docs"
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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 26
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: associare controlli WPF ai dati in Visual Studio
È possibile creare controlli [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] associati ai dati mediante la finestra **Origini dati**.  Prima di tutto, aggiungere un'origine dati alla finestra **Origini dati**.  Trascinare quindi gli elementi dalla finestra **Origini dati** a **WPF Designer**.  
  
##  <a name="adding"></a> Aggiunta di un'origine dati alla finestra Origini dati  
 Prima di creare controlli associati a dati, è necessario aggiungere un'origine dati alla finestra **Origini dati**.  
  
#### Per aggiungere un'origine dati alla finestra Origini dati  
  
1.  Scegliere **Altre finestre** dal menu **Visualizza**, quindi fare clic su **Origini dati**.  
  
2.  Fare clic su **Aggiungi nuova origine dati** e completare la **Configurazione guidata origine dati**.  
  
3.  Eseguire una delle attività seguenti per creare controlli associati ai dati:  
  
    -   [Creazione di un controllo associato a un singolo campo di dati](#simple).  
  
    -   [Creazione di un controllo associato a più campi di dati](#complex).  
  
    -   [Creazione di un set di controlli associati a più campi di dati](#details).  
  
    -   [Associazione di dati a controlli esistenti nella finestra di progettazione](#existing).  
  
##  <a name="simple"></a> Creazione di un controllo associato a un singolo campo di dati  
 Quando si aggiunge un'origine dati nella finestra **Origini dati**, è possibile creare un nuovo controllo associato a dati che visualizza un unico campo di dati, ad esempio <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox>.  
  
#### Per creare un controllo associato a un unico campo di dati  
  
1.  Nella finestra **Origini dati** espandere un elemento che rappresenta una tabella o un oggetto.  Individuare l'elemento figlio che rappresenta la colonna o la proprietà a cui eseguire l'associazione.  Per un esempio visivo, vedere [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  
  
2.  Facoltativamente, selezionare il controllo da creare.  Ogni elemento nella finestra **Origini dati** dispone di un controllo predefinito che viene creato quando si trascina l'elemento nella finestra di progettazione.  Il controllo predefinito dipende dal tipo di dati sottostante dell'elemento.  
  
     Per scegliere un controllo diverso, fare clic sulla freccia a discesa accanto all'elemento e selezionare un controllo.  Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Trascinare l'elemento in un contenitore valido nella finestra di progettazione, ad esempio <xref:System.Windows.Controls.Grid>.  Per altre informazioni sui contenitori validi, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea il nuovo controllo associato a dati e un oggetto <xref:System.Windows.Controls.Label> nel contenitore.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera anche [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e il codice per associare il controllo ai dati.  Per altre informazioni, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="complex"></a> Creazione di un controllo associato a più campi di dati  
 Quando si aggiunge un'origine dati nella finestra **Origini dati**, è possibile creare un nuovo controllo associato a dati che visualizza più campi di dati, ad esempio <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView>.  
  
#### Per creare un controllo associato a più campi di dati  
  
1.  Nella finestra **Origini dati** selezionare un elemento che rappresenta una tabella o un oggetto.  Per un esempio visivo, vedere [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  
  
2.  Facoltativamente, selezionare il controllo da creare.  Per impostazione predefinita, ogni elemento nella finestra **Origini dati** che rappresenta una tabella dati o un oggetto è impostato per creare un oggetto <xref:System.Windows.Controls.DataGrid> \(se il progetto è destinato a .NET Framework 4\) o <xref:System.Windows.Controls.ListView> \(per le versioni precedenti di .NET Framework\).  
  
     Per selezionare un controllo diverso, fare clic sulla freccia a discesa accanto all'elemento e selezionare un controllo.  Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Se si preferisce non visualizzare una determinata colonna o proprietà, espandere l'elemento per visualizzarne i figli.  Fare clic sulla freccia a discesa accanto alla colonna o alla proprietà da non visualizzare, quindi fare clic su **Nessuno**.  
  
3.  Trascinare l'elemento in un contenitore valido nella finestra di progettazione, ad esempio <xref:System.Windows.Controls.Grid>.  Per altre informazioni sui contenitori validi, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea il nuovo controllo associato a dati nel contenitore. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera inoltre [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e il codice per associare il controllo ai dati.  Per altre informazioni, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="details"></a> Creazione di un set di controlli associati a più campi di dati  
 Dopo avere aggiunto un'origine dati alla finestra **Origini dati**, è possibile associare una tabella dati o un oggetto a un set di controlli.  Viene creato un controllo diverso per ogni colonna o proprietà nella tabella o nell'oggetto.  
  
#### Per creare un set di controlli associati a più campi di dati  
  
1.  Nella finestra **Origini dati** selezionare un elemento che rappresenta una tabella o un oggetto.  Per un esempio visivo, vedere [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  
  
2.  Fare clic sulla freccia a discesa accanto all'elemento e selezionare **Details**.  
  
    > [!NOTE]
    >  Se si preferisce non visualizzare una determinata colonna o proprietà, espandere l'elemento per visualizzarne i figli.  Fare clic sulla freccia a discesa accanto alla colonna o alla proprietà da non visualizzare, quindi fare clic su **Nessuno**.  
  
3.  Trascinare l'elemento in un contenitore valido nella finestra di progettazione, ad esempio <xref:System.Windows.Controls.Grid>.  Per altre informazioni sui contenitori validi, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea i nuovi controlli associati a dati nel contenitore.  Ogni controllo è associato a una colonna o a una proprietà diversa ed è accompagnato da un controllo <xref:System.Windows.Controls.Label> con titolo appropriato. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera anche [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e il codice per associare i controlli ai dati.  Per altre informazioni, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="existing"></a> Associazione di dati a controlli esistenti nella finestra di progettazione  
 Dopo avere aggiunto un'origine dati alla finestra **Origini dati** è possibile aggiungere un'associazione dati a un controllo esistente nella finestra di progettazione.  
  
#### Per associare dati a un controllo esistente nella finestra di progettazione  
  
1.  Nella finestra **Origini dati** utilizzare una delle procedure seguenti:  
  
    -   Per aggiungere un'associazione dati a un controllo esistente che visualizza più campi di dati, ad esempio <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView>, selezionare l'elemento che rappresenta la tabella o l'oggetto da associare al controllo.  
  
    -   Per aggiungere un'associazione dati a un controllo esistente che visualizza più campi di dati, ad esempio <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox>, espandere l'elemento che rappresenta la tabella o l'oggetto che contiene i dati, quindi selezionare l'elemento che rappresenta i dati da associare al controllo.  
  
2.  Trascinare l'elemento selezionato dalla finestra **Origini dati** in un controllo esistente nella finestra di progettazione.  Il controllo deve essere una destinazione di rilascio valida.  Per altre informazioni, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e il codice per associare il controllo ai dati.  Per altre informazioni, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
    > [!NOTE]
    >  Se il controllo è già associato a dati, l'associazione dati per il controllo viene reimpostata sull'elemento trascinato nel controllo più di recente.  
  
## Vedere anche  
 [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Procedura: creare tabelle di ricerca nelle applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Procedura: visualizzare dati correlati nelle applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Procedura dettagliata: associazione di controlli WPF a un dataset](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Procedura dettagliata: associazione di controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)