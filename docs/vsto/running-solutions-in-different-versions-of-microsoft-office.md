---
title: "Esecuzione di soluzioni in versioni diverse di Microsoft Office | Microsoft Docs"
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
  - "più versioni di Office"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], più versioni di Office"
  - "sviluppo per Office in Visual Studio, più versioni di Office"
  - "Soluzioni Office [sviluppo per Office in Visual Studio]"
  - "soluzioni [sviluppo per Office in Visual Studio], più versioni di Office"
ms.assetid: 414e7741-c07d-4900-9d10-68b821413b3f
caps.latest.revision: 61
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# Esecuzione di soluzioni in versioni diverse di Microsoft Office
    
## Esecuzione di soluzioni Office create mediante Visual Studio 2010 e versioni successive  
  
|Versione di destinazione del modello di progetto di Office|Scegliere .NET Framework del progetto<sup>1</sup>|Versioni di Office che possono eseguire la soluzione|Runtime richiesto sul computer dell'utente finale|  
|----------------------------------------------------------------|-------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------|  
|Office 2016 e [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office System 2007<sup>2</sup>|Visual Studio 2010 Tools per Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office System 2007<sup>2</sup>|Visual Studio 2010 Tools per Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools per Office Runtime|  
|Microsoft Office System 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive,<br /><br /> oppure<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office System 2007|Visual Studio 2010 Tools per Office Runtime|  
  
 1.  Perché la soluzione funzioni è necessario che nei computer degli utenti finali sia installata la versione di .NET Framework di destinazione del progetto.  Ad esempio, se il progetto è per .NET Framework 3.5, sui computer degli utenti finali deve essere installato .NET Framework 3.5.  In questo esempio, la soluzione non verrà eseguita se nei computer degli utenti finali è installato solo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
 2.  In questo scenario, la soluzione verrà eseguita senza errori in Microsoft Office System 2007 solo se non utilizza funzionalità introdotte in [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
## Esecuzione di soluzioni Office create utilizzando versioni di Visual Studio precedenti a Visual Studio 2010  
 Le applicazioni Microsoft Office possono eseguire soluzioni create utilizzando versioni di Visual Studio precedenti a Visual Studio 2010.  In alcuni casi, queste soluzioni richiedono versioni diverse di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Versioni diverse del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] possono essere installate nello stesso computer.  
  
 Nella tabella seguente sono indicate le versioni di Microsoft Office che possono eseguire soluzioni create con versioni precedenti di Visual Studio e le versioni di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e .NET Framework necessarie per ciascuna soluzione.  
  
|Edizione di Visual Studio utilizzate per creare la soluzione|Versione di destinazione del modello di progetto di Office|Versioni di Office che possono eseguire la soluzione|Runtime richiesto sul computer dell'utente finale|Versione di .NET Framework richiesta nel computer dell'utente finale|  
|------------------------------------------------------------------|----------------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------|--------------------------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> o<br /><br /> Visual Studio Team System 2008|Microsoft Office System 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<sup>1</sup><br /><br /> Microsoft Office System 2007|Visual Studio 2010 Tools per Office Runtime<sup>1</sup><br /><br /> oppure<br /><br /> Microsoft Visual Studio Tools per Microsoft Office System \(versione 3.0 Runtime\)|.NET Framework 3.5|  
|Una delle seguenti edizioni di Visual Studio 2005 con VSTO 2005 SE<sup>2</sup> installato:<br /><br /> -   Visual Studio 2005 Tools per Office<br />-   Visual Studio Team System 2005<br />-   Visual Studio 2005 Professional|Microsoft Office System 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] \(solo 32 bit<sup>3</sup>\)<br /><br /> Microsoft Office System 2007|Microsoft Visual Studio 2005 Tools per Office Second Edition Runtime \(x86\)|.NET framework 2.0, .NET Framework 3.0 o .NET Framework 3.5|  
|Una delle seguenti edizioni di Visual Studio:<br /><br /> -   Visual Studio 2008 Professional<br />-   Visual Studio Team System 2008<br />-   Visual Studio 2005 Tools per Office \(con o senza VSTO 2005 SE<sup>2</sup> installato\)<br />-   Visual Studio Team System 2005 \(con o senza VSTO 2005 SE<sup>2</sup> installato\)<br />-   Visual Studio 2005 Professional con VSTO 2005 SE<sup>2</sup> installato|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] \(solo 32 bit<sup>3</sup>\)<br /><br /> Microsoft Office System 2007<br /><br /> Microsoft Office 2003|Microsoft Visual Studio 2005 Tools per Office Second Edition Runtime \(x86\)|.NET framework 2.0, .NET Framework 3.0 o .NET Framework 3.5|  
  
 1.  [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] includono Visual Studio 2010 Tools per Office Runtime. Pertanto, queste applicazioni utilizzano sempre Visual Studio 2010 Tools per Office Runtime anziché Visual Studio Tools per Microsoft Office System \(versione 3.0 Runtime\) in questo scenario.  Le applicazioni di Microsoft Office 2007 possono utilizzare Visual Studio 2007 Tools per Office Runtime o Visual Studio Tools per Microsoft Office System \(versione 3.0 Runtime\).  
  
 2.  VSTO 2005 SE è un componente aggiuntivo di Visual Studio gratuito che fornisce modelli di progetto di componente aggiuntivo VSTO per Microsoft Office 2003 e Microsoft Office System 2007.  Può essere installato con Visual Studio 2005 Professional, Visual Studio 2005 Tools per Office o un'edizione di Visual Studio Team System 2005.  Per ulteriori informazioni, vedere [Visual Studio 2005 Tools per Office Second Edition](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3.  Le soluzioni Office che richiedono Visual Studio 2005 Tools per Office Second Edition Runtime non sono compatibili con le versioni a 64 bit di [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  Per eseguire queste soluzioni nell'edizione a 64 bit di [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], è necessario aggiornare il progetto a [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] o a un progetto di Visual Studio 2008 destinato a Microsoft Office System 2007.  
  
## Vedere anche  
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Panoramica di Visual Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Scenari di installazione del runtime di Visual Studio Tools per Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Configurazione di un computer per lo sviluppo di soluzioni Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  