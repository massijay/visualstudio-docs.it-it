---
title: "Procedura: memorizzare e recuperare valori di data in intervalli di Excel a livello di codice"
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
  - "data (valori)"
  - "data (valori), memorizzazione in intervalli di Excel"
  - "date, recupero da intervalli di Excel"
  - "date, memorizzazione in intervalli di Excel"
  - "Excel [sviluppo per Office in Visual Studio], recupero di valori di date da intervalli"
  - "Excel [sviluppo per Office in Visual Studio], memorizzazione di valori di date in intervalli"
  - "intervalli, recupero di valori di date"
  - "intervalli, memorizzazione di valori di date"
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Procedura: memorizzare e recuperare valori di data in intervalli di Excel a livello di codice
  È possibile memorizzare e recuperare valori in un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> o in un oggetto dell'intervallo nativo di Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Se si archivia un valore data che cade il 1\/1\/1900 o dopo tale data tramite gli strumenti di sviluppo di Office in Visual Studi, tale valore verrà memorizzato in formato automazione OLE \(OA\).  È necessario utilizzare il metodo <xref:System.DateTime.FromOADate%2A> per recuperare il valore delle date in formato automazione OLE \(OA\).  Se la data è precedente al 1\/1\/1900, viene memorizzata come stringa.  
  
> [!NOTE]  
>  Le date di Excel differiscono dalle date dell'automazione OLE per i primi due mesi del 1900.  Esistono inoltre differenze se l'opzione del **sistema di date del 1904** è selezionata.  Negli esempi di codice riportati di seguito non vengono annoverate queste differenze.  
  
## Utilizzo di un controllo NamedRange  
  
-   Questo esempio è valido per personalizzazioni a livello di documento.  Inserire il codice seguente in una classe Sheet, non nella classe `ThisWorkbook`.  
  
#### Per memorizzare un valore di data in un intervallo denominato  
  
1.  Creare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> nella cella **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#50)]  
  
2.  Impostare la data odierna come valore di `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#51)]  
  
#### Per recuperare un valore di data da un intervallo denominato  
  
1.  Recuperare il valore di data da `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#52)]  
  
## Utilizzo di intervalli nativi di Excel  
  
#### Per memorizzare un valore di data in un oggetto intervallo nativo di Excel  
  
1.  Creare un oggetto <xref:Microsoft.Office.Interop.Excel.Range> che rappresenta la cella **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
2.  Impostare la data odierna come valore di `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
#### Per recuperare un valore di data da un oggetto intervallo nativo di Excel  
  
1.  Recuperare il valore di data da `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
## Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Procedura: fare riferimento agli intervalli dei fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  