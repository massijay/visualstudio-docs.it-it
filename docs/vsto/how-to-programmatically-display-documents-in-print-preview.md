---
title: "Procedura: Visualizzare documenti in un&#39;anteprima di stampa a livello di codice"
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
  - "Word [sviluppo per Office in Visual Studio], visualizzazione dei documenti in anteprima di stampa"
  - "documenti [sviluppo per Office in Visual Studio], visualizzazione in anteprima di stampa"
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Procedura: Visualizzare documenti in un&#39;anteprima di stampa a livello di codice
  Se la soluzione genera un report, è possibile che si voglia far visualizzare il report all'utente in modalità Anteprima di stampa.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Procedure per le personalizzazioni a livello di documento  
  
#### Per visualizzare un documento in Anteprima di stampa chiamando il metodo PrintPreview  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomation#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#13)]  
  
#### Per visualizzare un documento in Anteprima di stampa impostando la proprietà PrintPreview  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> su **true**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## Procedure per i componenti aggiuntivi VSTO  
  
#### Per visualizzare un documento in Anteprima di stampa chiamando il metodo PrintPreview  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole visualizzare in anteprima. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
#### Per visualizzare un documento in Anteprima di stampa impostando la proprietà PrintPreview  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> su **true**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## Vedere anche  
 [Procedura: Stampare documenti a livello di codice](../vsto/how-to-programmatically-print-documents.md)   
 [Procedura: aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Procedura: creare nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)  
  
  