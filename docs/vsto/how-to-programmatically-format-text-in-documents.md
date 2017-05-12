---
title: "Procedura: Formattare il testo nei documenti a livello di codice"
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
  - "formattazione [sviluppo per Office in Visual Studio]"
  - "documenti [sviluppo per Office in Visual Studio], formattazione di testo"
  - "testo [sviluppo per Office in Visual Studio], formattazione nei documenti"
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Procedura: Formattare il testo nei documenti a livello di codice
  È possibile usare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> per formattare il testo in un documento di Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'esempio seguente seleziona il primo paragrafo del documento e modifica le dimensioni del carattere, il nome del carattere e l'allineamento. Quindi, seleziona l'intervallo e visualizza una finestra messaggio per sospendere l'operazione prima di eseguire la successiva sezione di codice. La sezione successiva chiama il metodo Undo dell'elemento host <xref:Microsoft.Office.Tools.Word.Document> \(per una personalizzazione a livello di documento\) o la classe <xref:Microsoft.Office.Interop.Word.Document> \(per un componente aggiuntivo VSTO\) tre volte. Applica lo stile del livello di rientro normale, mostrando una finestra di messaggio per sospendere il codice. Il codice chiama quindi il metodo <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> una volta e visualizza una finestra di messaggio.  
  
## Esempio di personalizzazione a livello di documento  
  
#### Per formattare il testo usando una personalizzazione a livello di documento  
  
1.  L'esempio seguente può essere usato in una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#62)]  
  
## Esempio di componente aggiuntivo VSTO  
  
#### Per formattare il testo usando un componente aggiuntivo VSTO  
  
1.  L'esempio seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#62)]  
  
## Vedere anche  
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: inserire testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Procedura: cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  