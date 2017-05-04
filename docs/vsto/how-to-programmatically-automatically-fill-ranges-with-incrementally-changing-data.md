---
title: "Procedura: riempire automaticamente gli intervalli con dati modificati in modo incrementale a livello di codice | Microsoft Docs"
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
  - "AutoFill (metodo) [Excel]"
  - "riempimento automatico di intervalli"
  - "intervalli, riempimento automatico"
  - "cartelle di lavoro, riempimento di intervalli"
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Procedura: riempire automaticamente gli intervalli con dati modificati in modo incrementale a livello di codice
  Il metodo <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> dell'oggetto <xref:Microsoft.Office.Interop.Excel.Range> consente di inserire automaticamente valori in un intervallo del foglio di lavoro.  Il metodo <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> viene spesso utilizzato per archiviare valori di un intervallo che aumentano o diminuiscono in modo incrementale.  È possibile specificare il comportamento di tale metodo, fornendo una costante facoltativa dall'enumerazione <xref:Microsoft.Office.Interop.Excel.XlAutoFillType>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Quando si utilizza <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> è necessario specificare due intervalli:  
  
-   L'intervallo per la chiamata del metodo <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> che specifica il punto iniziale del riempimento e contiene un valore iniziale.  
  
-   L'intervallo da riempire, passato come parametro al metodo <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>.  L'intervallo di destinazione deve includere l'intervallo contenente il valore iniziale.  
  
    > [!NOTE]  
    >  Non è possibile passare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> invece di <xref:Microsoft.Office.Interop.Excel.Range>.  Per ulteriori informazioni, vedere [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#49)]  
  
## Compilazione del codice  
 La prima cella dell'intervallo che si desidera riempire deve contenere un valore iniziale.  
  
 Nell'esempio è richiesto il riempimento di tre aree:  
  
-   La colonna B deve contenere cinque giorni della settimana.  Come valore iniziale, digitare **Monday** nella cella B1.  
  
-   La colonna C deve contenere cinque nomi di mesi.  Come valore iniziale, digitare **January** nella cella C1.  
  
-   La colonna D deve contenere una serie di numeri, con un incremento di due unità a ogni riga.  Come valori iniziali, digitare **4** nella cella D1 e **6** nella cella D2.  
  
## Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Procedura: fare riferimento agli intervalli dei fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Procedura: Applicare stili agli intervalli nei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: eseguire calcoli in Excel a livello di codice](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  