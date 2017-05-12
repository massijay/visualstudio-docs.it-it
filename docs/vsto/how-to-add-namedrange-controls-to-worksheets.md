---
title: "Procedura: aggiungere controlli NamedRange a fogli di lavoro"
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
  - "intervalli, aggiunta a fogli di lavoro"
  - "NamedRange (controllo), aggiunta ai fogli di lavoro"
  - "controlli [sviluppo per Office in Visual Studio], aggiunta ai fogli di lavoro"
ms.assetid: da7ec48f-92cb-4fa3-b3e2-447c238d17a8
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Procedura: aggiungere controlli NamedRange a fogli di lavoro
  È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 È anche possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> in fase di esecuzione nei progetti di componente aggiuntivo VSTO.  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli NamedRange in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli NamedRange in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli NamedRange in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per altre informazioni sui controlli <xref:Microsoft.Office.Tools.Excel.NamedRange>, vedere [Controllo NamedRange](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Aggiunta di controlli NamedRange in fase di progettazione  
 Esistono diversi modi per aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro in un progetto a livello di documento in fase di progettazione: da Excel, dalla **casella degli strumenti** di Visual Studio e dalla finestra **Origini dati**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Per aggiungere un controllo NamedRange a un foglio di lavoro usando la casella Nome in Excel  
  
1.  Selezionare una o più celle da includere nell'intervallo denominato.  
  
2.  Nella casella **Nome** digitare un nome per l'intervallo e premere INVIO.  
  
     La casella **Nome** si trova accanto alla barra della formula, sopra la colonna **A** del foglio di lavoro.  
  
#### Per aggiungere un controllo NamedRange a un foglio di lavoro con la Casella degli strumenti  
  
1.  Aprire la **Casella degli strumenti** e fare clic sulla scheda **Controlli Excel**.  
  
2.  Fare clic su <xref:Microsoft.Office.Tools.Excel.NamedRange> e trascinarlo in un foglio di lavoro.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi controllo NamedRange**.  
  
3.  Selezionare una o più celle da includere nell'intervallo denominato.  
  
4.  Fare clic su **OK**.  
  
     Se non si vuole assegnare al controllo il nome predefinito, è possibile modificarlo nella finestra **Proprietà**.  
  
#### Per aggiungere un controllo NamedRange a un foglio di lavoro con la finestra Origini dati  
  
1.  Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per altre informazioni, vedere [Procedura: connettersi ai dati di un database](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
2.  Trascinare un singolo campo dalla finestra **Origini dati** al foglio di lavoro.  
  
     Un controllo con associazione ai dati <xref:Microsoft.Office.Tools.Excel.NamedRange> viene aggiunto al foglio di lavoro. Per altre informazioni, vedere [Associazione dati e Windows Form](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
##  <a name="runtimedoclevel"></a> Aggiunta di controlli NamedRange in fase di esecuzione in un progetto a livello di documento  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a livello di codice al foglio di lavoro in fase di esecuzione e creare in questo modo i controlli host in risposta a eventi. Gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Per aggiungere un controllo NamedRange a un foglio di lavoro a livello di codice  
  
1.  Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1` inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> alla cella **A1** e impostarne la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> su `Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Aggiunta di controlli NamedRange in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Per aggiungere un controllo NamedRange a un foglio di lavoro a livello di codice  
  
1.  Il codice seguente genera un elemento host del foglio di lavoro basato sul foglio di lavoro aperto, quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> alla cella **A1** e ne imposta la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> su `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#7)]  
  
## Vedere anche  
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  