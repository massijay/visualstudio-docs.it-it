---
title: "Procedura: Eseguire il mapping delle colonne ListObject ai dati | Microsoft Docs"
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
  - "dati [sviluppo per Office in Visual Studio], mapping alla colonna ListObject"
  - "ListObject (controllo), mapping dei dati"
ms.assetid: 2108d0c3-d595-410e-a0ae-3dd53bf6bcc7
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Procedura: Eseguire il mapping delle colonne ListObject ai dati
  Quando si associa un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a un oggetto <xref:System.Data.DataTable>, è possibile che non si voglia visualizzare tutte le colonne in un elenco o che alcune colonne non siano associate a dati. È possibile mappare le colonne da visualizzare nel <xref:Microsoft.Office.Tools.Excel.ListObject> quando si chiama il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere la [procedura per creare un elenco in Excel connesso a un elenco di SharePoint](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## Mapping di colonne  
  
#### Per mappare una tabella dati alle colonne in un elenco  
  
1.  Creare l'oggetto <xref:System.Data.DataTable> a livello di classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#16)]  
  
2.  Aggiungere colonne e dati di esempio nel gestore eventi `Startup` della classe `Sheet1` \(in un progetto a livello di documento\) oppure della classe `ThisAddIn` \(in un progetto di componente aggiuntivo VSTO\).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#17)]  
  
3.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. L'oggetto elenco verrà associato all'oggetto <xref:System.Data.DataTable> appena creato, ma l'ordine delle colonne nell'oggetto elenco sarà diverso dall'ordine in cui sono visualizzate nell'oggetto <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#18)]  
  
## Definizione delle colonne non mappate  
 Quando si mappano le colonne a un oggetto <xref:System.Data.DataTable>, si può anche specificare che alcune colonne non devono essere associate a dati passando una stringa vuota. Viene quindi aggiunta una nuova colonna non associata a dati al controllo <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
#### Per specificare una colonna non mappata durante il mapping delle colonne ListObject  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. Usare una stringa vuota per indicare dove viene aggiunta una colonna non mappata, in questo caso tra la colonna del titolo e la colonna del cognome.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#19)]  
  
## Compilazione del codice  
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1`.  
  
## Vedere anche  
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: Riempire controlli ListObject con dati](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Controllo ListObject](../vsto/listobject-control.md)  
  
  