---
title: "Procedura: copiare dati e formattazione nei fogli di lavoro a livello di codice | Microsoft Docs"
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
  - "copia di dati, sviluppo per Office in Visual Studio"
  - "dati [sviluppo per Office in Visual Studio], copia tra fogli di lavoro"
  - "formattazione [sviluppo per Office in Visual Studio]"
  - "fogli di lavoro, copia di dati"
ms.assetid: eed7dbaf-bdb5-4330-ba2e-5f3d50817eca
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Procedura: copiare dati e formattazione nei fogli di lavoro a livello di codice
  È possibile copiare i dati di un intervallo di un foglio in tutti gli altri fogli di una cartella di lavoro mediante il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A>.  Specificare un intervallo e indicare se si desidera copiare solo i dati, solo la formattazione o entrambi.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#44)]  
  
## Compilazione del codice  
 Per l'esecuzione di questo esempio è necessario utilizzare un intervallo denominato `rangeData` in un foglio di lavoro.  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Procedura: modificare la formattazione nelle righe di un foglio di lavoro contenenti celle selezionate a livello di codice](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  