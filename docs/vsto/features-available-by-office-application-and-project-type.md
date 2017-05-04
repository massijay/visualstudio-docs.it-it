---
title: "Funzionalit&#224; disponibili in base ai tipi di progetto e applicazioni di Office | Microsoft Docs"
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
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio]"
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio]"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio]"
  - "aree di modulo [sviluppo per Office in Visual Studio], funzionalità disponibili"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], funzionalità disponibili"
  - "sviluppo per Office in Visual Studio, funzionalità"
  - "progetti Office [sviluppo per Office in Visual Studio], funzionalità disponibili"
  - "barra multifunzione [sviluppo per Office in Visual Studio]"
ms.assetid: 3e9aa4d3-affb-4f76-bc67-49fe5f26a6a1
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Funzionalit&#224; disponibili in base ai tipi di progetto e applicazioni di Office
  In Visual Studio sono disponibili numerosi tipi di modelli di progetto che supportano scenari aziendali diversi per le applicazioni di Microsoft Office, inclusi i tipi seguenti:  
  
-   Personalizzazioni a livello di documento.  
  
-   Componenti aggiuntivi VSTO.  
  
 Non tutte le applicazioni possono utilizzare ogni tipo di progetto.  Ad esempio, i progetti a livello di documento sono disponibili solo per Microsoft Office Word e Microsoft Office Excel.  Analogamente, alcune funzionalità sono disponibili solo per determinati tipi di progetti o applicazioni.  Ad esempio, il riquadro azioni è disponibile solo nei progetti a livello di documento e le estensioni della barra multifunzione sono disponibili solo per alcune applicazioni.  Per altre informazioni su questi tipi di progetti, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Modelli di progetto di Office sono disponibili solo in alcune edizioni di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].   Per ulteriori informazioni, vedere [Configurazione di un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## Tipi di progetto disponibili per applicazioni di Microsoft Office diverse  
 Nella tabella seguente sono indicate le applicazioni che è possibile utilizzare con ogni tipo di progetto.  
  
|Tipi di progetto|Applicazione Microsoft Office|  
|----------------------|-----------------------------------|  
|Personalizzazioni a livello di documento|Excel<br /><br /> Word|  
|Componenti aggiuntivi VSTO|Excel<br /><br /> InfoPath \(solo InfoPath 2013 e InfoPath 2010\)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Progetto<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## Funzionalità disponibili in diversi tipi di progetto  
 Nella tabella seguente sono indicati i tipi di progetto che forniscono ciascuna funzionalità.  
  
|Funzionalità|Tipi di progetto che forniscono la funzionalità|Ulteriori informazioni|  
|------------------|-----------------------------------------------------|----------------------------|  
|Riquadro azioni.|Progetti a livello di documento.|[Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)|  
|Distribuzione ClickOnce.|Progetti a livello di documento e VS.|[Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)|  
|Riquadri attività personalizzati.|Progetti di componente aggiuntivo VSTO per le applicazioni seguenti:<br /><br /> -   Excel<br />-   InfoPath \(solo InfoPath 2013 e InfoPath 2010\)<br />-   Outlook<br />-   PowerPoint<br />-   Word|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
|Parti XML personalizzate.|Progetti a livello di documento.<br /><br /> Progetti di livello applicazione per le applicazioni seguenti:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|[Cenni preliminari sulle web part XML personalizzate](../vsto/custom-xml-parts-overview.md)|  
|Cache dei dati.|Progetti a livello di documento.|[Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)|  
|Esporre un oggetto in un componente aggiuntivo VSTO ad altre soluzioni Microsoft Office.|Progetti di componente aggiuntivo VSTO.|[Chiamata di codice nei componenti aggiuntivi VSTO da altre soluzioni Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|I controlli host seguenti:<br /><br /> -   Grafico<br />-   ListObject<br />-   NamedRange<br />-   Controlli del contenuto<br />-   Segnalibro|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO per Word ed Excel.|[Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)|  
|I controlli host seguenti:<br /><br /> -   XMLMappedRange \(controllo\)<br />-   XMLNode<br />-   XMLNodes|Progetti a livello di documento.|[Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)|  
|Distribuzione di più progetti.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO.|[Procedura dettagliata: distribuzione di più soluzioni Office in un unico programma di installazione ClickOnce](http://msdn.microsoft.com/it-it/051223c0-4082-4799-b78b-a4763a9def55)|  
|Aree di modulo di Outlook.|Progetti di componente aggiuntivo VSTO per Outlook.|[Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)|  
|Azioni di post\-distribuzione.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO.|[Procedura dettagliata: copia di un documento nel computer dell'utente finale dopo un'installazione ClickOnce](http://msdn.microsoft.com/it-it/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Personalizzazioni della barra multifunzione.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO per le applicazioni seguenti:<br /><br /> -   Excel<br />-   InfoPath \(solo InfoPath 2013 e InfoPath 2010\)<br />-   Outlook<br />-   PowerPoint<br />-   Progetto<br />-   Visio<br />-   Word|Per altre informazioni, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).|  
|Programma di creazione documenti visivi.|Progetti a livello di documento.|[Progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## Vedere anche  
 [Guida introduttiva &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)   
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  