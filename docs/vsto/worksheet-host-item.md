---
title: "Elemento host Worksheet | Microsoft Docs"
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
  - "elementi host [sviluppo per Office in Visual Studio], foglio di lavoro"
  - "Excel [sviluppo per Office in Visual Studio], fogli di lavoro"
  - "Worksheet (elementi host)"
  - "fogli di lavoro, eventi"
  - "Worksheet (elementi host), eventi"
  - "fogli di lavoro di Excel"
  - "fogli di lavoro, Excel"
  - "fogli di lavoro"
  - "eventi [sviluppo per Office in Visual Studio]"
ms.assetid: b4f7c501-81f5-409e-aa1b-748f010798b9
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Elemento host Worksheet
  L'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> è un tipo che estende il tipo <xref:Microsoft.Office.Interop.Excel.Worksheet> dall'assembly di interoperabilità primario per Excel. L'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> offre tutte le stesse proprietà, gli stessi metodi ed eventi di un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet>, ma espone anche eventi aggiuntivi e funge da contenitore per i controlli host e quelli Windows Form.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Nei progetti a livello di documento è possibile aggiungere elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> al progetto in fase di progettazione. Nei progetti di componente aggiuntivo VSTO è possibile generare elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione.  
  
## Informazioni sugli elementi host Worksheet nei progetti a livello di documento  
 Quando si crea un progetto a livello di documento per Excel, Visual Studio automaticamente crea tre elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> nel progetto. I nomi predefiniti dei fogli di lavoro sono `Sheet1`, `Sheet2` e `Sheet3`. Se si crea un progetto in base a una cartella di lavoro esistente, il numero di elementi host dipende dal numero di fogli di lavoro nella cartella di lavoro.  
  
 Queste classi del foglio di lavoro offrono l'accesso ai membri dell'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> per eseguire attività di base nella personalizzazione, come ad esempio la modifica dei contenuti in un foglio di lavoro. È anche possibile usare queste classi per aggiungere controlli ai fogli di lavoro. Con la combinazione di set di controlli diversi e con la scrittura di codice, è possibile associare i controlli ai dati, raccogliere le informazioni relative all'utente e rispondere alle azioni utente. Per altre informazioni, vedere [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).  
  
 Le classi del foglio di lavoro offrono un punto di partenza per iniziare a scrivere codice nel progetto. Dal momento che la classe offre tutte le stesse proprietà, gli stessi metodi ed eventi dell'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nell'assembly di interoperabilità primario per Excel, è possibile usare anche queste classi per accedere al modello a oggetti di Excel. Per altre informazioni, vedere [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md).  
  
 Nei progetti a livello di documento è possibile aggiungere elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> aggiuntivi al progetto in fase di progettazione aggiungendo un nuovo foglio di lavoro nella finestra di progettazione.  
  
### Ridenominazione dei fogli di lavoro  
 In un progetto a livello di documento è possibile rinominare i fogli di lavoro nella finestra di progettazione di Visual Studio, ma in tal modo viene modificato solo il nome visualizzato del foglio di lavoro. Il nome a livello di codice rimane il nome predefinito del foglio di lavoro. Se si rinomina il foglio di lavoro nella finestra **Proprietà**, viene modificato solo il nome a livello di codice.  
  
### Limitazioni dell'elemento host Worksheet nei progetti a livello di documento  
 Non è possibile creare nuovi elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione in un progetto a livello di documento. Se si crea un nuovo foglio di lavoro Excel in fase di esecuzione, sarà di tipo <xref:Microsoft.Office.Interop.Excel.Worksheet>. Dal momento che non si tratta di un elemento host, non può contenere alcun controllo host o controllo Windows Form. Per altre informazioni sulla creazione di documenti in fase di esecuzione, vedere [Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## Informazioni sugli elementi host Worksheet in progetti di componente aggiuntivo VSTO  
 Nei progetti a livello di applicazione è possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione per qualsiasi foglio di lavoro in Excel. È possibile usare l'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> per aggiungere controlli al foglio di lavoro associato oppure per gestire eventi che non sono disponibili su oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet>.  
  
 Per generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>, usare il metodo GetVstoObject. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Vedere anche  
 [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  