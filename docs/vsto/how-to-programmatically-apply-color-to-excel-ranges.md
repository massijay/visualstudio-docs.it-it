---
title: "Procedura: applicare il colore a intervalli di Excel a livello di codice"
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
  - "colore, intervalli di Excel"
  - "formattazione [sviluppo per Office in Visual Studio]"
  - "intervalli, applicazione di colore"
ms.assetid: a9c40229-5308-459a-9216-7e13d82c7cb5
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Procedura: applicare il colore a intervalli di Excel a livello di codice
  Per applicare un colore al testo all'interno di un intervallo di celle, utilizzare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> o un oggetto intervallo nativo di Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Utilizzo di un controllo NamedRange  
 Questo esempio è valido per personalizzazioni a livello di documento.  
  
#### Per applicare un colore a un controllo NamedRange  
  
1.  Creare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in corrispondenza della cella A1.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#65)]  
  
2.  Impostare il colore del testo nel controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#66)]  
  
## Utilizzo di intervalli nativi di Excel  
  
#### Per applicare un colore a un oggetto intervallo nativo di Excel  
  
1.  Creare un intervallo in corrispondenza della cella A1 e impostare il colore del testo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#67)]  
  
## Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Procedura: Applicare stili agli intervalli nei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: fare riferimento agli intervalli dei fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  