---
title: "Soluzioni Word | Microsoft Docs"
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
  - "soluzioni [sviluppo per Office in Visual Studio], Word"
  - "progetti di Office [sviluppo per Office in Visual Studio], Word"
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio], Word"
  - "Word [sviluppo per Office in Visual Studio]"
  - "progetti [sviluppo per Office in Visual Studio], Word"
  - "Word [sviluppo per Office in Visual Studio], informazioni su soluzioni Word"
  - "Soluzioni Office [sviluppo per Office in Visual Studio], Word"
  - "Word [sviluppo per Office in Visual Studio], componenti aggiuntivi a livello di applicazione "
  - "documenti [sviluppo per Office in Visual Studio], Word"
  - "sviluppo per Office in Visual Studio, soluzioni Word"
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], Word"
  - "Word [sviluppo per Office in Visual Studio], personalizzazioni a livello di documento"
  - "interfacce utente [sviluppo per Office in Visual Studio], Word"
  - "documenti di Office [sviluppo per Office in Visual Studio], Word"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], Word"
ms.assetid: ef339ad8-1897-4a44-b588-e6004d0b6d8b
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Soluzioni Word
  Visual Studio fornisce modelli di progetto che è possibile usare per creare personalizzazioni a livello di documento e componenti aggiuntivi VSTO per Microsoft Office Word. È possibile usare queste soluzioni per automatizzare Word, estenderne le funzionalità e personalizzarne l'interfaccia utente. Per altre informazioni sulle differenze tra personalizzazioni a livello di documento e componenti aggiuntivi VSTO, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 In questo argomento vengono fornite le seguenti informazioni:  
  
-   [Automazione di Word](#automating).  
  
-   [Sviluppo di personalizzazioni a livello di documento per Word](#doclevel).  
  
-   [Sviluppo di componenti aggiuntivi VSTO per Word](#applevel).  
  
-   [Personalizzazione dell'interfaccia utente di Word](#UI).  
  
##  <a name="automating"></a> Automazione di Word  
 Il modello a oggetti di Word espone diversi tipi che è possibile usare per automatizzare Word. Ad esempio, è possibile creare tabelle, formattare documenti e impostare testo in intervalli e paragrafi a livello di codice. Per altre informazioni, vedere [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md).  
  
 Quando si sviluppano soluzioni Word in Visual Studio, è anche possibile usare *elementi host* e *controlli host* nelle soluzioni. Si tratta di oggetti che estendono alcuni oggetti di uso comune nel modello a oggetti di Word, ad esempio gli oggetti <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.ContentControl>. Gli oggetti estesi si comportano come gli oggetti di Word su cui sono basati, ma aggiungono ulteriori eventi e funzionalità di data binding agli oggetti. Per altre informazioni, vedere [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Sviluppo di personalizzazioni a livello di documento per Word  
 Una personalizzazione a livello di documento per Microsoft Office Word è costituita da un assembly associato a un documento specifico. L'assembly in genere estende il documento personalizzando l'interfaccia utente e automatizzando Word. Diversamente da un componente aggiuntivo VSTO, associato a Word stesso, la funzionalità che si implementa in una personalizzazione è disponibile solo quando il documento associato è aperto in Word.  
  
 Per creare un progetto di personalizzazione a livello di documento per Word, usare il modello di progetto Documento di Word o Modello di Word nella finestra di dialogo **Nuovo progetto** di Visual Studio. Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Per altre informazioni sul funzionamento delle personalizzazioni a livello di documento, vedere [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
### Modello di programmazione delle personalizzazioni di Word  
 Quando si crea un progetto a livello di documento per Word, Visual Studio genera una classe denominata `ThisDocument`, che costituisce il fondamento della soluzione. Questa classe rappresenta il documento associato alla soluzione e fornisce un punto di partenza per la scrittura del codice.  
  
 Per altre informazioni sulla classe `ThisDocument` e su altre funzionalità che è possibile usare in un progetto a livello di documento, vedere [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Sviluppo di componenti aggiuntivi VSTO per Word  
 Un componente aggiuntivo VSTO per Microsoft Office Word è costituito da un assembly caricato da Word. L'assembly in genere estende Word personalizzando l'interfaccia utente e automatizzando Word. A differenza di una personalizzazione a livello di documento, associata a un documento specifico, la funzionalità implementata in un componente aggiuntivo VSTO non è limitata a un singolo documento.  
  
 Per creare un progetto di componente aggiuntivo VSTO per Word, usare i modelli di progetto di componente aggiuntivo di Word nella finestra di dialogo **Nuovo progetto** di Visual Studio. Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Per informazioni generali sul funzionamento dei componenti aggiuntivi VSTO, vedere [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### Modello di programmazione dei componenti aggiuntivi di Word  
 Quando si crea un progetto di componente aggiuntivo VSTO di Word, Visual Studio genera una classe denominata `ThisAddIn`, che costituisce il fondamento della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone anche il modello a oggetti di Word nel componente aggiuntivo VSTO.  
  
 Per altre informazioni sulla classe `ThisAddIn` e su altre funzionalità che è possibile usare in un componente aggiuntivo VSTO, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Personalizzazione dell'interfaccia utente di Word  
 Sono disponibili diverse modalità per personalizzare l'interfaccia utente di Word. Alcune opzioni sono disponibili per tutti i tipi di progetto e altre opzioni sono disponibili solo per i componenti aggiuntivi VSTO o le personalizzazioni a livello di documento.  
  
### Opzioni per tutti i tipi di progetto  
 La tabella seguente elenca le opzioni di personalizzazione disponibili per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Personalizzare la barra multifunzione.|[Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)|  
|Aggiungere controlli Windows Form o controlli di Word estesi al documento personalizzato \(per una personalizzazione a livello di documento\) o a qualsiasi documento aperto \(per un componente aggiuntivo VSTO\).|[Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Procedura: aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### Opzioni per le personalizzazioni a livello di documento  
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per le personalizzazioni a livello di documento.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Aggiungere un riquadro Azioni al documento.|[Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)<br /><br /> [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Aggiungere controlli XMLNode e XMLNodes estesi all'area del documento.|[Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### Opzioni per i componenti aggiuntivi VSTO  
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per i componenti aggiuntivi VSTO.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
  
### Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)|Fornisce una panoramica dei tipi principali forniti dal modello a oggetti di Word.|  
|[Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)|Fornisce informazioni sugli oggetti estesi \(forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]\) che è possibile usare nelle soluzioni Word.|  
|[Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Descrive come aggiungere controlli Windows Form ai documenti di Word.|  
|[Procedura dettagliata: creazione di una personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Illustra come creare una personalizzazione di base a livello di documento per Word.|  
|[Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Illustra come creare un componente aggiuntivo VSTO di base per Word.|  
|[Procedura dettagliata: Aggiunta di controlli a un documento in fase di esecuzione in un componente aggiuntivo VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Illustra come aggiungere un pulsante Windows Form e un oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a un documento in fase di esecuzione usando un componente aggiuntivo VSTO.|  
|[Word 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Fornisce collegamenti ad articoli e documentazione di riferimento sullo sviluppo di soluzioni Word \(non specifici dello sviluppo per Office tramite Visual Studio\).|  
  
  