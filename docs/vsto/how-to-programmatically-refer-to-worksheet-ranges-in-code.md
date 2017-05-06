---
title: "Procedura: fare riferimento agli intervalli dei fogli di lavoro nel codice a livello di codice"
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
  - "Excel [sviluppo per Office in Visual Studio], riferimento a intervalli dei fogli di lavoro"
  - "intervalli, riferimento"
  - "riferimento a intervalli dei fogli di lavoro"
  - "fogli di lavoro, riferimento a intervalli"
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Procedura: fare riferimento agli intervalli dei fogli di lavoro nel codice a livello di codice
  Un processo simile viene utilizzato per fare riferimento al contenuto di un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> o a un oggetto intervallo nativo di Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Utilizzo di un controllo NamedRange  
 Nell'esempio seguente viene aggiunto un oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro, quindi viene aggiunto il testo alla cella dell'intervallo.  
  
#### Per fare riferimento a un controllo NamedRange  
  
1.  Assegnare una stringa alla proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>.  Il codice deve essere inserito in una classe Sheet e non nella classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#46)]  
  
## Utilizzo di intervalli nativi di Excel  
 Nell'esempio seguente viene aggiunto un intervallo nativo di Excel a un foglio di lavoro, quindi viene aggiunto il testo alla cella dell'intervallo.  
  
#### Per fare riferimento a un oggetto intervallo nativo  
  
1.  Assegnare una stringa alla proprietà <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> dell'intervallo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#47)]  
  
## Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Procedura: Eseguire il controllo ortografico nei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Procedura: Applicare stili agli intervalli nei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: riempire automaticamente gli intervalli con dati modificati in modo incrementale a livello di codice](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Procedura: cercare testo negli intervalli dei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  