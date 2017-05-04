---
title: "Procedura: popolare documenti con dati da un database | Microsoft Docs"
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
  - "dati, aggiunta a documenti"
  - "documenti, popolazione con dati"
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Procedura: popolare documenti con dati da un database
  È possibile accedere ai dati dei progetti a livello di documento per Microsoft Office con la stessa procedura usata per accedere ai dati dei progetti Windows Form.  Per inserire dati da un database nella soluzione si usano infatti gli stessi strumenti e lo stesso codice e per visualizzare i dati è possibile usare i controlli Windows Form.  
  
 Inoltre, è possibile visualizzare i dati tramite i controlli host.  I controlli host sono oggetti nativi di Microsoft Office Word che sono stati migliorati con eventi e funzionalità di data binding.  Per altre informazioni, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Nell'esempio seguente viene mostrato come aggiungere controlli con associazione a dati in progetti a livello di documento mediante una finestra di progettazione.  Per un esempio relativo all'aggiunta in fase di esecuzione di controlli con associazione a dati nei progetti di componenti aggiuntivi VSTO, vedere [Procedura dettagliata: data binding semplice in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere [Binding di dati a controlli contenuto di Word 2007 con Visual Studio Tools per Office System  \(3.0\)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## Aggiunta di un controllo a un documento in fase di progettazione  
  
#### Per popolare un documento con dati da un database  
  
1.  Aprire un progetto a livello di documento Word in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], con il documento aperto nella finestra di progettazione.  
  
2.  Aprire la finestra **Origini dati** e creare un'origine dati da un database.  Per altre informazioni, vedere [Procedura: connettersi ai dati di un database](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
3.  Trascinare il campo desiderato dalla finestra **Origini dati** nel documento.  
  
 Al documento viene aggiunto un controllo contenuto.  Il tipo di controllo contenuto dipende dal tipo di dati del campo selezionato.  Per altre informazioni, vedere [Controlli del contenuto](../vsto/content-controls.md).  
  
 È possibile aggiungere un controllo diverso selezionando il campo dati nella finestra **Origini dati** e scegliendo un controllo differente dall'elenco a discesa.  
  
## Oggetti del progetto  
 Oltre al controllo, gli oggetti relativi ai dati seguenti vengono aggiunti automaticamente al progetto:  
  
-   Un set di dati tipizzato che incapsula le tabelle dati a cui ci si è connessi nel database.  Per altre informazioni, vedere [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Un oggetto <xref:System.Windows.Forms.BindingSource> che connette il controllo al set di dati tipizzato.  Per altre informazioni, vedere [Cenni preliminari sul componente BindingSource](../Topic/BindingSource%20Component%20Overview.md).  
  
-   Un oggetto TableAdapter che connette il set di dati tipizzato al database.  Per altre informazioni, vedere [Cenni preliminari sugli oggetti TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
-   Un oggetto TableAdapterManager, usato per coordinare gli adattatori di tabella nel set di dati per attivare gli aggiornamenti gerarchici.  Per altre informazioni, vedere [Aggiornamento gerarchico](../data-tools/hierarchical-update.md) e [Panoramica di TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 Quando si esegue il progetto, il controllo visualizza il primo record dell'origine dati.  È possibile usare <xref:System.Windows.Forms.BindingSource> per consentire agli utenti di scorrere i record.  
  
#### Per scorrere i record  
  
-   Usare i metodi <xref:System.Windows.Forms.BindingSource> quali <xref:System.Windows.Forms.BindingSource.MoveNext%2A> e <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Per informazioni su come inviare aggiornamenti al set di dati tipizzato e al database, vedere [Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Procedura: Popolare documenti con i dati di oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Cenni preliminari sull'utilizzo di file di un database locale nelle soluzioni Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Connessione ai dati nelle applicazioni Windows Form](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Cenni preliminari sul componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
  