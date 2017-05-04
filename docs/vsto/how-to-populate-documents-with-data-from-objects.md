---
title: "Procedura: Popolare documenti con i dati di oggetti | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documenti [sviluppo per Office in Visual Studio], popolamento con dati"
  - "dati [sviluppo per Office in Visual Studio], aggiunta ai documenti"
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Procedura: Popolare documenti con i dati di oggetti
  L'accesso ai dati di un oggetto dati è uguale sia nei progetti a livello di documento per Microsoft Office Word, sia nei progetti Windows Form. Per inserire i dati di un oggetto nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile usare i controlli Windows Form. Inoltre, è possibile visualizzare i dati tramite i controlli host. I controlli host sono oggetti nativi di Microsoft Office Word che sono stati migliorati con eventi e funzionalità di data binding. Per altre informazioni, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Per popolare il documento con i dati di un oggetto, è necessario completare tre passaggi di base:  
  
-   Aggiungere al documento un controllo che è possibile associare ai dati.  
  
-   Aggiungere un oggetto dati al documento.  
  
-   Connettere l'oggetto dati a BindingSource  
  
## Aggiunta di un oggetto dati  
  
#### Per aggiungere un oggetto dati  
  
-   Aprire la finestra **Origini dati** e creare un'origine dati da un oggetto. Per altre informazioni, vedere [Procedura: connettersi ai dati negli oggetti](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
## Connessione dell'oggetto dati a BindingSource  
 Nei progetti a livello di documento i controlli vengono aggiunti al documento e associati ai dati in fase di progettazione.  
  
 Nei progetti di componente aggiuntivo VSTO è possibile creare controlli e associarli in fase di esecuzione.  
  
### Progetti a livello di documento  
  
##### Per connettere l'oggetto dati a BindingSource  
  
1.  Trascinare il campo dati desiderato dalla finestra **Origini dati** al documento in modo da creare automaticamente un controllo.  
  
2.  Nel codice creare un'istanza del tipo di oggetto selezionato per l'origine dati.  
  
3.  Assegnare l'istanza alla proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> dell'oggetto <xref:System.Windows.Forms.BindingSource>.  
  
### Progetti a livello di applicazione  
  
##### Per connettere l'oggetto dati a BindingSource  
  
1.  Nel codice creare un'istanza del tipo di oggetto associato all'origine dati.  
  
2.  Creare un'istanza di un oggetto <xref:System.Windows.Forms.BindingSource>.  
  
3.  Assegnare l'istanza dell'origine dati alla proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> dell'oggetto <xref:System.Windows.Forms.BindingSource>.  
  
4.  Aggiungere l'origine dati come data binding al controllo.  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Connessione ai dati nelle applicazioni Windows Form](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Cenni preliminari sul componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
  