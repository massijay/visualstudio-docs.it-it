---
title: "Procedura: popolare fogli di lavoro con dati da un database | Microsoft Docs"
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
  - "dati [sviluppo per Office in Visual Studio], aggiunta a fogli di lavoro"
  - "database [sviluppo per Office in Visual Studio], compilazione di fogli di lavoro"
  - "fogli di lavoro [sviluppo per Office in Visual Studio], compilazione"
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Procedura: popolare fogli di lavoro con dati da un database
  È possibile accedere ai dati dei progetti di Office a livello di documento nella stessa modalità di accesso ai dati dei progetti Windows Form.  Per inserire i dati nella soluzione si utilizzano infatti gli stessi strumenti e lo stesso codice. Inoltre, per visualizzare i dati si possono persino utilizzare i controlli Windows Form.  È inoltre possibile sfruttare i controlli host, oggetti nativi di Microsoft Office Excel che sono stati estesi con eventi e funzionalità di associazione dati.  Per ulteriori informazioni, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Nell'esempio seguente viene mostrato come aggiungere controlli con associazione a dati in progetti a livello di documento mediante una finestra di progettazione.  Per un esempio relativo all'aggiunta in fase di esecuzione di controlli con associazione a dati nei progetti a livello di applicazione, vedere [Procedura dettagliata: Data binding complesso in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere la [procedura relativa al trasferimento di dati in una cartella di lavoro di Excel](http://go.microsoft.com/fwlink/?LinkID=130277)e [la procedura relativa all'utilizzo di dati di database in Excel](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## Aggiunta di un controllo con associazione a dati a un foglio di lavoro in fase di progettazione  
  
#### Per popolare un foglio di lavoro con i dati di un database  
  
1.  Aprire un progetto a livello di documento di Excel in Visual Studio, tenendo aperto il foglio di lavoro nella finestra di progettazione.  
  
2.  Aprire la finestra **Origini dati** e creare un'origine dati per il progetto.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un database](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
3.  Trascinare la tabella o il campo desiderato dalla finestra **Origini dati** sul foglio di lavoro.  
  
 Uno dei controlli seguenti viene creato sul foglio di lavoro:  
  
-   Se si trascina un campo, sul foglio di lavoro viene creato un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>.  Per ulteriori informazioni, vedere [Controllo NamedRange](../vsto/namedrange-control.md).  
  
-   Se si trascina una tabella, sul foglio di lavoro viene creato un controllo <xref:Microsoft.Office.Tools.Excel.ListObject>.  Per ulteriori informazioni, vedere [Controllo ListObject](../vsto/listobject-control.md).  
  
 È possibile aggiungere un controllo differente selezionando la tabella o il campo nella finestra **Origini dati** e scegliendo un controllo differente dall'elenco a discesa.  
  
## Oggetti del progetto  
 Oltre al controllo, i seguenti oggetti relativi ai dati vengono aggiunti automaticamente al progetto:  
  
-   Un dataset tipizzato che incapsula le tabelle dati a cui ci si è connessi nel database.  Per ulteriori informazioni, vedere [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Un oggetto <xref:System.Windows.Forms.BindingSource> che connette il controllo al dataset tipizzato.  Per ulteriori informazioni, vedere [Cenni preliminari sul componente BindingSource](../Topic/BindingSource%20Component%20Overview.md).  
  
-   Un oggetto TableAdapter che connette il dataset tipizzato al database.  Per ulteriori informazioni, vedere [Cenni preliminari sugli oggetti TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
-   Un oggetto TableAdapterManager, utilizzato per coordinare i TableAdapter nel dataset per attivare gli aggiornamenti gerarchici.  Per ulteriori informazioni, vedere [Aggiornamento gerarchico](../data-tools/hierarchical-update.md) e [Panoramica di TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 Quando si esegue il progetto, nel controllo verrà visualizzato il primo record dell'origine dati.  È possibile utilizzare <xref:System.Windows.Forms.BindingSource> per consentire agli utenti di scorrere i record.  
  
#### Per scorrere i record  
  
-   Utilizzare i metodi <xref:System.Windows.Forms.BindingSource> quali <xref:System.Windows.Forms.BindingSource.MoveNext%2A> e <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Per informazioni su come inviare aggiornamenti al dataset tipizzato e al database, vedere [Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Procedura: Popolare documenti con i dati di oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: Compilare documenti con dati forniti da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Ricerca di categorie: Trasferire i dati in un foglio di lavoro di Excel](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Ricerca di categorie: Utilizzare dati del database in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  