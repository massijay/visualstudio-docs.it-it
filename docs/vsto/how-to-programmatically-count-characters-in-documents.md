---
title: "Procedura: Conteggiare i caratteri nei documenti a livello di codice | Microsoft Docs"
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
  - "caratteri, conteggio nei documenti"
  - "conteggio di caratteri nei documenti"
  - "documenti [sviluppo per Office in Visual Studio], conteggio dei caratteri"
ms.assetid: ab64fe87-896a-4b56-bdf8-91c4326b540e
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Procedura: Conteggiare i caratteri nei documenti a livello di codice
  Il primo carattere in un documento è nella posizione del carattere 0, che rappresenta il punto di inserimento. La posizione dell'ultimo carattere è uguale al numero totale di caratteri nel documento. È possibile determinare il numero di caratteri in un documento usando la proprietà <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Characters>.  
  
 Tutti i caratteri del documento vengono contati, inclusi gli spazi, i segni di paragrafo e altri caratteri che sono normalmente nascosti. Anche un nuovo documento vuoto restituisce un numero di un solo carattere perché contiene un segno di paragrafo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Per visualizzare il numero di caratteri in una personalizzazione a livello di documento  
  
1.  Selezionare l'intero documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomation#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#98)]  
  
2.  Visualizzare il numero di caratteri del documento in una finestra di messaggio.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomation#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#99)]  
  
### Per visualizzare il numero di caratteri in un componente aggiuntivo VSTO  
  
1.  Selezionare l'intero documento. L'esempio di codice seguente seleziona il documento attivo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#98)]  
  
2.  Visualizzare il numero di caratteri del documento in una finestra di messaggio.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#99)]  
  
## Vedere anche  
 [Procedura: Recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  