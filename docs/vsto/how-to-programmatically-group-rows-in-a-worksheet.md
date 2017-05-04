---
title: "Procedura: raggruppare righe in un foglio di lavoro a livello di codice | Microsoft Docs"
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
  - "colonne [sviluppo per Office in Visual Studio], annullamento del raggruppamento"
  - "gruppi"
  - "gruppi [sviluppo per Office in Visual Studio], cancellazione in fogli di lavoro"
  - "gruppi, creazione in fogli di lavoro"
  - "intervalli, creazione di gruppi"
  - "righe [sviluppo per Office in Visual Studio], annullamento del raggruppamento"
  - "fogli di lavoro, cancellazione di gruppi"
  - "fogli di lavoro, creazione di gruppi"
  - "fogli di lavoro, annullamento del raggruppamento di righe e colonne"
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Procedura: raggruppare righe in un foglio di lavoro a livello di codice
  È possibile raggruppare una o più righe intere.  Per creare un gruppo in un foglio di lavoro, utilizzare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> o un oggetto intervallo nativo di Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Utilizzo di un controllo NamedRange  
 Se si aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un progetto a livello di documento in fase di progettazione, è possibile utilizzare il controllo per creare un gruppo a livello di codice.  Nell'esempio seguente si presuppone che siano presenti tre controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> nello stesso foglio di lavoro: `data2001`, `data2002` e `dataAll`.  Ogni intervallo denominato fa riferimento a una riga intera nel foglio di lavoro.  
  
#### Per creare un gruppo di controlli NamedRange su un foglio di lavoro  
  
1.  Raggruppare tre intervalli denominati chiamando il metodo <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> di ciascun intervallo.  Il codice deve essere inserito in una classe Sheet e non nella classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Per separare le righe, chiamare il metodo <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A>.  
  
## Utilizzo di intervalli nativi di Excel  
 Nel codice si presuppone che siano presenti tre intervalli di Excel denominati `data2001`, `data2002` e `dataAll` in un foglio di lavoro.  
  
#### Per creare un gruppo di intervalli di Excel in un foglio di lavoro  
  
1.  Raggruppare tre intervalli denominati chiamando il metodo <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> di ciascun intervallo.  Nell'esempio seguente si presuppone che siano presenti tre controlli <xref:Microsoft.Office.Interop.Excel.Range> denominati `data2001`, `data2002` e `dataAll` nello stesso foglio di lavoro.  Ogni intervallo denominato fa riferimento a una riga intera nel foglio di lavoro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Per separare le righe, chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A>.  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  