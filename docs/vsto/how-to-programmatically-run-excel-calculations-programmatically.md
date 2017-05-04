---
title: "Procedura: eseguire calcoli in Excel a livello di codice | Microsoft Docs"
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
  - "calcoli, esecuzione in Excel"
  - "Excel [sviluppo per Office in Visual Studio], esecuzione di calcoli a livello di codice"
  - "intervalli, esecuzione di calcoli"
  - "cartelle di lavoro, esecuzione di calcoli"
ms.assetid: 0bf30d93-8620-43ad-bfb8-f45bf3b5461f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Procedura: eseguire calcoli in Excel a livello di codice
  Un processo simile viene utilizzato per eseguire i calcoli in un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> o in un oggetto intervallo nativo di Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Esecuzione di calcoli in un controllo NamedRange  
 Nell'esempio seguente viene creato un oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> in corrispondenza della cella A1 e, successivamente, tale cella viene calcolata.  Il codice deve essere inserito in una classe Sheet e non nella classe `ThisWorkbook`.  
  
#### Per eseguire calcoli in un controllo NamedRange  
  
1.  Creare l'intervallo denominato.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#75)]  
  
2.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> dell'intervallo specificato.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#76)]  
  
## Esecuzione di calcoli in un intervallo nativo di Excel  
  
#### Per eseguire i calcoli in un intervallo nativo di Excel  
  
1.  Creare l'intervallo denominato.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#30)]  
  
2.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> dell'intervallo specificato.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#31)]  
  
## Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  