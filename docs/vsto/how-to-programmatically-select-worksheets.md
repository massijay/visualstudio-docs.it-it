---
title: "Procedura: selezionare fogli di lavoro a livello di codice"
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
  - "progetti Excel, selezione di fogli di lavoro"
  - "fogli di lavoro, selezione"
ms.assetid: 9e7cdb11-e825-4c9f-abcd-d46fd20dc5e0
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Procedura: selezionare fogli di lavoro a livello di codice
  Il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> seleziona l'oggetto specificato e questa operazione sposta la selezione dell'utente al nuovo oggetto.  Usare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> se si vuole applicare lo stato attivo all'oggetto senza modificare la selezione dell'utente.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Se si vuole selezionare un foglio di lavoro esistente in un componente aggiuntivo VSTO o se il foglio di lavoro è stato creato in fase di esecuzione in una personalizzazione a livello di documento, è necessario accedervi usando la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Excel della cartella di lavoro di Excel, altrimenti è possibile accedere direttamente all'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>.  
  
## Uso dell'elemento host Worksheet  
 In una personalizzazione a livello di documento aggiungere il codice seguente a **Sheet1.vb** o **Sheet1.cs**.  
  
#### Per selezionare il primo foglio di lavoro in una cartella di lavoro usando un elemento host  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> di `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#19)]  
  
## Uso della raccolta Sheets della cartella di lavoro di Excel  
 Accedere al foglio di lavoro usando la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Excel.  
  
#### Per selezionare il primo foglio di lavoro in una cartella di lavoro usando la raccolta Sheets della cartella di lavoro di Excel  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> per selezionare il primo foglio di lavoro della cartella di lavoro attiva.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#20)]  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: stampa di fogli di lavoro a livello di codice](../vsto/how-to-programmatically-print-worksheets.md)   
 [Procedura: eliminare fogli di lavoro da una cartella di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Procedura: Nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Procedura: proteggere fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  