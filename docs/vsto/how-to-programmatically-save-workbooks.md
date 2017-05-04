---
title: "Procedura: salvare cartelle di lavoro a livello di codice | Microsoft Docs"
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
  - "cartelle di lavoro, salvataggio"
  - "cartelle di lavoro, salvataggio di copie di backup"
  - "cartelle di lavoro, salvataggio in formato XML"
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Procedura: salvare cartelle di lavoro a livello di codice
  Una cartella di lavoro può essere salvata in più modi,  ad esempio senza modificare il percorso.  Se si tratta del primo salvataggio della cartella di lavoro, è necessario specificare un percorso.  Se non viene specificato un percorso esplicito, Microsoft Office Excel salva il file nella cartella corrente con il nome assegnato al momento della creazione.  È anche possibile salvare una copia della cartella di lavoro senza modificare la cartella di lavoro aperta in memoria.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Salvataggio di una cartella di lavoro senza modifica del percorso  
  
#### Per salvare una cartella di lavoro associata a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> della classe ThisWorkbook.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#4)]  
  
#### Per salvare la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> per salvare la cartella di lavoro attiva.  Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Salvataggio di una cartella di lavoro con un nuovo percorso  
 È possibile salvare la cartella di lavoro specificata in un nuovo percorso o con un nuovo nome, specificando eventualmente un formato di file, una password, una modalità di accesso e altre opzioni.  
  
> [!NOTE]  
>  Potrebbe essere necessario impostare la proprietà <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> su **False** prima di salvare la cartella di lavoro con un nuovo percorso poiché per il salvataggio in alcuni formati è necessaria l'interazione.  Se si imposta questa proprietà su **False**, in Excel verranno usati tutti i valori predefiniti.  
  
#### Per salvare una cartella di lavoro associata a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> della classe `ThisWorkbook`.  Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#5)]  
  
#### Per salvare la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> per salvare la cartella di lavoro attiva in un nuovo percorso.  Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Salvataggio di una copia della cartella di lavoro  
 È possibile salvare una copia della cartella di lavoro in un file senza modificare la cartella di lavoro aperta in memoria.  Questa operazione è utile per creare una copia di backup senza modificare il percorso della cartella di lavoro.  
  
#### Per salvare una cartella di lavoro associata a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> della classe `ThisWorkbook`.  Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#6)]  
  
#### Per salvare la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> per salvare una copia della cartella di lavoro attiva.  Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## Programmazione efficiente  
 Se si annulla in modo interattivo uno dei metodi usati per salvare o copiare la cartella di lavoro, viene generato un errore di run\-time nel codice.  Se ad esempio nella routine viene chiamato il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> ma non vengono disabilitati i prompt da Excel e l'utente fa clic su **Annulla** quando gli viene richiesto, viene generato un errore di run\-time in Excel.  
  
## Vedere anche  
 [Uso delle cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Procedura: Chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  