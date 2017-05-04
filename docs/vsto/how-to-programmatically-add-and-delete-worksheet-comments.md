---
title: "Procedura: Aggiungere ed eliminare commenti in un foglio di lavoro a livello di codice | Microsoft Docs"
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
  - "intervalli, commenti"
  - "fogli di lavoro, commenti"
  - "commenti, fogli di lavoro"
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Procedura: Aggiungere ed eliminare commenti in un foglio di lavoro a livello di codice
  È possibile aggiungere ed eliminare commenti a livello di codice nei fogli di lavoro di Microsoft Office Excel. I commenti possono essere aggiunti solo a singole celle, non a intervalli con più celle.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Aggiunta ed eliminazione di un commento in un progetto a livello di documento  
 Gli esempi seguenti presuppongono la presenza di un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a cella singola denominato `dateComment` in un foglio di lavoro denominato `Sheet1`.  
  
#### Per aggiungere un nuovo commento a un intervallo denominato  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> e fornire il testo del commento. Questo codice deve essere inserito nella classe `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#30)]  
  
#### Per eliminare un commento da un intervallo denominato  
  
1.  Verificare l'esistenza di un commento nell'intervallo ed eliminarlo. Questo codice deve essere inserito nella classe `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#29)]  
  
## Aggiunta ed eliminazione di un commento in un progetto di componente aggiuntivo VSTO  
 Gli esempi seguenti presuppongono la presenza di un oggetto <xref:Microsoft.Office.Interop.Excel.Range> a cella singola denominato `dateComment` nel foglio di lavoro attivo.  
  
#### Per aggiungere un nuovo commento a un intervallo di Excel  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> dell'oggetto <xref:Microsoft.Office.Interop.Excel.Range> e fornire il testo del commento.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
#### Per eliminare un commento da un intervallo di Excel  
  
1.  Verificare l'esistenza di un commento nell'intervallo ed eliminarlo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: Visualizzare commenti in un foglio di lavoro a livello di codice](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)  
  
  