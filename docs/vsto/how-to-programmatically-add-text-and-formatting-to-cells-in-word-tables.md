---
title: "Procedura: aggiungere testo e formattazione alle celle delle tabelle di Word a livello di codice"
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
  - "celle, aggiunta di testo e formattazione"
  - "formattazione [sviluppo per Office in Visual Studio]"
  - "tabelle [sviluppo per Office in Visual Studio], aggiunta di testo e formattazione"
  - "testo [sviluppo per Office in Visual Studio], aggiunta a tabelle di Word"
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Procedura: aggiungere testo e formattazione alle celle delle tabelle di Word a livello di codice
  Ogni tabella è costituita da una raccolta di celle.  Ogni singolo oggetto <xref:Microsoft.Office.Interop.Word.Cell> rappresenta una cella della tabella.  Le singole celle vengono individuate tramite la relativa posizione nella tabella.  Questo esempio si riferisce alla cella che si trova nella prima riga e nella prima colonna della tabella. Viene aggiunto un testo alla cella e viene applicata la formattazione.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Per aggiungere testo e formattazione alle celle  
  
1.  Fare riferimento alla cella tramite la relativa posizione nella tabella, aggiungere testo alla cella e applicare la formattazione.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  Per usare questo esempio, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomation#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#97)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO.  L'esempio usa il documento attivo.  Per usare l'esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#97)]  
  
## Vedere anche  
 [Procedura: creare tabelle di Word a livello di codice](../vsto/how-to-programmatically-create-word-tables.md)   
 [Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Procedura: compilare tabelle di Word con le proprietà documento a livello di codice](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  