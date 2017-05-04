---
title: "Procedura: compilare tabelle di Word con le propriet&#224; documento a livello di codice | Microsoft Docs"
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
  - "proprietà di documento, inserimento in tabelle di Word"
  - "documenti [sviluppo per Office in Visual Studio], proprietà di documento"
ms.assetid: 7ed65a3d-58ed-43b3-92d6-dc10a2c331db
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Procedura: compilare tabelle di Word con le propriet&#224; documento a livello di codice
  L'esempio seguente crea una tabella di Microsoft Office Word nella parte superiore del documento e la popola con le proprietà del documento host.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Popolamento delle tabelle in una personalizzazione a livello di documento  
  
#### Per creare una tabella e popolarla con le proprietà del documento  
  
1.  Impostare l'intervallo nella parte superiore del documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomation#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#90)]  
  
2.  Inserire un titolo per la tabella e includere i segni di paragrafo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomation#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#91)]  
  
3.  Aggiungere la tabella al documento nell'intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomation#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#92)]  
  
4.  Formattare la tabella e applicare uno stile.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomation#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#93)]  
  
5.  Inserire le proprietà del documento nelle celle.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomation#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#94)]  
  
 L'esempio seguente mostra la procedura completa.  Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomation#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#89)]  
  
## Popolamento di tabelle in un componente aggiuntivo VSTO  
  
#### Per creare una tabella e popolarla con le proprietà del documento  
  
1.  Impostare l'intervallo nella parte superiore del documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#90)]  
  
2.  Inserire un titolo per la tabella e includere i segni di paragrafo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#91)]  
  
3.  Aggiungere la tabella al documento nell'intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#92)]  
  
4.  Formattare la tabella e applicare uno stile.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#93)]  
  
5.  Inserire le proprietà del documento nelle celle.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#94)]  
  
 L'esempio seguente mostra la procedura completa.  Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#89)]  
  
## Vedere anche  
 [Procedura: creare tabelle di Word a livello di codice](../vsto/how-to-programmatically-create-word-tables.md)   
 [Procedura: aggiungere testo e formattazione alle celle delle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  