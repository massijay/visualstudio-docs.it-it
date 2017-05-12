---
title: "Propriet&#224; nei progetti di Office"
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
  - "Percorso assembly attendibili (proprietà)"
  - "Memorizza nella cache del documento (proprietà)"
  - "proprietà [sviluppo per Office in Visual Studio]"
  - "spazio dei nomi per la proprietà dell'elemento host"
  - "progetti di Office [sviluppo per Office in Visual Studio], proprietà"
  - "progetti [sviluppo per Office in Visual Studio], proprietà"
  - "Value2 (proprietà)"
ms.assetid: 1284d6c3-8200-4151-88ce-0b5c7765af25
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Propriet&#224; nei progetti di Office
  Per i progetti di Office in Visual Studio, sono disponibili numerose proprietà importanti, alle quali è possibile accedere dalla finestra **Proprietà**.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Spazio dei nomi per elemento host  
 Usare la proprietà **Spazio dei nomi per elemento host** per modificare lo spazio dei nomi delle classi dell'elemento host \(ad esempio, le classi `ThisAddIn`, `ThisWorkbook` o `ThisDocument`\) nei progetti Visual C\#. Questa proprietà viene visualizzata nella finestra **Proprietà** quando si seleziona il nodo del documento in un progetto a livello di documento \(ad esempio ExcelWorkbook1.xlsx o WordDocument1.docx\) o il nodo dell'applicazione in un progetto relativo a un componente aggiuntivo VSTO \(come Excel o Word\) in **Esplora soluzioni**.  
  
 Quando si crea un progetto di Office in Visual C\#, agli elementi host viene attribuito uno spazio dei nomi in base al nome del progetto. Si consiglia di usare la proprietà **Spazio dei nomi per elemento host** per modificare lo spazio dei nomi anziché modificare direttamente i file di codice. Quando si usa questa proprietà, lo spazio dei nomi viene modificato nei file di codice \(nascosti\) generati, oltre che nei file di codice visibili.  
  
## CacheInDocument  
 La proprietà **CacheInDocument** viene visualizzata nella finestra **Proprietà** per i progetti a livello di documento quando si seleziona un'istanza di un oggetto <xref:System.Data.DataSet> nella finestra di progettazione di Visual Studio. È possibile memorizzare nella cache solo i membri pubblici. Assicurarsi che la proprietà **Modificatori** sia impostata su **Pubblica** se si desidera memorizzare nella cache un oggetto <xref:System.Data.DataSet>.  
  
 Questa proprietà accetta un valore booleano:  
  
-   Selezionare **true** per memorizzare nella cache il set di dati nel documento.  
  
-   Selezionare **false** se non si desidera che il set di dati venga memorizzato nella cache del documento.  
  
 Per altre informazioni sulla memorizzazione dei dati nella cache, vedere [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).  
  
## Value2  
 La proprietà **Value2** è disponibile solo per progetti modello o cartella di lavoro di Excel. Viene visualizzata nel nodo proprietà **Databindings** nella finestra **Proprietà** quando si seleziona un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> nella finestra di progettazione del foglio di lavoro.  
  
 Usare la proprietà **Value2** nella finestra **Proprietà** per associare la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> di <xref:Microsoft.Office.Tools.Excel.NamedRange> a un campo dell'origine dati.  
  
## Vedere anche  
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)   
 [Eventi nei progetti di Office](../vsto/events-in-office-projects.md)  
  
  