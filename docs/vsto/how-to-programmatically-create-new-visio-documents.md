---
title: "Procedura: Creare nuovi documenti di Visio a livello di codice"
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
  - "Visio [sviluppo per Office in Visual Studio], creazione di documenti di Visio"
  - "documenti [sviluppo per Office in Visual Studio], creazione di documenti di Visio"
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Procedura: Creare nuovi documenti di Visio a livello di codice
  Quando si crea un nuovo disegno di Microsoft Office Visio, viene aggiunto alla raccolta Microsoft.Office.Interop.Visio.Documents di documenti di Visio aperti. Il metodo Microsoft.Office.Interop.Visio.Documents.Add crea quindi un nuovo documento di disegno di Visio. Per altre informazioni, vedere la documentazione di riferimento di VBA relativa al metodo [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241).  
  
## Creazione di nuovi documenti vuoti  
  
#### Per creare un nuovo documento  
  
-   Usare il metodo Microsoft.Office.Interop.Visio.Documents.Add per creare un nuovo documento vuoto che non si basa su un modello.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## Creazione di documenti copiati da documenti esistenti  
 Il metodo Microsoft.Office.Interop.Visio.Documents.Add può creare un nuovo documento che è una copia di un documento di Visio esistente. È necessario specificare il nome file e il percorso completo del diagramma.  
  
#### Per creare un nuovo documento copiato da un documento esistente  
  
-   Chiamare il metodo Microsoft.Office.Interop.Visio.Documents.Add e specificare il percorso del diagramma di Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## Creazione di stencil copiati da stencil esistenti  
 Il metodo [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) può creare un nuovo stencil che è una copia di uno stencil di Visio esistente. È necessario specificare il nome file e il percorso completo dello stencil.  
  
#### Per creare un nuovo stencil copiato da uno stencil esistente  
  
-   Chiamare il metodo Microsoft.Office.Interop.Visio.Documents.Add e specificare il percorso dello stencil.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Creazione di documenti basati su modelli esistenti  
 Il metodo Microsoft.Office.Interop.Visio.Documents.Add può creare un nuovo documento \(file con estensione vsd\) basato su un modello di Visio esistente \(file con estensione vst\). Questo metodo copia gli stencil, gli stili e le impostazioni che fanno parte dell'area di lavoro modello. È necessario specificare il nome file e il percorso completo del modello.  
  
#### Per creare un nuovo documento basato su un modello esistente  
  
-   Chiamare il metodo Microsoft.Office.Interop.Visio.Documents.Add e specificare il percorso del modello.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Compilazione del codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Deve essere presente un documento di Visio denominato `myDrawing.vsd` in una directory denominata `Test` nella cartella Documenti.  
  
-   Deve essere presente un documento di Visio denominato `myStencil.vss` in una directory denominata `Test` nella cartella Documenti.  
  
-   Deve essere presente un documento di Visio denominato `myTemplate.vst` in una directory denominata `Test` nella cartella Documenti.  
  
## Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: Aprire documenti di Visio a livello di codice](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: Chiudere documenti di Visio a livello di codice](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: Salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Procedura: Stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  