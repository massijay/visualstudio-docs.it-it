---
title: "Procedura: Nascondere i fogli di lavoro a livello di codice"
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
  - "fogli di lavoro nascosti"
  - "fogli di lavoro, nascondere"
ms.assetid: 3208f633-137f-47f9-9c9c-2cf8e3c72096
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Procedura: Nascondere i fogli di lavoro a livello di codice
  È possibile mostrare o nascondere qualsiasi foglio di lavoro da una cartella di lavoro. Per nascondere un foglio di lavoro, usare l'elemento host Worksheet o accedere al foglio di lavoro usando la raccolta Sheets della cartella di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Uso dell'elemento host Worksheet  
 Se il foglio di lavoro è stato aggiunto in fase di progettazione in una personalizzazione a livello di documento, per nasconderlo usare la proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A>.  
  
#### Per nascondere un foglio di lavoro usando un elemento host Worksheet  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> dell'elemento host `Sheet1` sul valore di enumerazione <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#25)]  
  
## Uso della raccolta Sheets della cartella di lavoro di Excel  
 Accedere ai fogli di lavoro mediante la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Microsoft Office Excel nei casi seguenti:  
  
-   Se si intende nascondere un foglio di lavoro in un componente aggiuntivo VSTO  
  
-   Se il foglio di lavoro che si vuole nascondere è stato creato in fase di esecuzione in una personalizzazione a livello di documento  
  
#### Per nascondere un foglio di lavoro usando la raccolta Sheets della cartella di lavoro di Excel  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> del foglio di lavoro sul valore di enumerazione <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#26)]  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: eliminare fogli di lavoro da una cartella di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Procedura: Spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Procedura: proteggere fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  