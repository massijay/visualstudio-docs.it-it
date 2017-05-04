---
title: "Procedura: Aggiungere controlli ListObject a fogli di lavoro | Microsoft Docs"
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
  - "ListObject (controllo), aggiunta ai fogli di lavoro"
  - "controlli [sviluppo per Office in Visual Studio], aggiunta ai fogli di lavoro"
ms.assetid: 40788ecb-937f-4d2a-90ba-9c938e495b74
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Procedura: Aggiungere controlli ListObject a fogli di lavoro
  È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 È anche possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione nei progetti di componente aggiuntivo VSTO.  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli ListObject in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli ListObject in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per altre informazioni sui controlli <xref:Microsoft.Office.Tools.Excel.ListObject>, vedere [Controllo ListObject](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Aggiunta di controlli ListObject in fase di progettazione  
 Esistono diversi modi per aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro in un progetto a livello di documento in fase di progettazione: da Excel, dalla **casella degli strumenti** di Visual Studio e dalla finestra **Origini dati**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Per usare la barra multifunzione in Excel  
  
1.  Nel gruppo **Tabelle** della scheda **Inserisci** fare clic su **Tabella**.  
  
2.  Selezionare una o più celle da includere nell'elenco e fare clic su **OK**.  
  
#### Per usare la casella degli strumenti  
  
1.  Dalla scheda **Controlli Excel** della **casella degli strumenti** trascinare <xref:Microsoft.Office.Tools.Excel.ListObject> nel foglio di lavoro.  
  
     Viene visualizzata la finestra di dialogo **Aggiungi controllo ListObject**.  
  
2.  Selezionare una o più celle da includere nell'elenco e fare clic su **OK**.  
  
     Per modificare il nome predefinito, usare la finestra **Proprietà**.  
  
#### Per usare la finestra Origini dati  
  
1.  Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per altre informazioni, vedere [Procedura: connettersi ai dati di un database](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
2.  Trascinare una tabella dalla finestra **Origini dati** al foglio di lavoro.  
  
     Un controllo con associazione ai dati <xref:Microsoft.Office.Tools.Excel.ListObject> viene aggiunto al foglio di lavoro. Per altre informazioni, vedere [Associazione dati e Windows Form](../Topic/Data%20Binding%20and%20Windows%20Forms.md).  
  
##  <a name="runtimedoclevel"></a> Aggiunta di controlli ListObject in fase di esecuzione in un progetto a livello di documento  
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in modo dinamico in fase di esecuzione e creare in questo modo i controlli host in risposta a eventi. Gli oggetti elenco creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro è chiuso. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Per aggiungere un controllo ListObject a un foglio di lavoro a livello di codice  
  
1.  Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1` inserire il codice seguente per aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> alle celle da **A1** ad **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Aggiunta di controlli ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Gli oggetti elenco creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene salvato e chiuso. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Per aggiungere un controllo ListObject a un foglio di lavoro a livello di codice  
  
1.  Il codice seguente genera un elemento host del foglio di lavoro basato sul foglio di lavoro aperto, quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> alle celle da **A1** ad **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#8)]  
  
## Vedere anche  
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Controllo ListObject](../vsto/listobject-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: Ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  