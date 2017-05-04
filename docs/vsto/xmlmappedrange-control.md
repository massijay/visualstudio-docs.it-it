---
title: "Controllo XmlMappedRange | Microsoft Docs"
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
  - "XMLMappedRange (controllo)"
  - "XMLMappedRange (controllo), associazione dati"
  - "XMLMappedRange (controllo), eventi"
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Controllo XmlMappedRange
  Il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è un intervallo creato soltanto quando un elemento non ripetitivo dello schema viene mappato a una cella in Microsoft Office Excel.  Ad esempio, quando l'attributo `maxOccurs` di un elemento dello schema è uguale a 1.  Una volta che in Visual Studio è stato creato l'intervallo mappato XML, è possibile eseguire la programmazione per questo oggetto in modo diretto, senza dover passare al modello a oggetti di Excel.  È possibile eliminare un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> all'interno di Excel solo quando viene rimosso il mapping dell'elemento.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere la procedura dettagliata relativo all'[utilizzo del mapping XML in Excel](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## Associazione di dati al controllo  
 Un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> supporta l'associazione a un unico campo di dati \(associazione dati semplice\).  Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> è invece in grado di supportare l'associazione dati complessa e viene creato automaticamente quando un elemento di schema ripetitivo è mappato a una cella.  Per ulteriori informazioni, vedere [Controllo ListObject](../vsto/listobject-control.md).  
  
 Il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> deve essere associato a un'origine dati mediante la proprietà <xref:System.Windows.Forms.Control.DataBindings%2A>.  Quando un oggetto <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> viene aggiunto a una cella del foglio di lavoro, in Visual Studio viene automaticamente generato un set di dati dai dati delle celle mappate, che viene associato al controllo.  La proprietà di associazione dati predefinita di <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Se i dati nel set di dati associato vengono aggiornati attraverso un qualsiasi meccanismo, il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> rifletterà tali modifiche.  
  
## Formattazione  
 A un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> può essere applicata la stessa formattazione applicabile a un controllo <xref:Microsoft.Office.Interop.Excel.Range>.  Nella formattazione sono inclusi bordi, tipi di carattere, formato numero e stili.  
  
## Eventi  
 Gli eventi disponibili per il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> sono:  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## Vedere anche  
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Procedura: aggiungere controlli XMLMappedRange a fogli di lavoro](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura: mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  