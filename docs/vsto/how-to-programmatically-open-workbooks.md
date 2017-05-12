---
title: "Procedura: aprire cartelle di lavoro a livello di codice"
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
  - "Excel [sviluppo per Office in Visual Studio], apertura di cartelle di lavoro"
  - "cartelle di lavoro, apertura"
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Procedura: aprire cartelle di lavoro a livello di codice
  La raccolta <xref:Microsoft.Office.Interop.Excel.Workbooks> in Microsoft Office Excel consente di lavorare con tutte le cartelle di lavoro aperte e di aprire cartelle di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Per aprire una cartella di lavoro esistente  
  
1.  Utilizzare il metodo <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Workbooks> passando il percorso della cartella di lavoro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#2)]  
  
## Compilazione del codice  
 Di seguito sono indicati i requisiti di questo esempio di codice:  
  
-   Una cartella di lavoro denominata `YourWorkbook.xls` deve essere presente in una directory denominata `Test` nell'unità C.  
  
## Vedere anche  
 [Uso delle cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: aprire file di testo come cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Procedura: creare nuove cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Procedura: salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md)   
 [Procedura: Chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  