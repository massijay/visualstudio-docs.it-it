---
title: "Procedura: copiare fogli di lavoro a livello di codice | Microsoft Docs"
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
  - "Excel [sviluppo per Office in Visual Studio], copia di fogli di lavoro"
  - "fogli di lavoro, copia"
ms.assetid: e49e03f5-7b2f-416b-b5fe-0965336c47e1
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Procedura: copiare fogli di lavoro a livello di codice
  È possibile creare una copia di un foglio di lavoro e inserirla prima o dopo un foglio di lavoro esistente nella cartella di lavoro.  e non si specifica dove inserire il foglio di lavoro, Excel crea una nuova cartella di lavoro per il nuovo foglio di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Indipendentemente dal fatto che il foglio di lavoro venga copiato a livello di codice o manualmente dall'utente finale, non è presente codice nel nuovo foglio di lavoro e i controlli presenti sul nuovo foglio non funzionano  perché il foglio di lavoro appena copiato è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> e non un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>.  I controlli Windows Form e i controlli host possono essere aggiunti solo agli elementi host.  Per altre informazioni, vedere [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### Per aggiungere una copia di un foglio di lavoro a una cartella di lavoro in una personalizzazione a livello di documento  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> per copiare il primo foglio nella cartella di lavoro corrente e inserire la copia dopo il terzo foglio.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#16)]  
  
### Per aggiungere una copia di un foglio di lavoro a una cartella di lavoro in un componente aggiuntivo VSTO  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> per copiare il primo foglio nella cartella di lavoro corrente e inserire la copia dopo il terzo foglio.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Procedura: eliminare fogli di lavoro da una cartella di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Procedura: selezionare fogli di lavoro a livello di codice](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  