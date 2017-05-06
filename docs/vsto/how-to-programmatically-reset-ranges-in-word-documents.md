---
title: "Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice"
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
  - "documenti [sviluppo per Office in Visual Studio], reimpostazione degli intervalli"
  - "intervalli, reimpostazione in documenti"
ms.assetid: 45ea9434-e548-4d24-938f-4f1ffa5010d0
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice
  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> per ridimensionare un intervallo esistente in un documento di Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Per reimpostare un intervallo esistente  
  
1.  Impostare un intervallo iniziale iniziando con i primi sette caratteri nel documento.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#43)]
     [!code-vb[Trin_VstcoreWordAutomation#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#43)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#43)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#43)]  
  
2.  Usare <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> per iniziare l'intervallo in corrispondenza della seconda frase e terminarla alla fine della quinta frase.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#44)]
     [!code-vb[Trin_VstcoreWordAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#44)]  
  
## Esempio di personalizzazione a livello di documento  
  
#### Per reimpostare un intervallo esistente in una personalizzazione a livello di documento  
  
1.  L'esempio seguente mostra l'esempio completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#42)]
     [!code-vb[Trin_VstcoreWordAutomation#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#42)]  
  
## Esempio di componente aggiuntivo VSTO  
  
#### Per reimpostare un intervallo esistente in un componente aggiuntivo VSTO  
  
1.  L'esempio seguente illustra l'esempio completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#42)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#42)]  
  
## Vedere anche  
 [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: Recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Procedura: Comprimere intervalli o selezioni in documenti a livello di codice](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)  
  
  