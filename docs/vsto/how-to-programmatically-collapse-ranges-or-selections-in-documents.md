---
title: "Procedura: Comprimere intervalli o selezioni in documenti a livello di codice | Microsoft Docs"
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
  - "selezioni, compressione"
  - "documenti [sviluppo per Office in Visual Studio], compressione degli intervalli"
  - "compressione di selezioni"
  - "intervalli, compressione"
  - "compressione di intervalli"
ms.assetid: 0bd059dd-8606-42ae-a8a9-97f8f3bd5cc5
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Procedura: Comprimere intervalli o selezioni in documenti a livello di codice
  Se si usa un oggetto <xref:Microsoft.Office.Interop.Word.Range> o <xref:Microsoft.Office.Interop.Word.Selection>, è possibile che si voglia modificare la selezione in un punto di inserimento prima di inserire il testo, per evitare la sovrascrittura del testo esistente. Gli oggetti <xref:Microsoft.Office.Interop.Word.Range> e <xref:Microsoft.Office.Interop.Word.Selection> dispongono di un metodo Collapse, che usa i valori di enumerazione <xref:Microsoft.Office.Interop.Word.WdCollapseDirection>:  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> comprime la selezione nella parte iniziale. Rappresenta il valore predefinito se non viene specificato un valore di enumerazione.  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> comprime la selezione nella parte finale.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Per comprimere un intervallo e inserire nuovo testo  
  
1.  Creare un oggetto <xref:Microsoft.Office.Interop.Word.Range> costituito dal primo paragrafo del documento.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#46)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#46)]  
  
2.  Usare il valore di enumerazione <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> per comprimere l'intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#47)]
     [!code-vb[Trin_VstcoreWordAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#47)]  
  
3.  Inserire il nuovo testo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#48](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#48)]
     [!code-vb[Trin_VstcoreWordAutomation#48](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#48)]  
  
4.  Selezionare <xref:Microsoft.Office.Interop.Word.Range>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#49)]
     [!code-vb[Trin_VstcoreWordAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#49)]  
  
 Se si usa il valore di enumerazione <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd>, il testo viene inserito all'inizio del paragrafo seguente.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#50)]
 [!code-vb[Trin_VstcoreWordAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#50)]  
  
 Contrariamente a quanto potrebbe prevedersi, la nuova frase non viene inserita prima del marcatore di paragrafo perché è incluso nell'intervallo originale. Per altre informazioni, vedere [Procedura: Escludere i segni di paragrafo durante l'inserimento di intervalli a livello di codice](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## Esempio di personalizzazione a livello di documento  
  
#### Per comprimere un intervallo in una personalizzazione a livello di documento  
  
1.  L'esempio seguente illustra il metodo completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#45)]  
  
## Esempio di componente aggiuntivo VSTO  
  
#### Per comprimere un intervallo in un componente aggiuntivo VSTO  
  
1.  L'esempio seguente illustra il metodo completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#45)]  
  
## Vedere anche  
 [Procedura: inserire testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: Recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Procedura: Escludere i segni di paragrafo durante l'inserimento di intervalli a livello di codice](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  
  