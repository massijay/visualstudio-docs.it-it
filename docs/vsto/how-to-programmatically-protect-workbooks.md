---
title: "Procedura: proteggere cartelle di lavoro a livello di codice | Microsoft Docs"
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
  - "protezione di documenti, aggiunta a cartelle di lavoro"
  - "protezione di documenti, rimozione da cartelle di lavoro"
  - "documenti [sviluppo per Office in Visual Studio], protezione di documenti"
  - "cartelle di lavoro, password"
  - "cartelle di lavoro, protezione"
  - "cartelle di lavoro, rimozione della protezione"
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Procedura: proteggere cartelle di lavoro a livello di codice
  È possibile proteggere una cartella di lavoro di Microsoft Office Excel in modo da impedire agli utenti di aggiungere o eliminare fogli di lavoro e anche rimuovere la protezione a livello di codice.  È possibile specificare una password e indicare se si desidera proteggere la struttura, per evitare che gli utenti spostino i fogli, e le finestre della cartella di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 La protezione di una cartella di lavoro non impedisce agli utenti di modificare le celle.  Per proteggere i dati, è necessario proteggere i fogli di lavoro.  Per ulteriori informazioni, vedere [Procedura: proteggere fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 Negli esempi di codice seguenti viene utilizzata una variabile in cui inserire una password ottenuta dall'utente.  
  
## Protezione di una cartella di lavoro facente parte di una personalizzazione a livello di documento  
  
#### Per proteggere una cartella di lavoro  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> della cartella di lavoro e includere una password.  Per utilizzare l'esempio di codice seguente, eseguirlo nella classe `ThisWorkbook`, non in una classe Sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#10)]  
  
#### Per rimuovere la protezione da una cartella di lavoro  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>, se necessario passando una password.  Per utilizzare l'esempio di codice seguente, eseguirlo nella classe `ThisWorkbook`, non in una classe Sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#11)]  
  
## Protezione di una cartella di lavoro mediante un componente aggiuntivo a livello di applicazione  
  
#### Per proteggere una cartella di lavoro  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> della cartella di lavoro e includere una password.  In questo esempio di codice viene utilizzata la cartella di lavoro attiva.  Per utilizzare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
#### Per rimuovere la protezione da una cartella di lavoro  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> della cartella di lavoro attiva passando una password, se necessario.  Per utilizzare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## Vedere anche  
 [Uso delle cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: proteggere fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Procedura: Nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  