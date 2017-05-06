---
title: "Procedura: aggiungere controlli Chart a fogli di lavoro"
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
  - "Chart (controllo) [sviluppo per Office in Visual Studio], aggiunta a fogli di lavoro"
  - "controlli [sviluppo per Office in Visual Studio], aggiunta a fogli di lavoro"
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Procedura: aggiungere controlli Chart a fogli di lavoro
  È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.Chart> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nelle personalizzazioni a livello di documento.  È anche possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.Chart> in fase di esecuzione nei componenti aggiuntivi VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli Chart in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli Chart in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli Chart in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per altre informazioni sui controlli <xref:Microsoft.Office.Tools.Excel.Chart>, vedere [Controllo Chart](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Aggiunta di controlli Chart in fase di progettazione  
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart> al foglio di lavoro nello stesso modo in cui si aggiunge un grafico dall'interno dell'applicazione.  
  
> [!NOTE]  
>  Il controllo <xref:Microsoft.Office.Tools.Excel.Chart> non è disponibile nella **Casella degli strumenti** né nella finestra **Origini dati**.  
  
#### Per aggiungere un controllo host Chart a un foglio di lavoro in Excel  
  
1.  Nella scheda **Inserisci** del gruppo **Grafici** fare clic su **Colonna**, fare clic su una categoria di grafici e quindi fare clic sul tipo di grafico desiderato.  
  
2.  Nella finestra di dialogo **Inserisci grafico** fare clic su **OK**.  
  
3.  Nella scheda **Progettazione** fare clic su **Seleziona dati** nel gruppo **Dati**.  
  
4.  Nella finestra di dialogo **Seleziona origine dati** fare clic nella casella **Intervallo datigrafico** e deselezionare eventuali selezioni predefinite.  
  
5.  Nel foglio **Dati per grafico** selezionare l'intervallo di celle contenente i dati per il grafico \(celle da **A5** a **D8**\).  
  
6.  Nella finestra di dialogo **Seleziona origine dati** fare clic su **OK**.  
  
##  <a name="runtimedoclevel"></a> Aggiunta di controlli Chart in fase di esecuzione in un progetto a livello di documento  
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart> in modo dinamico in fase di esecuzione.  I grafici creati dinamicamente non vengono salvati in modo permanente nel documento come controlli host quando il documento viene chiuso.  Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice  
  
1.  Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1` inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Aggiunta di controlli Chart in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.Chart> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO.  Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 I controlli Chart creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene chiuso.  Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice  
  
1.  Il codice seguente genera un elemento host foglio di lavoro basato sul foglio di lavoro aperto e quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#9)]  
  
## Compilazione del codice  
 L'esempio prevede i requisiti seguenti:  
  
-   Dati da usare per creare il grafico, archiviati nell'intervallo da A5 a D8 nel foglio di lavoro.  
  
## Vedere anche  
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Controllo Chart](../vsto/chart-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  