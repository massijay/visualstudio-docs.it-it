---
title: "Controllo NamedRange"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Toolbox.Range"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "denominati, intervalli"
  - "NamedRange (controllo), eventi"
  - "NamedRange (controllo), data binding"
  - "NamedRange (controllo)"
ms.assetid: 07878c7c-cb5a-4f98-95c4-e828de25dae5
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Controllo NamedRange
  Il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> è un intervallo con un nome univoco che espone gli eventi e può essere associato ai dati. Per altre informazioni, vedere [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Creazione del controllo  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione o in fase di esecuzione nei progetti a livello di documento.  
  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro in fase di esecuzione in un componente aggiuntivo VSTO. Per altre informazioni, vedere [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Per impostazione predefinita, gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 I controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> possono essere costituiti solo da intervalli in fogli specifici. I controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> non possono avere nomi relativi che si applicano a tutti i fogli e non possono essere costituiti da intervalli estesi a due o più fogli di lavoro di una cartella di lavoro \(intervalli 3D\).  
  
## Data binding al controllo  
 Un intervallo denominato può sembrare il candidato ideale per il data binding complesso, dal momento che può includere diverse celle. Un intervallo è però semplicemente una raccolta di celle di cui non è possibile eseguire facilmente il mapping a una determinata colonna particolare di un set di dati. Di conseguenza, i controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> supportano solo il data binding semplici. Per il data binding complesso è possibile usare il controllo <xref:Microsoft.Office.Tools.Excel.ListObject>. Per altre informazioni, vedere [Controllo ListObject](../vsto/listobject-control.md).  
  
 È possibile associare il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un'origine dati usando le proprietà <xref:System.Windows.Forms.Control.DataBindings%2A>. La proprietà di data binding predefinita del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> è <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Se i dati nel set di dati associato vengono aggiornati con qualsiasi meccanismo, il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> rispecchia le modifiche.  
  
## Formattazione  
 La formattazione applicabile a <xref:Microsoft.Office.Interop.Excel.Range> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>. Questo include i bordi, i tipi di carattere, il formato numero e gli stili.  
  
## Ridenominazione del controllo  
 Quando si aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> al foglio di lavoro dalla **Casella degli strumenti**, Visual Studio genera automaticamente un nome per il controllo che può essere modificato nella finestra **Proprietà**.  
  
## Eventi  
 Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>:  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## Vedere anche  
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura dettagliata: programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  