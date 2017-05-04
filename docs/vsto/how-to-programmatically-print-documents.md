---
title: "Procedura: Stampare documenti a livello di codice | Microsoft Docs"
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
  - "Word [sviluppo per Office in Visual Studio], stampa di documenti"
  - "documenti [sviluppo per Office in Visual Studio], stampa"
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Procedura: Stampare documenti a livello di codice
  È possibile stampare un intero documento di Microsoft Office Word o parte di un documento sulla stampante predefinita.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Stampa di un documento che fa parte di una personalizzazione a livello di documento  
  
#### Per stampare l'intero documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> della classe `ThisDocument` nel progetto per stampare l'intero documento. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#11)]  
  
#### Per stampare la pagina corrente del documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> della classe `ThisDocument` nel progetto e specificare che una copia della pagina corrente deve essere stampata. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomation#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#12)]  
  
## Stampa di un documento usando un componente aggiuntivo VSTO  
  
#### Per stampare un intero documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> da stampare. L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
#### Per stampare la pagina corrente di un documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole stampare e specificare che una copia della pagina corrente deve essere stampata. L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Vedere anche  
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  