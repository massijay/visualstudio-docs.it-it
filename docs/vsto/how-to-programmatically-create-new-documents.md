---
title: "Procedura: creare nuovi documenti a livello di codice | Microsoft Docs"
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
  - "documenti [sviluppo per Office in Visual Studio], creazione"
  - "modelli [sviluppo per Office in Visual Studio], documento personalizzato"
  - "Word [sviluppo per Office in Visual Studio], creazione di documenti"
ms.assetid: c24bb8a3-1303-438e-9b33-ba8b00b29c3b
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Procedura: creare nuovi documenti a livello di codice
  Quando si crea un documento a livello di programmazione, il nuovo documento è un oggetto <xref:Microsoft.Office.Interop.Word.Document> nativo.  Questo oggetto non ha le funzionalità di data binding e gli eventi aggiuntivi di un elemento host <xref:Microsoft.Office.Tools.Word.Document>.  Per altre informazioni, vedere [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Quando si sviluppa un progetto a livello di documento, non è possibile aggiungere a livello di codice elementi host <xref:Microsoft.Office.Tools.Word.Document> al progetto.  In un progetto di componente aggiuntivo VSTO è possibile convertire qualsiasi oggetto <xref:Microsoft.Office.Interop.Word.Document> in elemento host <xref:Microsoft.Office.Tools.Word.Document> in fase di esecuzione.  Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### Per creare un nuovo documento basato sul modello Normal  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Documents> per creare un nuovo documento basato sul modello Normal.  Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreWordAutomation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#1)]  
  
## Uso di modelli personalizzati  
 Il metodo <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> include un argomento *Template* facoltativo per creare un nuovo documento basato su un modello diverso dal modello Normal.  È necessario specificare il nome file e il percorso completo del modello.  
  
#### Per creare un nuovo documento basato su un modello personalizzato  
  
-   Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Documents> e specificare il percorso del modello.  Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreWordAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#2)]  
  
## Vedere anche  
 [Procedura: aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  