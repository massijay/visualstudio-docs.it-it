---
title: "Procedura: Estendere gli intervalli nei documenti a livello di codice"
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
  - "intervalli, estensione"
  - "documenti [sviluppo per Office in Visual Studio], estensione degli intervalli"
ms.assetid: 055af7a4-13d5-4236-b5fb-a112721482c5
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Procedura: Estendere gli intervalli nei documenti a livello di codice
  Una volta definito un oggetto <xref:Microsoft.Office.Interop.Word.Range> in un documento di Microsoft Office Word, è possibile modificare i punti iniziale e finale usando i metodi <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> e <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>. I metodi <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> e <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> accettano gli stessi due argomenti, *Unit* e *Count*. L'argomento *Count* rappresenta il numero di unità da spostare, mentre l'argomento *Unit* può rappresentare uno dei seguenti valori <xref:Microsoft.Office.Interop.Word.WdUnits>:  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'esempio seguente definisce un intervallo di sette caratteri. La posizione iniziale dell'intervallo viene quindi spostata sette caratteri dopo la posizione iniziale originale.  Dal momento che anche la posizione finale dell'intervallo era sette caratteri dopo la posizione iniziale, il risultato è un intervallo composto da zero caratteri. All'interno del codice, la posizione finale viene spostata sette caratteri dopo la posizione finale corrente.  
  
### Per estendere un intervallo  
  
1.  Definire un intervallo di caratteri. Per altre informazioni, vedere [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#39)]
     [!code-vb[Trin_VstcoreWordAutomation#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#39)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#39)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#39)]  
  
2.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> per spostare la posizione iniziale dell'intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#40](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#40)]
     [!code-vb[Trin_VstcoreWordAutomation#40](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#40)]  
  
3.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> per spostare la posizione finale dell'intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#41](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#41)]
     [!code-vb[Trin_VstcoreWordAutomation#41](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#41)]  
  
## Codice di personalizzazione a livello di documento  
  
#### Per estendere un intervallo in una personalizzazione a livello di documento  
  
1.  L'esempio seguente mostra il codice completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#38)]
     [!code-vb[Trin_VstcoreWordAutomation#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#38)]  
  
## Codice di componente aggiuntivo VSTO  
  
#### Per estendere un intervallo in un componente aggiuntivo VSTO a livello di applicazione  
  
1.  L'esempio seguente illustra il codice completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#38)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#38)]  
  
## Vedere anche  
 [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Procedura: Comprimere intervalli o selezioni in documenti a livello di codice](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: Recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Procedura: Escludere i segni di paragrafo durante l'inserimento di intervalli a livello di codice](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  