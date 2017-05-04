---
title: "Procedura: Proteggere documenti e parti di documenti a livello di codice | Microsoft Docs"
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
  - "protezione di documenti"
  - "documenti [sviluppo per Office in Visual Studio], protezione di documenti"
  - "documenti Word, protezione"
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Procedura: Proteggere documenti e parti di documenti a livello di codice
  È possibile aggiungere protezione ai documenti di Microsoft Office Word per impedire agli utenti di apportare modifiche al documento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 È anche possibile contrassegnare determinate aree del documento come eccezioni in modo che gli utenti possano modificare solo quelle aree del documento. Ad esempio, si potrebbe voler proteggere un intero documento ad eccezione di un segnalibro particolare. È possibile aggiungere facoltativamente una password in modo che gli utenti non possano rimuovere la protezione del documento a meno che non si conosca la password.  
  
> [!NOTE]  
>  Nell'esempio seguente non viene usata la protezione con password; tuttavia, si consiglia di usare una password quando si aggiunge la protezione di documenti. Per altre informazioni, vedere Esempio di strumento di protezione dei documenti [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 È possibile anche usare i controlli contenuto per proteggere parti di un documento. Per altre informazioni, vedere [Procedura: proteggere parti di documenti mediante i controlli del contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## Protezione di un documento che fa parte di una personalizzazione a livello di documento  
  
#### Per proteggere un documento che fa parte di una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> della classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
#### Per escludere un controllo Bookmark dalla protezione di documenti  
  
1.  Proteggere l'intero documento usando il metodo <xref:Microsoft.Office.Tools.Word.Document.Protect%2A>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
2.  Escludere `Bookmark1` dalla protezione di documenti.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#112](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#112)]
     [!code-vb[Trin_VstcoreWordAutomation#112](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#112)]  
  
### Compilazione del codice  
 Per usare questi esempi di codice, eseguirli dalla classe `ThisDocument` nel progetto. Questi esempi di codice presuppongono che nel documento in cui appare questo codice sia disponibile il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> esistente denominato `Bookmark1`.  
  
## Protezione di un documento usando un componente aggiuntivo VSTO  
  
#### Per proteggere un documento usando un componente aggiuntivo VSTO a livello di applicazione  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole proteggere.  
  
     L'esempio di codice seguente protegge il documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#111)]  
  
## Vedere anche  
 [Sicurezza dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Sicurezza tramite password di documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Procedura: supportare l'esecuzione di codice sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Procedura: aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  