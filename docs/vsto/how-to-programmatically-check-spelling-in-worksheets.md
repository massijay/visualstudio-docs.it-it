---
title: "Procedura: Eseguire il controllo ortografico nei fogli di lavoro a livello di codice | Microsoft Docs"
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
  - "correttore ortografico"
  - "correttore ortografico, fogli di lavoro"
  - "fogli di lavoro, correttore ortografico"
  - "ortografia, controllo nei fogli di lavoro"
ms.assetid: 16367c5d-2075-4174-bb87-dfc59f02c84c
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Procedura: Eseguire il controllo ortografico nei fogli di lavoro a livello di codice
  A livello di codice è possibile eseguire il controllo ortografico delle parole in un foglio di lavoro. La finestra di dialogo **Controllo ortografia** viene visualizzata automaticamente se si sono parole formulate in modo non corretto nel foglio di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Per controllare l'ortografia in un foglio di lavoro in una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> del foglio di lavoro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#45)]  
  
### Per controllare l'ortografia in un foglio di lavoro in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> del foglio di lavoro attivo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#22)]  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: eseguire calcoli in Excel a livello di codice](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  