---
title: "Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice"
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
  - "cartelle di lavoro, aggiunta di fogli di lavoro"
  - "cartelle di lavoro, creazione di fogli di lavoro"
  - "fogli di lavoro, creazione"
  - "fogli di lavoro, aggiunta a cartelle di lavoro"
ms.assetid: 19f0d815-51b2-406c-9f36-34aa0ec16b4a
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice
  È possibile creare un foglio di lavoro a livello di codice, quindi aggiungerlo alla raccolta di fogli di lavoro nella cartella di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Per aggiungere un nuovo foglio di lavoro a una cartella di lavoro in una personalizzazione a livello di documento  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#15)]  
  
     Il nuovo foglio di lavoro è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo e non un elemento host. Per aggiungere un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>, aggiungere il foglio di lavoro in fase di progettazione.  
  
### Per aggiungere un nuovo foglio di lavoro a una cartella di lavoro in un componente aggiuntivo VSTO  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
     Il nuovo foglio di lavoro è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo e non un elemento host. È anche possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> dall'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: eliminare fogli di lavoro da una cartella di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Procedura: selezionare fogli di lavoro a livello di codice](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  