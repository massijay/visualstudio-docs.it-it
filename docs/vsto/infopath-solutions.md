---
title: "Soluzioni InfoPath | Microsoft Docs"
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
  - "soluzioni [sviluppo per Office in Visual Studio], InfoPath"
  - "modelli [sviluppo per Office in Visual Studio], InfoPath"
  - "InfoPath [sviluppo per Office in Visual Studio]"
  - "sviluppo per Office in Visual Studio, soluzioni InfoPath"
  - "progetti [sviluppo per Office in Visual Studio], InfoPath"
  - "soluzioni Office [sviluppo per Office in Visual Studio], InfoPath"
  - "progetti di Office [sviluppo per Office in Visual Studio], InfoPath"
ms.assetid: 20ac6bee-b17f-4217-9f78-11304a11236a
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Soluzioni InfoPath
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office InfoPath 2013 e InfoPath 2010. InfoPath non è disponibile in Office 2016.  
  
> [!NOTE]  
>  È comunque possibile creare un componente aggiuntivo VSTO per InfoPath anche se è installato Office 2016. È sufficiente installare InfoPath 2013 o Office 2013 side\-by\-side con Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
 I componenti aggiuntivi VSTO per InfoPath sono simili ai componenti aggiuntivi VSTO per altre applicazioni di Microsoft Office. Questi tipi di soluzioni sono costituiti da un assembly caricato dall'applicazione. Gli utenti finali possono avere accesso alle funzionalità di questo assembly indipendentemente dal modulo o dal modello di modulo aperto. Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 non include i progetti del modello di modulo InfoPath forniti nelle versioni precedenti di Visual Studio. Non è nemmeno possibile usare Visual Studio 2015 per aprire o modificare un progetto del modello di modulo InfoPath creato in una versione precedente di Visual Studio. Tuttavia, è possibile aprire e modificare un progetto del modello di modulo InfoPath usando Visual Studio Tools for Applications. Per altre informazioni, vedere [Uso dei progetti VSTO 2008 in InfoPath 2010](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## Automazione di InfoPath usando un componente aggiuntivo  
 Per accedere al modello a oggetti InfoPath da un componente aggiuntivo VSTO di Office creato mediante gli strumenti di sviluppo per Office in Visual Studio, usare il campo `Application` della classe `ThisAddIn` nel progetto. Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.InfoPath.Application> che rappresenta l'istanza corrente di InfoPath. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quando si effettuano chiamate nel modello a oggetti InfoPath da un componente aggiuntivo VSTO, si usano i tipi che sono stati forniti nell'assembly di interoperabilità primario per InfoPath. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in InfoPath. Tutti i tipi nell'assembly di interoperabilità primario di InfoPath sono definiti nello spazio dei nomi <xref:Microsoft.Office.Interop.InfoPath>. Per altre informazioni sull'assembly di interoperabilità primario di InfoPath, vedere [Informazioni sull'assembly di interoperabilità primario di Microsoft Office InfoPath](http://msdn.microsoft.com/it-it/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Per altre informazioni sugli assembly di interoperabilità primari in generale, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
## Personalizzazione dell'interfaccia utente di InfoPath usando un componente aggiuntivo  
 Quando si crea un componente aggiuntivo VSTO per InfoPath, sono disponibili varie opzioni di personalizzazione dell'interfaccia utente. Nella tabella riportata di seguito vengono elencate alcune di queste opzioni.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
|Aggiungere schede personalizzate alla barra multifunzione in InfoPath.|[Personalizzazione di una barra multifunzione per InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Per altre informazioni sulla personalizzazione dell'interfaccia utente di InfoPath e di altre applicazioni di Microsoft Office, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## Vedere anche  
 [Informazione sull'assembly di interoperabilità primario di Microsoft Office InfoPath](http://msdn.microsoft.com/it-it/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [InfoPath 2010 nello sviluppo di applicazioni per Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  