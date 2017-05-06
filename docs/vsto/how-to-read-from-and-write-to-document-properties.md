---
title: "Procedura: Leggere e scrivere nelle propriet&#224; dei documenti"
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
  - "Word [sviluppo per Office in Visual Studio], proprietà documento"
  - "documenti [sviluppo per Office in Visual Studio], proprietà"
  - "proprietà di documento [sviluppo per Office in Visual Studio]"
  - "Excel [sviluppo per Office in Visual Studio], proprietà documento"
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Procedura: Leggere e scrivere nelle propriet&#224; dei documenti
  È possibile archiviare le proprietà del documento insieme a un documento. Le applicazioni di Office offrono svariate proprietà predefinite, ad esempio autore, titolo e oggetto. Questo argomento illustra come impostare le proprietà dei documenti in Microsoft Office Excel e Microsoft Office Word.  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere [Procedura: Accedere e modificare le proprietà personalizzate dei documenti in Microsoft Word](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## Impostazione delle proprietà dei documenti in Excel  
 Per usare le proprietà predefinite in Excel, configurare le proprietà seguenti:  
  
-   In un progetto a livello di documento usare la proprietà <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> della classe `ThisWorkbook`.  
  
-   In un progetto a livello di componente aggiuntivo VSTO, usare la proprietà <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties>, che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty>. È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.  
  
 L'esempio di codice seguente illustra come modificare la proprietà predefinita **Revision Number** in un progetto a livello di documento.  
  
#### Per modificare la proprietà Numero revisione in Excel  
  
1.  Assegnare le proprietà predefinite del documento a una variabile.  
  
     [!code-csharp[Trin_VstcoreProgramming#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#7)]
     [!code-vb[Trin_VstcoreProgramming#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#7)]  
  
2.  Incrementare di uno la proprietà `Revision Number`.  
  
     [!code-csharp[Trin_VstcoreProgramming#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#8)]
     [!code-vb[Trin_VstcoreProgramming#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#8)]  
  
## Impostazione delle proprietà dei documenti in Word  
 Per usare le proprietà predefinite in Word, configurare le proprietà seguenti:  
  
-   In un progetto a livello di documento usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> della classe `ThisDocument`.  
  
-   In un progetto a livello di componente aggiuntivo VSTO, usare la proprietà <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Document>.  
  
 Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties>, che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty>. È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.  
  
 L'esempio di codice seguente illustra come modificare la proprietà predefinita **Subject** in un progetto a livello di documento.  
  
#### Per modificare la proprietà Oggetto  
  
1.  Assegnare le proprietà predefinite del documento a una variabile.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#1)]  
  
2.  Modificare la proprietà `Subject` in "White paper".  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#2)]  
  
## Programmazione efficiente  
 Questo esempio presuppone che il codice della classe `ThisWorkbook` sia stato scritto in un progetto a livello di documento per Excel e quello della classe `ThisDocument` in un progetto a livello di documento per Word.  
  
 Anche se si usano Word ed Excel e i rispettivi oggetti, Microsoft Office fornisce l'elenco di proprietà predefinite disponibili per i documenti. Il tentativo di accesso a una proprietà non definita provocherà un'eccezione.  
  
## Vedere anche  
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Procedura: Creare e modificare proprietà personalizzate di un documento](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  