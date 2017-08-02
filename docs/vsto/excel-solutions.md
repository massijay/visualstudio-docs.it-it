---
title: "Soluzioni Excel"
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
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio], Excel"
  - "Excel [sviluppo per Office in Visual Studio], componenti aggiuntivi a livello di applicazione"
  - "soluzioni Office [sviluppo per Office in Visual Studio], Excel"
  - "soluzioni [sviluppo per Office in Visual Studio], Excel"
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], Excel"
  - "Excel [sviluppo per Office in Visual Studio], informazioni su soluzioni Excel"
  - "Excel [sviluppo per Office in Visual Studio]"
  - "documenti [sviluppo per Office in Visual Studio], Excel"
  - "documenti di Office [sviluppo per Office in Visual Studio], Excel"
  - "progetti [sviluppo per Office in Visual Studio], Excel"
  - "Excel [sviluppo per Office in Visual Studio], personalizzazioni a livello di documento"
  - "interfacce utente [sviluppo per Office in Visual Studio], Excel"
  - "sviluppo per Office in Visual Studio, soluzioni Excel"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], Excel"
  - "progetti di Office [sviluppo per Office in Visual Studio], Excel"
ms.assetid: 34444d54-d7b6-479a-b5b7-a946267081e9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Soluzioni Excel
  Visual Studio fornisce modelli di progetto che è possibile usare per creare personalizzazioni a livello di documento e componenti aggiuntivi VSTO per Microsoft Office Excel. È possibile usare queste soluzioni per automatizzare Excel, estenderne le funzionalità e personalizzarne l'interfaccia utente. Per altre informazioni sulle differenze tra personalizzazioni a livello di documento e componenti aggiuntivi VSTO, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 In questo argomento vengono fornite le seguenti informazioni:  
  
-   [Automazione di Excel](#automating)  
  
-   [Sviluppo di personalizzazioni a livello di documento per Excel](#doclevel).  
  
-   [Sviluppo di componenti aggiuntivi VSTO per Excel](#applevel).  
  
-   [Personalizzazione dell'interfaccia utente di Excel](#UI).  
  
##  <a name="automating"></a> Automazione di Excel  
 Il modello a oggetti di Excel espone diversi tipi che è possibile usare per automatizzare Excel. Ad esempio, è possibile creare grafici, formattare fogli di lavoro e impostare i valori degli intervalli e delle celle a livello di codice. Per altre informazioni, vedere [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md).  
  
 Quando si sviluppano soluzioni Excel in Visual Studio, si possono anche usare *elementi host* e *controlli host* nelle soluzioni. Si tratta di oggetti che estendono alcuni oggetti di uso comune nel modello a oggetti di Excel, ad esempio gli oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet> e <xref:Microsoft.Office.Interop.Excel.Range>. Gli oggetti estesi si comportano come gli oggetti di Excel sui quali si basano, ma aggiungono ulteriori eventi e funzionalità di data binding agli oggetti. Per altre informazioni, vedere [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Sviluppo di personalizzazioni a livello di documento per Excel  
 Una personalizzazione a livello di documento per Microsoft Office Excel è costituita da un assembly associato a una cartella di lavoro specifica. L'assembly in genere estende la cartella di lavoro personalizzando l'interfaccia utente e automatizzando Excel. Diversamente da un componente aggiuntivo VSTO a livello di applicazione, associato a Excel stesso, la funzionalità che si implementa in una personalizzazione è disponibile solo quando la cartella di lavoro associata è aperta in Excel.  
  
 Per creare un progetto relativo alla personalizzazione a livello di documento per Excel, usare i modelli di progetto relativi alla cartella di lavoro o al modello di Excel nella finestra di dialogo **Nuovo progetto** di Visual Studio. Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Per altre informazioni sul funzionamento delle personalizzazioni a livello di documento, vedere [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
### Modello di programmazione delle personalizzazioni di Excel  
 Quando si crea un progetto a livello di documento per Excel, in Visual Studio vengono generate diverse classi che costituiscono il fondamento della soluzione: `ThisWorkbook`, `Sheet1`, `Sheet2` e `Sheet3`. Queste classi rappresentano la cartella di lavoro e fogli di lavoro associati alla soluzione e forniscono un punto di partenza per la scrittura del codice.  
  
 Per altre informazioni su queste classi generate e su altre funzionalità che è possibile usare in un progetto a livello di documento, vedere [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Sviluppo di componenti aggiuntivi VSTO per Excel  
 Un componente aggiuntivo VSTO per Microsoft Office Excel è costituito da un assembly caricato da Excel. L'assembly in genere estende Excel personalizzando l'interfaccia utente e automatizzando Excel. A differenza di una personalizzazione a livello di documento, associata a una cartella di lavoro specifica, la funzionalità implementata in un componente aggiuntivo VSTO non è limitata a una singola cartella di lavoro.  
  
 Per creare un progetto di componente aggiuntivo VSTO per Excel, usare i modelli di progetto relativi alla cartella di lavoro o al modello di Excel nella finestra di dialogo **Nuovo progetto** di Visual Studio. Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Per informazioni generali sul funzionamento dei componenti aggiuntivi VSTO, vedere [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 ![Collegamento a video](~/docs/data-tools/media/playvideo.gif "Collegamento a video") Per una dimostrazione video correlata, vedere la [procedura per automatizzare PowerPoint da un componente aggiuntivo di Excel](http://go.microsoft.com/fwlink/?LinkID=130300).  
  
### Modello di programmazione dei componenti aggiuntivi di Excel  
 Quando si crea un progetto di componente aggiuntivo VSTO per Excel, Visual Studio genera una classe, chiamata `ThisAddIn`, che costituisce la base della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone anche il modello a oggetti di Excel nel componente aggiuntivo VSTO.  
  
 Per altre informazioni sulla classe `ThisAddIn` e su altre funzionalità di Visual Studio che è possibile usare in un componente aggiuntivo VSTO, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Personalizzazione dell'interfaccia utente di Excel  
 Sono disponibili diverse modalità per personalizzare l'interfaccia utente di Excel. Alcune opzioni sono disponibili per tutti i tipi di progetto e altre opzioni sono disponibili solo per i componenti aggiuntivi VSTO o le personalizzazioni a livello di documento.  
  
### Opzioni per tutti i tipi di progetto  
 La tabella seguente elenca le opzioni di personalizzazione disponibili per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Personalizzare la barra multifunzione.|[Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)|  
|Aggiungere controlli Windows Form o controlli estesi di Excel a un foglio di lavoro della cartella di lavoro personalizzata per una personalizzazione a livello di documento, o in qualsiasi cartella di lavoro aperta per un componente aggiuntivo VSTO.|[Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Procedura: aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### Opzioni per le personalizzazioni a livello di documento  
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per le personalizzazioni a livello di documento.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Aggiunta di un riquadro delle azioni alla cartella di lavoro.|[Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)<br /><br /> [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Aggiungere a un foglio di lavoro controlli di intervallo esteso mappati ai nodi XML.|[Procedura: aggiungere controlli XMLMappedRange a fogli di lavoro](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### Opzioni per i componenti aggiuntivi VSTO  
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per i componenti aggiuntivi VSTO.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
  
### Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)|Fornisce una panoramica dei tipi principali forniti dal modello a oggetti di Excel..|  
|[Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)|Fornisce informazioni sugli oggetti estesi \(forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]\) che è possibile usare nelle soluzioni Excel.|  
|[Globalizzazione e localizzazione di soluzioni di Excel](../vsto/globalization-and-localization-of-excel-solutions.md)|Contiene considerazioni speciali per le soluzioni Excel eseguite in computer che hanno impostazioni di Windows non in inglese.|  
|[Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Descrive come è possibile aggiungere controlli Windows Form ai fogli di lavoro di Excel.|  
|[Procedura dettagliata: creazione di una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Illustra come creare una personalizzazione di base a livello di documento per Excel.|  
|[Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Mostra come creare un componente aggiuntivo VSTO di base per Excel.|  
|[Procedura dettagliata: Aggiunta di controlli a un foglio di lavoro in fase di esecuzione in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|Illustra come aggiungere un pulsante di Windows Form, <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro in fase di esecuzione con un componente aggiuntivo VSTO.|  
|[Excel 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199011)|Fornisce collegamenti ad articoli e documentazione di riferimento sullo sviluppo di soluzioni Excel. Gli articoli non sono specifici per lo sviluppo di Office usando Visual Studio.|  
  
  