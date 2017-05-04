---
title: "Procedura: aggiungere immagini e WordArt ai documenti a livello di codice | Microsoft Docs"
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
  - "documenti [sviluppo per Office in Visual Studio], aggiunta di immagini"
  - "grafica, aggiunta a documenti di Word"
  - "documenti di Word, aggiunta di immagini"
  - "documenti di Word, aggiunta di WordArt"
  - "WordArt, aggiunta a documenti"
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Procedura: aggiungere immagini e WordArt ai documenti a livello di codice
  È possibile aggiungere immagini e oggetti disegno ai documenti in fase di progettazione o in fase di esecuzione.  WordArt consente di aggiungere testo decorativo ai documenti di Microsoft Office Word.  Questi effetti di testo speciali sono oggetti disegno che è possibile personalizzare e inserire nel documento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Aggiunta di un'immagine in fase di progettazione  
 Se si sviluppa una personalizzazione a livello di documento, è possibile aggiungere un'immagine al documento in fase di progettazione.  
  
#### Per aggiungere un'immagine a un documento di Word in fase di progettazione  
  
1.  Posizionare il cursore nel punto in cui si vuole inserire l'immagine nel documento.  
  
2.  Fare clic sulla scheda **Inserisci** della barra multifunzione.  
  
3.  Nel gruppo **Illustrazioni** fare clic su **Immagine**.  
  
4.  Nella finestra di dialogo **Inserisci immagine** passare all'immagine da inserire e fare clic su **Inserisci**.  
  
     L'immagine verrà aggiunta al documento in corrispondenza della posizione corrente del cursore.  
  
## Aggiunta di un'immagine in fase di esecuzione  
 È possibile inserire un'immagine in un documento in corrispondenza della posizione corrente del cursore.  
  
#### Per aggiungere un'immagine in corrispondenza della posizione del cursore  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> della raccolta <xref:Microsoft.Office.Interop.Word.InlineShapes> e passare il nome del file.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#108](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#108)]
     [!code-vb[Trin_VstcoreWordAutomation#108](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#108)]  
  
## Aggiunta di un oggetto WordArt in fase di progettazione  
 Se si sviluppa una personalizzazione a livello di documento, è possibile aggiungere un oggetto WordArt al documento in fase di progettazione.  
  
#### Per aggiungere un oggetto WordArt a un documento di Word in fase di progettazione  
  
1.  Posizionare il cursore nel punto in cui si vuole inserire l'oggetto WordArt nel documento.  
  
2.  Fare clic sulla scheda **Inserisci** della barra multifunzione.  
  
3.  Nel gruppo **Testo** fare clic su **WordArt** e quindi selezionare uno stile WordArt.  
  
4.  Aggiungere nella finestra di dialogo **Modifica testo WordArt** il testo che si vuole visualizzare nel documento e fare clic su **OK**.  
  
     Il testo verrà aggiunto al documento con lo stile WordArt selezionato applicato.  
  
## Aggiunta di un oggetto WordArt in fase di esecuzione  
 È possibile inserire un oggetto WordArt in un documento in corrispondenza della posizione corrente del cursore.  La procedura è diversa per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
#### Per aggiungere un oggetto WordArt in corrispondenza della posizione del cursore in una personalizzazione a livello di documento  
  
1.  Ottenere la posizione corrente superiore e sinistra del cursore.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomation#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#109)]  
  
2.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Shapes> nel documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomation#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#110)]  
  
#### Per aggiungere un oggetto WordArt in corrispondenza della posizione del cursore in un componente aggiuntivo VSTO  
  
1.  Ottenere la posizione corrente superiore e sinistra del cursore.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#109)]  
  
2.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Shapes> del documento attivo \(o un documento diverso specificato\).  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#110)]  
  
## Compilazione del codice  
  
-   Nell'unità C deve essere presente un'immagine denominata **SamplePicture.jpg**.  
  
## Vedere anche  
 [Procedura: aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Procedura: inserire testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Procedura: ripristinare le selezioni dopo le ricerche a livello di codice](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Procedura: salvare documenti a livello di codice](../vsto/how-to-programmatically-save-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  