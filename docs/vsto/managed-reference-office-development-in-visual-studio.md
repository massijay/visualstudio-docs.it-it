---
title: "Riferimenti gestiti (sviluppo per Office in Visual Studio) | Microsoft Docs"
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
  - "riferimenti [sviluppo per Office in Visual Studio], Microsoft Office System 2007"
  - "sviluppo per Office in Visual Studio, riferimenti"
ms.assetid: 1fa66da0-9d90-4524-ba4f-4da13aab73b5
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Riferimenti gestiti (sviluppo per Office in Visual Studio)
  Questa sezione include documentazione di riferimento alle API per gli spazi dei nomi e i tipi usati nei progetti di Office destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per la documentazione di riferimento alle API sugli spazi dei nomi e i tipi usati nei progetti di Office destinati a .NET Framework 3.5, vedere la sezione di riferimento seguente nella documentazione di Visual Studio: [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
## Contenuto della sezione  
 <xref:Microsoft.Office.Tools>  
 Contiene classi comuni per la programmazione di soluzioni Office. Includono la classe base per i componenti aggiuntivi VSTO, classi per la creazione di riquadri attività personalizzati nei componenti aggiuntivi VSTO, classi per la creazione di smart tag nelle soluzioni Excel e Word e classi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento.  
  
 <xref:Microsoft.Office.Tools.Excel>  
 Contiene i controlli e gli elementi host che si possono usare nelle soluzioni per Excel.  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 Contiene i controlli Excel e Windows Form che si possono usare nelle soluzioni per Excel.  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 Contiene le classi usate dai componenti aggiuntivi VSTO per Outlook, comprese le classi usate per creare aree del modulo personalizzate.  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 Contiene le classi usate per modificare a livello di codice le personalizzazioni della barra multifunzione create usando la finestra di progettazione della barra multifunzione.  
  
 <xref:Microsoft.Office.Tools.Word>  
 Contiene i controlli e gli elementi host che si possono usare nelle soluzioni per Word.  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 Contiene i controlli Word e Windows Form che si possono usare nelle soluzioni per Word.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 Contiene la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> e un set di classi di dati memorizzati nella cache correlate. Queste classi possono essere usate per modificare alcuni aspetti delle personalizzazioni a livello di documento nei computer in cui non è installato Microsoft Office.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 Contiene l'interfaccia <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> \(che è possibile implementare per creare un'*azione post\-distribuzione* per una soluzione Office\), le eccezioni che possono essere generate quando si installa una soluzione Office e altre API che appartengono all'infrastruttura di Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 Contiene la maggior parte delle eccezioni che possono essere generate da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], diverse classi che si possono usare per memorizzare i dati nelle personalizzazioni a livello di documento e altre API che fanno parte dell'infrastruttura di Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 Contiene classi di attività MSBuild che vengono usate per compilare progetti di Office.  
  
## Vedere anche  
 [Panoramica di Visual Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Guida introduttiva &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  