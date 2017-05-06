---
title: "Procedura: Stampare documenti di Visio a livello di codice"
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
  - "Visio [sviluppo per Office in Visual Studio], stampa di documenti Visio"
  - "documenti [sviluppo per Office in Visual Studio], stampa di documenti Visio"
ms.assetid: 606a2678-5eb8-40b2-a50a-305cecb1b3d4
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: Stampare documenti di Visio a livello di codice
  È possibile stampare l'intero contenuto o solo una pagina specifica di un documento di Microsoft Office Visio.  
  
 Per informazioni dettagliate sui metodi di stampa, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Document.Print](HV10070345) e [Microsoft.Office.Interop.Visio.Page.Print](HV10070404).  
  
## Stampa di un documento di Visio  
  
#### Per stampare un documento completo  
  
-   Chiamare il metodo Microsoft.Office.Interop.Visio.Document.Print dell'oggetto Microsoft.Office.Interop.Visio.Document da stampare.  
  
     L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#8)]  
  
## Stampa di una pagina di un documento di Visio  
  
#### Per stampare una pagina di un documento  
  
-   Chiamare il metodo Microsoft.Office.Interop.Visio.Pages.Print dell'oggetto Microsoft.Office.Interop.Visio.Pages da stampare.  
  
     L'esempio di codice seguente stampa la prima pagina del documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: Creare nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: Aprire documenti di Visio a livello di codice](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: Chiudere documenti di Visio a livello di codice](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: Salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  