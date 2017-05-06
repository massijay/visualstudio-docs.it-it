---
title: "Procedura: Compilare documenti con dati forniti da servizi"
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
  - "Servizi Web [sviluppo per Office in Visual Studio], popolamento di documenti"
  - "dati [sviluppo per Office in Visual Studio], aggiunta ai documenti"
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Procedura: Compilare documenti con dati forniti da servizi
  L'accesso ai dati funziona in modo identico per i progetti a livello di documento per Microsoft Office e per i progetti Windows Form. Per inserire i dati nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile persino usare i controlli Windows Form. Inoltre, è possibile usare i controlli chiamati controlli host, ossia oggetti nativi in Microsoft Office Excel e Microsoft Office Word migliorati con funzionalità di associazione di dati ed eventi. Per altre informazioni, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L'esempio seguente mostra come aggiungere controlli con associazione ai dati ai documenti in fase di progettazione. Per un esempio su come aggiungere i controlli con associazione ai dati nei componenti aggiuntivi VSTO in fase di esecuzione, vedere [Procedura dettagliata: Associazione ai dati di un servizio in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere il video che descrive la [procedura di interazione con i servizi Web da Microsoft Excel](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### Per popolare un progetto a livello di documento con i dati da un servizio Web  
  
1.  Aprire la finestra **Origini dati** e creare un'origine dati del servizio per il progetto. Per altre informazioni, vedere [Procedura: connettersi ai dati di un servizio](~/data-tools/how-to-connect-to-data-in-a-service.md).  
  
2.  Trascinare la tabella o il campo desiderato dalla finestra **Origini dati** al documento.  
  
     Viene creato un controllo nel documento, un oggetto <xref:System.Windows.Forms.BindingSource> associato alla classe di oggetti nel progetto e classi per il servizio.  
  
3.  Nel codice creare un'istanza della classe del servizio Web a cui è stata eseguita la connessione nel passaggio 1.  
  
4.  Se alcune proprietà sono necessarie per la comunicazione con il servizio Web, creare istanze di queste proprietà.  
  
5.  Creare e inviare una richiesta di dati usando i metodi esposti dal servizio Web e le eventuali istanze delle proprietà create nel passaggio 4.  
  
     I metodi usati dipendono dall'offerta del servizio Web.  
  
6.  Assegnare la risposta di dati dal servizio Web alla proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> di <xref:System.Windows.Forms.BindingSource>.  
  
 Quando si esegue il progetto, i controlli visualizzano il primo record nell'origine dati. È possibile abilitare lo scorrimento dei record gestendo gli eventi di valuta tramite gli oggetti in <xref:System.Windows.Forms.BindingSource>.  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Procedura: popolare fogli di lavoro con dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Procedura: Popolare documenti con i dati di oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  