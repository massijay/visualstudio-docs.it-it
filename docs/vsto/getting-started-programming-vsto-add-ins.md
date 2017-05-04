---
title: "Introduzione alla programmazione di componenti aggiuntivi VSTO | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.Outlook"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], introduzione"
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio], introduzione"
ms.assetid: 9ac1e6ea-9511-4633-80f9-dc7641f22b63
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Introduzione alla programmazione di componenti aggiuntivi VSTO
  È possibile usare componenti aggiuntivi VSTO per automatizzare le applicazioni di Microsoft Office, estendere le funzionalità dell'applicazione e personalizzare l'interfaccia utente dell'applicazione.  Per informazioni sul confronto tra i componenti aggiuntivi VSTO e altri tipi di soluzioni Office che è possibile creare mediante Visual Studio, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Creazione di progetti di componente aggiuntivo VSTO  
 Per creare progetti di componente aggiuntivo VSTO, usare uno dei modelli di progetto di componente aggiuntivo VSTO contenuti nella finestra di dialogo **Nuovo progetto**.  Questi modelli includono riferimenti dell'assembly e file di progetto necessari.  Visual Studio offre modelli di progetto di componente aggiuntivo VSTO per la maggior parte delle applicazioni di Office.  
  
 Per altre informazioni su come creare un progetto di componente aggiuntivo VSTO, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Per ulteriori informazioni sui modelli di progetto, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
## Sviluppo di progetti di componente aggiuntivo VSTO  
 Quando si crea un progetto di componente aggiuntivo VSTO, Visual Studio crea automaticamente un file di codice ThisAddIn.vb \(in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) o un file di codice ThisAddIn.cs \(in C\#\).  Questo file contiene la classe `ThisAddIn`, che fornisce le basi per il componente aggiuntivo VSTO.  È possibile usare i membri di questa classe per eseguire il codice quando il componente aggiuntivo VSTO viene caricato o scaricato, per accedere al modello a oggetti dell'applicazione host e per estendere le funzionalità dell'applicazione.  Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
## Automazione di applicazioni utilizzando i modelli a oggetti  
 I modelli a oggetti delle applicazioni di Microsoft Office espongono molti tipi per i quali è possibile eseguire la programmazione in un componente aggiuntivo VSTO.  È possibile utilizzare questi tipi per automatizzare l'applicazione.  Ad esempio, a livello di programmazione, è possibile creare e inviare un messaggio di posta elettronica in Outlook o è possibile aprire un documento e aggiungere contenuto in Word.  Per ulteriori informazioni su come accedere al modello a oggetti dell'applicazione host nel codice, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Per altre informazioni sui modelli a oggetti di applicazioni specifiche di Microsoft Office, vedere gli argomenti seguenti:  
  
-   [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)  
  
-   [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)  
  
-   [Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Soluzioni InfoPath](../vsto/infopath-solutions.md)  
  
-   [Soluzioni PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Soluzioni Project](../vsto/project-solutions.md)  
  
-   [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)  
  
## Personalizzazione dell'interfaccia utente delle applicazioni  
 Esistono diversi modi per personalizzare l'interfaccia utente dell'applicazione host mediante un componente aggiuntivo VSTO:  
  
-   Per Excel e Word, è possibile aggiungere controlli gestiti ai documenti.  Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Se l'applicazione la supporta, è possibile personalizzare la barra multifunzione.  Per altre informazioni, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  
  
-   Se l'applicazione lo supporta, è possibile creare un riquadro attività personalizzato.  Per altre informazioni, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
-   Per Outlook, è possibile creare un'area del modulo personalizzato.  Per altre informazioni, vedere [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md).  
  
-   Per tutte le applicazioni di Microsoft Office, è possibile visualizzare Windows Form nel componente aggiuntivo VSTO.  
  
 Per altre informazioni su come personalizzare l'interfaccia utente delle applicazioni di Microsoft Office, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## Passaggi successivi  
 Per informazioni su come creare componenti aggiuntivi VSTO, vedere le procedure dettagliate seguenti:  
  
-   [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 Queste procedure dettagliate presentano gli strumenti di sviluppo per Office disponibili in Visual Studio e il modello di programmazione per i componenti aggiuntivi VSTO.  
  
 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Office, vedere [Attività comuni nella programmazione con Office](../vsto/common-tasks-in-office-programming.md).  
  
## Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Guida introduttiva &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)  
  
  