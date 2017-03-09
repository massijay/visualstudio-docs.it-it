---
title: "Procedura: associare controlli Windows Form ai dati | Microsoft Docs"
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
  - "dati [Windows Form], visualizzazione"
  - "origini dati, visualizzazione"
  - "visualizzazione di dati, controlli Windows Form"
  - "Windows Form, visualizzazione di dati"
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: associare controlli Windows Form ai dati
Associare dati ai controlli Windows Form trascinando oggetti dalla [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  Prima di trascinare elementi dalla finestra **Origini dati**, è possibile impostare il tipo di controllo della tabella su **Dettagli** per i controlli singoli oppure su **DataGridView** per un oggetto <xref:System.Windows.Forms.DataGridView>.  Per ulteriori informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
 Se i controlli necessari dall'applicazione non sono disponibili dalla finestra **Origini dati**, è possibile aggiungere controlli.  Per ulteriori informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Visualizzazione di un'intera tabella di dati nei singoli controlli  
 È possibile visualizzare un'intera tabella di dati in singoli controlli trascinando la tabella, o un nodo che rappresenti una raccolta se si utilizza un'origine dati oggetto, dalla finestra **Origini dati** in un form di un'applicazione Windows.  
  
#### Per visualizzare un'intera tabella di dati  
  
1.  Aprire la finestra **Origini dati**.  Per ulteriori informazioni, vedere [Procedura: Aprire la finestra Origini dati](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Se la finestra **Origini dati** è vuota, aggiungervi un'origine dati.  Per ulteriori informazioni, vedere la classe [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md).  
  
2.  Aprire il form in **Progettazione Windows Form**.  
  
3.  Selezionare una tabella nella finestra **Origini dati**, fare clic sulla freccia a discesa, quindi selezionare **Dettagli**.  
  
4.  Trascinare la tabella dalla finestra **Origini dati** in un form.  
  
     Sul form viene creato un singolo controllo associato a dati per ciascuna colonna o proprietà, insieme a un controllo Label denominato in modo appropriato.  
  
## Visualizzazione di colonne di dati selezionate nei singoli controlli  
 Visualizzare singole colonne di dati in singoli controlli trascinando le colonne, o le proprietà se si utilizza un'origine dati oggetto, dalla finestra **Origini dati** in un form di un'applicazione Windows.  
  
#### Per visualizzare le colonne di dati selezionate  
  
1.  Aprire la finestra **Origini dati**.  Per ulteriori informazioni, vedere [Procedura: Aprire la finestra Origini dati](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Se la finestra **Origini dati** è vuota, aggiungervi un'origine dati.  Per ulteriori informazioni, vedere la classe [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md).  
  
2.  Espandere la tabella per visualizzare le singole colonne.  
  
    > [!TIP]
    >  Per impostare il controllo creato per ciascuna colonna, selezionare la colonna nella finestra **Origini dati**, fare clic sulla freccia a discesa e scegliere un  controllo dall'elenco dei controlli disponibili.  Per ulteriori informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Aprire il form in **Progettazione Windows Form**.  
  
4.  Trascinare le colonne desiderate dalla finestra **Origini dati** in un form.  
  
     Per ciascuna colonna o proprietà trascinata, sul form viene creato un singolo controllo associato a dati, insieme a un controllo Label denominato in maniera appropriata.  
  
 È inoltre possibile trascinare elementi dalla finestra **Origini dati** ai controlli esistenti \(già presenti in un form\) per associare il controllo ai dati.  Se un controllo è già associato a dei dati, le associazioni a dati vengono reimpostate sull'elemento trascinato nel controllo più di recente.  
  
> [!NOTE]
>  Per essere considerate destinazioni di trascinamento valide, i controlli devono consentire la visualizzazione del tipo di dati sottostante dell'elemento trascinato dalla finestra **Origini dati**.  Non è consentito ad esempio trascinare un elemento il cui tipo di dati è <xref:System.DateTime> in un controllo <xref:System.Windows.Forms.CheckBox> perché <xref:System.Windows.Forms.CheckBox> non è in grado di visualizzare una data.  
  
#### Per associare un controllo esistente ai dati  
  
1.  Aprire la finestra **Origini dati**.  Per ulteriori informazioni, vedere [Procedura: Aprire la finestra Origini dati](../data-tools/how-to-open-the-data-sources-window.md).  
  
2.  Aprire il form in [Windows Forms Designer](http://msdn.microsoft.com/it-it/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
3.  Espandere una tabella o un oggetto nella finestra **Origini dati** per visualizzarne le singole colonne o proprietà.  
  
4.  Trascinare l'elemento desiderato dalla finestra **Origini dati** in un controllo esistente.  
  
     Il controllo è ora associato all'elemento selezionato.  
  
## Visualizzazione di dati in un controllo DataGridView  
  
#### Per visualizzare i dati in un nuovo controllo DataGridView di Windows Form  
  
1.  Aprire la finestra **Origini dati**.  Per ulteriori informazioni, vedere [Procedura: Aprire la finestra Origini dati](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Se la finestra **Origini dati** è vuota, aggiungerle un'origine dati.  Per ulteriori informazioni, vedere la classe [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md).  
  
2.  Aprire il form in **Progettazione Windows Form**.  
  
3.  Selezionare una tabella nella finestra **Origini dati**, fare clic sulla freccia a discesa, quindi selezionare **DataGridView**.  
  
4.  Trascinare la tabella dalla finestra **Origini dati** in un form.  
  
     Sul form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti sono visualizzati gli oggetti [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
#### Per visualizzare i dati in un controllo DataGridView esistente di Windows Form  
  
1.  Aprire la finestra **Origini dati**.  Per ulteriori informazioni, vedere [Procedura: Aprire la finestra Origini dati](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Se la finestra **Origini dati** è vuota, aggiungerle un'origine dati.  Per ulteriori informazioni, vedere la classe [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md).  
  
2.  Aprire il form in **Progettazione Windows Form**.  
  
3.  Selezionare una tabella nella finestra **Origini dati**, fare clic sulla freccia a discesa, quindi selezionare **DataGridView**.  
  
4.  Trascinare la tabella dalla finestra **Origini dati** in un controllo <xref:System.Windows.Forms.DataGridView> sul form.  
  
     Il controllo <xref:System.Windows.Forms.DataGridView> è ora associato alla tabella trascinata al suo interno.  Sulla barra dei componenti vengono visualizzati gli oggetti [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md) e <xref:System.Windows.Forms.BindingSource>.  
  
## Vedere anche  
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cenni preliminari sul componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)   
 [Cenni preliminari sul controllo BindingNavigator](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)   
 [Strumenti per l'utilizzo delle origini dati in Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)