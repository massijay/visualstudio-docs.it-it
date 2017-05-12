---
title: "Procedura: elencare i file di cartelle di lavoro utilizzati di recente a livello di codice"
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
  - "Excel [sviluppo per Office in Visual Studio], elenco dei file utilizzati di recente"
  - "elenco di file recenti, Excel"
  - "RecentFiles (proprietà)"
  - "cartelle di lavoro, elenco dei file utilizzati di recente"
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Procedura: elencare i file di cartelle di lavoro utilizzati di recente a livello di codice
  La proprietà <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> restituisce una raccolta che contiene i nomi di tutti i file presenti nell'elenco dei file utilizzati di recente in Microsoft Office Excel.  La lunghezza dell'elenco dipende dal numero di file da conservare selezionati dall'utente.  È possibile visualizzare i risultati in un intervallo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Per elencare le cartelle di lavoro utilizzate di recente in un oggetto intervallo  
  
1.  Riprodurre a ciclo continuo l'elenco dei file recenti e visualizzare i nomi nelle celle relative a un oggetto <xref:Microsoft.Office.Interop.Excel.Range>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## Vedere anche  
 [Uso delle cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  