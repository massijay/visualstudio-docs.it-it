---
title: "Procedura: Scorrere in ciclo gli elementi trovati nei documenti a livello di codice"
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
  - "cicli, in elementi trovati nei documenti"
  - "documenti [sviluppo per Office in Visual Studio], ricerca"
  - "testo [sviluppo per Office in Visual Studio], ricerca nei documenti"
ms.assetid: 68dc41b1-eb96-4697-ac93-1a88c862ebad
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Procedura: Scorrere in ciclo gli elementi trovati nei documenti a livello di codice
  Nella classe <xref:Microsoft.Office.Interop.Word.Find> è presente una proprietà <xref:Microsoft.Office.Interop.Word.Find.Found%2A>, che restituisce **true** ogni volta che viene trovato un elemento di cui è stata effettuata la ricerca. Per scorrere in ciclo tutte le istanze trovate in un oggetto <xref:Microsoft.Office.Interop.Word.Range>, è possibile usare il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Per scorrere in ciclo gli elementi trovati  
  
1.  Dichiarare un oggetto <xref:Microsoft.Office.Interop.Word.Range>.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#79)]
     [!code-vb[Trin_VstcoreWordAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#79)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#79)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#79)]  
  
2.  Usare la proprietà <xref:Microsoft.Office.Interop.Word.Find.Found%2A> in un ciclo per ricercare tutte le occorrenze della stringa nel documento e incrementare di un'unità una variabile di tipo Integer ogni volta che viene trovata la stringa.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#80)]
     [!code-vb[Trin_VstcoreWordAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#80)]  
  
3.  Visualizza il numero di occorrenze trovate della stringa in una finestra di messaggio.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#81](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#81)]
     [!code-vb[Trin_VstcoreWordAutomation#81](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#81)]  
  
 Gli esempi seguenti illustrano il metodo completo.  
  
## Esempio di personalizzazione a livello di documento  
  
#### Per scorrere in ciclo gli elementi di una personalizzazione a livello di documento  
  
1.  L'esempio seguente mostra il codice completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#78)]
     [!code-vb[Trin_VstcoreWordAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#78)]  
  
## Esempio di componente aggiuntivo VSTO  
  
#### Per scorrere in ciclo gli elementi di un componente aggiuntivo VSTO  
  
1.  L'esempio seguente illustra il codice completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#78)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#78)]  
  
## Vedere anche  
 [Procedura: cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Procedura: impostare opzioni di ricerca in Word a livello di codice](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: ripristinare le selezioni dopo le ricerche a livello di codice](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  