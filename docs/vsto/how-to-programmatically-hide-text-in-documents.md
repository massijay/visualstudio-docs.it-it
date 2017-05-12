---
title: "Procedura: Nascondere il testo nei documenti a livello di codice"
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
  - "documenti [sviluppo per Office in Visual Studio], nascondere testo"
  - "testo [sviluppo per Office in Visual Studio], nascondere nei documenti"
ms.assetid: f5ced4ec-22ca-463b-b963-d34ce631b486
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura: Nascondere il testo nei documenti a livello di codice
  È possibile nascondere testo in un documento impostando la proprietà <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> di un controllo <xref:Microsoft.Office.Interop.Word.Range.Font%2A> per un intervallo di testo determinato.  
  
 È possibile, ad esempio, nascondere temporaneamente il testo all'interno di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> \(in una personalizzazione a livello di documento\) o un <xref:Microsoft.Office.Interop.Word.Bookmark> \(in un componente aggiuntivo VSTO\) prima di inviare un documento a una stampante.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Per nascondere testo in un controllo Bookmark mentre si stampa il documento  
  
1.  Creare una routine che nasconda tutto il testo che rientra in un intervallo specificato.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#105](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#105)]
     [!code-vb[Trin_VstcoreWordAutomation#105](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#105)]  
  
2.  Creare una routine che scopra tutto il testo che rientra in un intervallo specificato.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#106](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#106)]
     [!code-vb[Trin_VstcoreWordAutomation#106](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#106)]  
  
3.  Passare l'intervallo di un segnalibro al metodo `HideText`, stampare il documento e quindi passare lo stesso intervallo al metodo `UnhideText`.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento. Per usare questo esempio, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomation#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#107)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo. Per usare l'esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#107)]  
  
## Compilazione del codice  
 Questo esempio di codice presuppone che il documento contenga un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> \(in una personalizzazione a livello di documento\) o un controllo <xref:Microsoft.Office.Interop.Word.Bookmark> \(in un componente aggiuntivo VSTO\) denominato `bookmark1`.  
  
## Vedere anche  
 [Procedura: Stampare documenti a livello di codice](../vsto/how-to-programmatically-print-documents.md)   
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Procedura: aggiornare testo di segnalibro a livello di codice](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  