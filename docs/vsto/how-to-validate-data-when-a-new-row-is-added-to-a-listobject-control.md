---
title: "Procedura: Convalidare dati quando viene aggiunta una nuova riga a un controllo ListObject"
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
  - "controlli [sviluppo per Office in Visual Studio], convalida dei dati"
  - "ListObject (controllo), nuova riga"
  - "ListObject (controllo), convalida dei dati"
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Procedura: Convalidare dati quando viene aggiunta una nuova riga a un controllo ListObject
  Gli utenti possono aggiungere nuove righe a un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> associato ai dati. È possibile convalidare i dati dell'utente prima del commit delle modifiche all'origine dati.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Convalida dei dati  
 Ogni volta che viene aggiunta una riga a <xref:Microsoft.Office.Tools.Excel.ListObject> associata ai dati, viene generato l'evento <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>. È possibile gestire questo evento per eseguire la convalida dei dati. Se, ad esempio, l'applicazione richiede che solo i dipendenti di età compresa tra i 18 e i 65 anni possano essere aggiunti all'origine dati, è possibile verificare che l'età inserita sia compresa nell'intervallo prima di aggiungere la riga.  
  
> [!NOTE]  
>  È sempre opportuno verificare l'input dell'utente non solo nel client ma anche nel server. Per altre informazioni, vedere [Applicazioni client protette](http://msdn.microsoft.com/library/6239592e-fa7d-4dea-9f00-d296d0048b01).  
  
#### Per convalidare i dati quando una nuova riga viene aggiunta a un controllo ListObject associato ai dati  
  
1.  Creare variabili per l'ID e la classe <xref:System.Data.DataTable> a livello di classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#8)]  
  
2.  Creare un nuovo oggetto <xref:System.Data.DataTable> e aggiungere colonne e dati di esempio nel gestore eventi `Startup` della classe `Sheet1` \(in un progetto a livello di documento\) oppure della classe `ThisAddIn` \(in un progetto di componente aggiuntivo VSTO\).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#9)]  
  
3.  Aggiungere codice al gestore eventi `list1_BeforeAddDataBoundRow` per controllare se l'età immessa è compresa nell'intervallo appropriato.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#10)]  
  
## Compilazione del codice  
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1`.  
  
## Vedere anche  
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Controllo ListObject](../vsto/listobject-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Procedura: Eseguire il mapping delle colonne ListObject ai dati](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  