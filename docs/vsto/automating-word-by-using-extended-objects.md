---
title: "Automazione di Word usando oggetti estesi | Microsoft Docs"
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
  - "Word [Office sviluppo per Office in Visual Studio], automazione"
  - "oggetti estesi [sviluppo per Office in Visual Studio], Word"
  - "automazione [sviluppo per Office in Visual Studio], Word"
  - "elementi host [sviluppo per Office in Visual Studio], Word"
  - "automazione di Word"
  - "controlli [sviluppo per Office in Visual Studio], controlli host di Word"
  - "controlli host, Word"
  - "controlli host [sviluppo per Office in Visual Studio], Word"
  - "Word [sviluppo per Office in Visual Studio], controlli host"
ms.assetid: 3911c7cd-7092-468d-bd82-2fdec53a2d9b
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Automazione di Word usando oggetti estesi
  Quando si sviluppano soluzioni Word in Visual Studio, è possibile usare *elementi host* e *controlli host* nelle soluzioni. Si tratta di oggetti che estendono determinati oggetti usati comunemente nel modello a oggetti di Word \(cioè, il modello a oggetti esposto dall'assembly di interoperabilità primario per Word\), come ad esempio gli oggetti <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.ContentControl>. Gli oggetti estesi si comportano come gli oggetti di Word su cui sono basati, ma aggiungono ulteriori eventi e funzionalità di data binding agli oggetti.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Gli elementi e i controlli host sono disponibili nelle personalizzazioni a livello di documento e dei componenti aggiuntivi VSTO, sebbene il contenuto in cui possono essere usati è diverso per ogni tipo di soluzione. Per altre informazioni, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
## Elemento host Document  
 I progetti Word consentono l'accesso all'elemento host <xref:Microsoft.Office.Tools.Word.Document>. L'elemento host <xref:Microsoft.Office.Tools.Word.Document> viene usato come contenitore per altri controlli, inclusi i controlli host e quelli Windows Form, e gestisce informazioni relative ai controlli della relativa area. L'elemento host <xref:Microsoft.Office.Tools.Word.Document> fornisce anche la maggior parte dei membri della classe <xref:Microsoft.Office.Interop.Word.Document>, ovvero la classe corrispondente nel modello a oggetti di Word.  
  
 Per altre informazioni, vedere [Elemento host Document](../vsto/document-host-item.md).  
  
## Controlli host di Word  
 Vi sono vari controlli host per Word che consentono di creare, organizzare e automatizzare i documenti. La maggior parte delle funzionalità offerte include l'importazione, la presentazione e la protezione dei dati. Si tratta di controlli host che forniscono funzionalità di data binding ed eventi che non sono disponibili nelle rispettive controparti del modello a oggetti di Word nativo.  
  
 Nei progetti a livello di documento è possibile aggiungere al documento qualsiasi controllo host in fase di progettazione oppure controlli contenuto e controlli segnalibro in fase di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere controlli contenuto e segnalibro a qualsiasi documento aperto in fase di esecuzione.  
  
 Per altre informazioni sui controlli host da poter usare in progetti Word, vedere i seguenti argomenti:  
  
-   [Controlli del contenuto](../vsto/content-controls.md)  
  
-   [Controllo Bookmark](../vsto/bookmark-control.md)  
  
-   [Controllo XMLNode](../vsto/xmlnode-control.md)  
  
-   [Controllo XMLNodes](../vsto/xmlnodes-control.md)  
  
## Vedere anche  
 [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Procedura: aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Procedura: Ridimensionare i controlli Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Procedura dettagliata: creazione di un modello utilizzando i controlli del contenuto](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Procedura dettagliata: associazione dei controlli del contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Procedura dettagliata: creazione di menu di scelta rapida per segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Soluzioni Word](../vsto/word-solutions.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  