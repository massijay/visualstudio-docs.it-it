---
title: "Soluzioni Outlook | Microsoft Docs"
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
  - "soluzioni [sviluppo per Office in Visual Studio], Outlook"
  - "progetti di Office [sviluppo per Office in Visual Studio], Outlook"
  - "soluzioni Office [sviluppo per Office in Visual Studio], Outlook"
  - "modelli [sviluppo per Office in Visual Studio], Outlook"
  - "progetti [sviluppo per Office in Visual Studio], Outlook"
  - "Outlook [sviluppo per Office in Visual Studio]"
  - "posta elettronica [sviluppo per Office in Visual Studio], soluzioni Outlook"
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Soluzioni Outlook
  Visual Studio offre modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Outlook. È possibile usare i componenti aggiuntivi VSTO per automatizzare Outlook, estenderne le funzionalità o personalizzarne l'interfaccia utente. Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Creazione di un nuovo progetto di componente aggiuntivo VSTO di Outlook  
 Creare progetti Outlook usando uno dei modelli di progetto **Componente aggiuntivo per Outlook** nella finestra di dialogo **Nuovo progetto**. Questo modello include i riferimenti agli assembly e i file di progetto necessari.  
  
 Per altre informazioni sulla creazione di un progetto di componente aggiuntivo VSTO, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per altre informazioni sui modelli di progetto, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
## Modello di programmazione dei componenti aggiuntivi VSTO per Outlook  
 Quando si crea un progetto di componente aggiuntivo VSTO per Outlook, Visual Studio genera una classe, chiamata `ThisAddIn`, che costituisce la base della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone inoltre il modello a oggetti di Outlook nel componente aggiuntivo VSTO.  
  
 Per altre informazioni sulla classe `ThisAddIn` e su altre funzionalità che è possibile usare in un componente aggiuntivo VSTO, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
## Automazione di Outlook mediante il modello a oggetti di Outlook  
 Il modello a oggetti di Outlook espone diversi tipi che è possibile usare per automatizzare Outlook. Questi tipi consentono di scrivere il codice per eseguire attività comuni:  
  
-   Creare e inviare messaggi di posta elettronica a livello di codice.  
  
-   Inviare nuove convocazioni riunione.  
  
-   Cercare elementi in cartelle di Outlook.  
  
 Per altre informazioni, vedere [Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md).  
  
## Personalizzazione dell'interfaccia utente di un'applicazione di Outlook  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Aggiungere schede personalizzate alla barra multifunzione di un controllo di Outlook.|[Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)|  
|Aggiungere gruppi personalizzati a una scheda predefinita in un controllo di Outlook.|[Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|  
|Aggiungere un riquadro attività personalizzato da visualizzare in un controllo di Outlook|[Riquadri attività personalizzati](../vsto/custom-task-panes.md).|  
|Aggiungere un'area del modulo che estende o sostituisce moduli di Outlook esistenti.|[Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Per altre informazioni sulla personalizzazione dell'interfaccia utente di Outlook e di altre applicazioni di Microsoft Office, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)|Contiene una panoramica degli oggetti forniti dal modello a oggetti di Word.|  
|[Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)|Descrive gli strumenti disponibili in Visual Studio che semplificano la progettazione, lo sviluppo e il debug delle aree del modulo.|  
|[Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Mostra come creare un componente aggiuntivo VSTO per Microsoft Office Outlook.|  
|[Outlook 2010 nello sviluppo di applicazioni per Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Area di MSDN Library in cui è possibile trovare articoli e documentazione di riferimento sullo sviluppo di soluzioni Office \(non specifiche per lo sviluppo di Office con Visual Studio\).|  
  
  