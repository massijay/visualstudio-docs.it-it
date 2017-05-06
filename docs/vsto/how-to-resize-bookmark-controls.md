---
title: "Procedura: Ridimensionare i controlli Bookmark"
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
  - "controlli [sviluppo per Office in Visual Studio], ridimensionamento"
  - "Bookmark (controllo), ridimensionamento"
ms.assetid: 3de1c774-921a-4113-a54a-e3b8d4a65d53
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Procedura: Ridimensionare i controlli Bookmark
  Le dimensioni di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> vengono impostate quando il controllo viene aggiunto a un documento di Microsoft Office Word. È anche possibile ridimensionare tale controllo in un secondo momento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Il ridimensionamento di un segnalibro può avvenire in tre modi:  
  
-   Aggiungere o rimuovere un testo nel controllo <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Ogni volta che si aggiunge del testo in un segnalibro, le dimensioni del segnalibro aumentano automaticamente al fine di contenere il nuovo testo. Quando si elimina il testo, le dimensioni del segnalibro si riducono automaticamente.  
  
-   Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> del controllo <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Questa funzionalità è utile se si modificano le dimensioni solo di un numero limitato di caratteri.  
  
-   Ricreare il controllo <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Questa funzionalità è utile in caso di una modifica sostanziale delle dimensioni o della posizione di un segnalibro.  
  
 Nei progetti a livello di documento è possibile aggiungere controlli <xref:Microsoft.Office.Tools.Word.Bookmark> al documento nel progetto in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere i controlli <xref:Microsoft.Office.Tools.Word.Bookmark> a qualsiasi documento aperto in fase di esecuzione. Per altre informazioni, vedere [Procedura: aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Modifica delle proprietà Start ed End  
  
#### Per ridimensionare un segnalibro in un progetto a livello di documento in fase di progettazione  
  
1.  Selezionare il segnalibro nella finestra **Proprietà**.  
  
2.  Aumentare o ridurre il valore della proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>.  
  
3.  Aumentare o ridurre il valore della proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A>.  
  
#### Per ridimensionare un segnalibro in un progetto a livello di documento in fase di esecuzione  
  
1.  Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> creato in fase di esecuzione o di progettazione.  
  
     L'esempio di codice seguente aggiunge cinque caratteri all'inizio di un segnalibro denominato `SampleBookmark`. In questo codice si presuppone che prima del segnalibro siano presenti almeno cinque caratteri di testo.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#2)]  
  
     L'esempio di codice seguente aggiunge cinque caratteri alla fine dello stesso segnalibro. In questo codice si presuppone che dopo il segnalibro siano presenti almeno cinque caratteri di testo.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#3)]  
  
#### Per ridimensionare un segnalibro in un progetto di componente aggiuntivo VSTO in fase di esecuzione  
  
1.  Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> creato in fase di esecuzione.  
  
     L'esempio di codice seguente crea un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> che contiene il testo del primo paragrafo del documento attivo, quindi rimuove cinque caratteri dall'inizio e dalla fine dell'oggetto <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_WordAddInDynamicControls#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#16)]  
  
## Ricreazione del segnalibro  
 È possibile ridimensionare un segnalibro in un progetto a livello di documento aggiungendo un nuovo segnalibro con lo stesso nome del segnalibro esistente, ma le cui dimensioni sono diverse.  
  
#### Per ricreare un segnalibro in un progetto a livello di documento in fase di progettazione  
  
1.  Selezionare il testo da includere nel nuovo controllo <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
2.  Scegliere **Segnalibro** dal menu **Inserisci**.  
  
3.  Nella finestra di dialogo **Segnalibro** selezionare il nome del segnalibro da ridimensionare e scegliere **Aggiungi**.  
  
## Vedere anche  
 [Procedura: aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Procedura: Ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  