---
title: "Procedura: aggiornare testo di segnalibro a livello di codice"
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
  - "Bookmark (controllo), aggiornamento di contenuti"
  - "segnalibri, aggiornamento di testo"
  - "testo [sviluppo per Office in Visual Studio], aggiornamento in segnalibri"
ms.assetid: 2324164d-2538-4695-9aaf-7285ce403be3
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Procedura: aggiornare testo di segnalibro a livello di codice
  È possibile inserire testo in un segnalibro in un documento di Microsoft Office Word in modo da poter recuperare il testo in seguito o sostituire il testo in un segnalibro.  Se si sviluppa una personalizzazione a livello di documento, è anche possibile aggiornare il testo in un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> associato a dati.  Per altre informazioni, vedere [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'oggetto segnalibro può essere di due tipi diversi:  
  
-   Controllo host <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     I controlli <xref:Microsoft.Office.Tools.Word.Bookmark> estendono gli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> nativi permettendo il data binding e l'esposizione di eventi.  Per altre informazioni sui controlli host, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
-   Oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo.  
  
     Gli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> non includono eventi né hanno funzionalità di data binding.  
  
 Quando si assegna testo a un segnalibro, il comportamento tra un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> e un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> è diverso.  Per altre informazioni, vedere [Controllo Bookmark](../vsto/bookmark-control.md).  
  
## Uso di controlli host  
  
#### Per aggiornare il contenuto dei segnalibri mediante un controllo Bookmark  
  
1.  Creare una routine che accetti un argomento `bookmark` per il nome del segnalibro e un argomento `newText` per la stringa da assegnare alla proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.  
  
    > [!NOTE]  
    >  Se si assegna testo alla proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> o <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark>, il segnalibro non viene eliminato.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#63)]
     [!code-vb[Trin_VstcoreWordAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#63)]  
  
2.  Assegnare quindi *newText* alla proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> dell'oggetto <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#64)]
     [!code-vb[Trin_VstcoreWordAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#64)]  
  
## Uso di oggetti di Word  
  
#### Per aggiornare il contenuto dei segnalibri mediante un oggetto Bookmark di Word  
  
1.  Creare una routine che includa un argomento `bookmark` per il nome dell'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> e un argomento `newText` per la stringa da assegnare alla proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del segnalibro.  
  
    > [!NOTE]  
    >  Se si assegna testo a un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo di Word, il segnalibro viene eliminato.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#65)]
     [!code-vb[Trin_VstcoreWordAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#65)]  
  
2.  Assegnare la stringa *newText* alla proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del segnalibro. Questa operazione provoca l'eliminazione automatica del segnalibro.  Riaggiungere quindi il segnalibro alla raccolta <xref:Microsoft.Office.Interop.Word.Bookmarks>.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#66)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO.  L'esempio usa il documento attivo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#66)]  
  
## Vedere anche  
 [Procedura: inserire testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Controllo Bookmark](../vsto/bookmark-control.md)  
  
  