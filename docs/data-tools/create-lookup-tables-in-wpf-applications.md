---
title: "Procedura: creare tabelle di ricerca nelle applicazioni WPF | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2016"
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: creare tabelle di ricerca nelle applicazioni WPF
È possibile creare una tabella di ricerca trascinando il nodo principale di una tabella o oggetto padre nella finestra **Origini dati** in un controllo già associato a una colonna o proprietà in una tabella figlio correlata.  Il termine *tabella di ricerca* \(detto talvolta *associazione di ricerche*\) descrive un controllo che visualizza informazioni di una tabella dati in base al valore di un campo di chiave esterna di un'altra tabella.  
  
 Si consideri, ad esempio, una tabella `Orders` in un database Sales.  Ciascun record contenuto nella tabella `Orders` include un `CustomerID` che indica il cliente che ha effettuato l'ordine.  Si tratta di una chiave esterna che punta a un record cliente nella tabella `Customers`.  Nel visualizzare un elenco di ordini della tabella `Orders`, è possibile visualizzare il nome effettivo del cliente invece del `CustomerID`.  Poiché il nome del cliente si trova nella tabella `Customers`, è necessario creare una tabella di ricerca per visualizzare il nome del cliente.  La tabella di ricerca utilizza il valore `CustomerID` nel record `Orders` per esplorare la relazione e restituire il nome del cliente semplice da usare.  
  
### Per creare una tabella di ricerca  
  
1.  Aggiungere al progetto uno dei tipi seguenti di origini dati con i dati correlati:  
  
    -   Dataset o Entity Data Model.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
    -   Servizio dati WCD, servizio WCF o servizio Web.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un servizio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   Oggetti.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati negli oggetti](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
    > [!NOTE]
    >  Per poter creare una tabella di ricerca, devono esistere due tabelle o oggetti correlati come origine dati per il progetto.  
  
2.  Aprire **Progettazione WPF** e verificare che nella finestra di progettazione sia disponibile un contenitore che sia una destinazione di rilascio valida per gli elementi nella finestra **Origini dati**.  
  
     Per ulteriori informazioni sulle destinazioni di rilascio valide, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
3.  Scegliere **Mostra origini dati** dal menu **Dati** per aprire la finestra **Origini dati**.  
  
4.  Espandere i nodi nella finestra **Origini dati** fino a visualizzare la tabella o l'oggetto padre e la tabella o l'oggetto figlio correlato.  
  
    > [!NOTE]
    >  La tabella o l'oggetto figlio correlato è il nodo visualizzato come nodo figlio espandibile sotto la tabella o l'oggetto padre.  
  
5.  Fare clic sul menu a discesa relativo al nodo figlio e selezionare **Dettagli**.  
  
6.  Espandere il nodo figlio.  
  
7.  Sotto il nodo figlio fare clic sul menu a discesa relativo all'elemento che correla i dati figlio e padre \(nell'esempio precedente, il nodo **CustomerID**\).  Selezionare uno dei tipi seguenti di controlli che supportano l'associazione di ricerche:  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Se il controllo **ListBox** o **ListView** non è visualizzato nell'elenco, è possibile aggiungere questi controlli all'elenco.  Per informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Qualsiasi controllo personalizzato derivante dalla classe <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        >  Per informazioni sull'aggiunta di controlli personalizzati all'elenco di controlli selezionabili per elementi presenti nella finestra **Origini dati**, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Trascinare il nodo figlio dalla finestra **Origini dati** su un contenitore in Progettazione WPF \(nell'esempio precedente, il nodo figlio sarebbe il nodo **Orders**\).  
  
     In Visual Studio viene generato XAML che crea i nuovi controlli associati a dati per ognuno degli elementi trascinati.  XAML aggiunge inoltre un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> per la tabella o l'oggetto figlio alle risorse della destinazione di rilascio.  Per alcune origini dati, Visual Studio genera inoltre il codice per caricare i dati nella tabella o nell'oggetto.  Per ulteriori informazioni, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
9. Trascinare il nodo padre dalla finestra **Origini dati** sul controllo dell'associazione di ricerche creato in precedenza \(nell'esempio precedente, il nodo padre sarebbe il nodo **Customers**\).  
  
     Visual Studio imposta alcune proprietà sul controllo per configurare l'associazione di ricerche.  Nella tabella seguente vengono elencate le proprietà modificate da Visual Studio.  Se necessario, è possibile modificare queste proprietà in XAML o nella finestra **Proprietà**.  
  
    |Proprietà|Descrizione dell'impostazione|  
    |---------------|-----------------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Questa proprietà specifica la raccolta o l'associazione utilizzata per ottenere i dati visualizzati nel controllo.  In Visual Studio la proprietà viene impostata sull'oggetto <xref:System.Windows.Data.CollectionViewSource> per i dati padre trascinati sul controllo.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Questa proprietà specifica il percorso dell'elemento di dati visualizzato nel controllo.  In Visual Studio la proprietà viene impostata sulla prima colonna o proprietà dei dati padre, dopo la chiave primaria, che dispone di un tipo di dati stringa.<br /><br /> Se si desidera visualizzare una colonna o una proprietà diversa nei dati padre, impostare questa proprietà sul percorso di una proprietà diversa.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|In Visual Studio la proprietà viene associata alla colonna o alla proprietà dei dati figlio trascinati nella finestra di progettazione.  Si tratta della chiave esterna ai dati padre.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|In Visual Studio la proprietà viene impostata sul percorso della colonna o della proprietà dei dati figlio corrispondenti alla chiave esterna ai dati padre.|  
  
## Vedere anche  
 [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Procedura: associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Procedura: visualizzare dati correlati nelle applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)