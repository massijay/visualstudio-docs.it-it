---
title: "Procedura: visualizzare dati correlati nelle applicazioni WPF | Microsoft Docs"
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
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: visualizzare dati correlati nelle applicazioni WPF
In alcune applicazioni, potrebbe essere necessario utilizzare dati provenienti da più tabelle o entità reciprocamente correlate in una relazione padre\-figlio.  Potrebbe essere necessario, ad esempio, visualizzare una griglia in cui sono mostrati i clienti presenti in una tabella `Customers`.  Quando l'utente seleziona un cliente specifico, in un'altra griglia vengono visualizzati gli ordini di tale cliente presenti in una tabella `Orders` correlata.  
  
 È possibile creare controlli associati a dati che consentono di visualizzare i dati correlati tramite trascinamento degli elementi dalla finestra **Origini dati** a Progettazione WPF.  
  
### Per creare controlli per la visualizzazione di record correlati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati** per aprire la finestra **Origini dati**.  
  
2.  Scegliere **Aggiungi nuova origine dati** e completare la **Configurazione guidata origine dati**.  
  
3.  Aprire Progettazione WPF e verificare che nella finestra di progettazione sia disponibile un contenitore che sia una destinazione di rilascio valida per gli elementi nella finestra **Origini dati**.  
  
     Per ulteriori informazioni sulle destinazioni di rilascio valide, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4.  Nella finestra **Origini dati** espandere il nodo che rappresenta la tabella o l'oggetto padre nella relazione.  La tabella o l'oggetto padre si trova sul lato "uno" di una relazione uno\-a\-molti.  
  
5.  Trascinare il nodo padre \(o singoli elementi nel nodo padre\) dalla finestra **Origini dati** su una destinazione di rilascio valida nella finestra di progettazione.  
  
     In Visual Studio viene generato XAML che crea i nuovi controlli associati a dati per ogni elemento trascinato.  XAML aggiunge inoltre un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> per la tabella o l'oggetto padre alle risorse della destinazione di rilascio.  Per alcune origini dati, Visual Studio genera inoltre il codice per caricare i dati nella tabella o nell'oggetto padre.  Per ulteriori informazioni, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Nella finestra **Origini dati** individuare la tabella o l'oggetto figlio correlato.  Le tabelle e gli oggetti figlio correlati vengono visualizzati come nodi espandibili alla fine dell'elenco di dati del nodo padre.  
  
7.  Trascinare il nodo figlio \(o singoli elementi nel nodo figlio\) dalla finestra **Origini dati** su una destinazione di rilascio valida nella finestra di progettazione.  
  
     In Visual Studio viene generato XAML che crea i nuovi controlli associati a dati per ognuno degli elementi trascinati.  XAML aggiunge inoltre un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> per la tabella o l'oggetto figlio alle risorse della destinazione di rilascio.  Questo nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> viene associato alla proprietà della tabella o dell'oggetto padre trascinato nella finestra di progettazione.  Per alcune origini dati, Visual Studio genera inoltre il codice per caricare i dati nella tabella o nell'oggetto figlio.  
  
     Nella figura seguente viene illustrata la tabella **Orders** correlata della tabella **Customers** in un dataset nella finestra **Origini dati**.  
  
     ![Finestra Origini dati con visualizzazione delle relazioni](~/docs/data-tools/media/datasources2.gif "DataSources2")  
  
## Vedere anche  
 [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Procedura: associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Procedura: creare tabelle di ricerca nelle applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)