---
title: "Procedura: ripristinare le selezioni dopo le ricerche a livello di codice | Microsoft Docs"
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
  - "documenti [sviluppo per Office in Visual Studio], ripristino di selezioni"
  - "ricerche, ripristino della selezione"
  - "selezioni, ripristino dopo una ricerca"
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Procedura: ripristinare le selezioni dopo le ricerche a livello di codice
  Se si effettua un'operazione di ricerca e sostituzione di testo in un documento, può rivelarsi utile ripristinare la selezione originale dell'utente dopo il completamento della ricerca.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Nel codice della routine di esempio vengono utilizzati due oggetti <xref:Microsoft.Office.Interop.Word.Range>.  Uno consente di archiviare l'oggetto <xref:Microsoft.Office.Interop.Word.Selection> corrente e l'altro consente di impostare l'intero documento come intervallo di ricerca.  
  
### Per ripristinare la selezione originale dell'utente dopo una ricerca  
  
1.  Creare gli oggetti <xref:Microsoft.Office.Interop.Word.Range> per il documento e la selezione corrente.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#83)]
     [!code-vb[Trin_VstcoreWordAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#83)]  
  
2.  Eseguire l'operazione di ricerca e sostituzione.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#84](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#84)]
     [!code-vb[Trin_VstcoreWordAutomation#84](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#84)]  
  
3.  Selezionare l'intervallo iniziale per ripristinare la selezione originale dell'utente.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#85](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#85)]
     [!code-vb[Trin_VstcoreWordAutomation#85](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#85)]  
  
 Nell'esempio riportato di seguito viene illustrato il metodo completo.  
  
## Esempio  
 [!code-csharp[Trin_VstcoreWordAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#82)]
 [!code-vb[Trin_VstcoreWordAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#82)]  
  
## Vedere anche  
 [Procedura: cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Procedura: impostare opzioni di ricerca in Word a livello di codice](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Procedura: Scorrere in ciclo gli elementi trovati nei documenti a livello di codice](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  