---
title: "Guida introduttiva alla programmazione di personalizzazioni a livello di documento per Excel | Microsoft Docs"
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
  - "Excel (progetti) [sviluppo per Office in Visual Studio], introduzione"
  - "Excel (soluzioni in Visual Studio)"
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Guida introduttiva alla programmazione di personalizzazioni a livello di documento per Excel
  Chi sta iniziando ad creazione di personalizzazioni a livello di documento per Microsoft Office Excel con Visual Studio, ecco cosa è necessario conoscere.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## Funzionamento delle personalizzazioni a livello di documento per Excel  
 Una personalizzazione a livello di documento per Excel è basata su una sola cartella di lavoro.  Per iniziare a utilizzare la personalizzazione, l'utente finale apre la cartella di lavoro o la crea da un modello di Excel.  Gli eventi presenti nella cartella di lavoro, come ad esempio l'immissione all'interno delle celle o la scelta di pulsanti e voci di menu, possono chiamare metodi di gestione degli eventi nell'assembly.  Quando la cartella di lavoro viene chiusa, le funzionalità fornite dalla personalizzazione non sono più disponibili in Excel, solo nel documento che le ha contenute.  
  
 Per ulteriori informazioni, vedere [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
## Creazione di progetti a livello di documento per Excel  
 Per creare una personalizzazione a livello di documento per Excel, utilizzare il modello di progetto Cartella di lavoro di Excel o Modello di Excel nella finestra di dialogo **Nuovo progetto**.  Questi modelli includono riferimenti ad assembly e file di progetto necessari.  
  
 Per ulteriori informazioni su come creare un progetto a livello di documento per Excel, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Per ulteriori informazioni sui modelli di progetto, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
## Programmazione di cartelle di lavoro di Excel utilizzando elementi host e controlli host  
 *Gli elementi host* e *controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento create tramite Visual Studio.  
  
 Gli elementi host forniscono un punto di ingresso per il codice e possono funzionare da contenitori per i controlli host e Windows Form.  Nei progetti a livello di documento per Excel, questi elementi host sono rappresentati da classi `ThisWorkbook`, `Sheet1`, `Sheet2`e `Sheet3`.  
  
 I controlli host sono basati su oggetti Excel nativi, ad esempio oggetti elenco e intervalli.  I controlli host, oltre a presentare funzionalità analoghe a quelle degli oggetti Excel nativi, forniscono anche il supporto della finestra di progettazione nonché nuovi eventi e funzionalità di associazione dati.  Tali controlli vengono visualizzati come oggetti di primaria importanza nel codice del progetto e in IntelliSense, il che rende più semplice fare riferimento a oggetti specifici direttamente nel codice senza dover ricorrere al modello a oggetti di Excel.  
  
 Per ulteriori informazioni, vedere i seguenti argomenti:  
  
-   [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)  
  
-   [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
## Personalizzazione dell'interfaccia utente di Excel  
 Nella maggior parte delle soluzioni di Microsoft Office, l'interfaccia utente \(UI, User Interface\) dell'applicazione di Office viene modificata allo scopo di consentire agli utenti di interagire con la soluzione.  Una personalizzazione a livello di documento consente di modificare vari aspetti dell'UI di Excel.  Ad esempio, è possibile aggiungere controlli alla barra multifunzione, o visualizzare un riquadro azioni.  Per ulteriori informazioni, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
 È inoltre possibile aprire la cartella di lavoro associata direttamente al progetto in Visual Studio.  Quando la cartella di lavoro viene aperta in Visual Studio, è possibile modificare la cartella di lavoro tramite l'interfaccia utente di Excel.  È inoltre possibile utilizzare la cartella di lavoro come un'area di progettazione che consente di trascinare i controlli sui fogli di lavoro.  Per ulteriori informazioni, vedere [Progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Utilizzo dell'associazione dati  
 I controlli host fanno anch'essi parte dell'elenco di controllo che è possibile trascinare dalla finestra **Origini dati**.  Aggiungendo controlli host in questo modo li si associa automaticamente all'origine dati impostata utilizzando la finestra.  Senza scrivere codice, è possibile visualizzare i dati da database, i servizi web e oggetti business.  Per ulteriori informazioni, vedere [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## Passaggi successivi  
 Per informazioni su come creare una personalizzazione a livello di documento per Excel, vedere [Procedura dettagliata: creazione di una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md).  In questa procedura dettagliata vengono introdotti gli strumenti di sviluppo di Office in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Excel.  
  
 Per un elenco degli argomenti che analizzano alcune delle comuni attività nei progetti di Excel, vedere [Attività comuni nella programmazione con Office](../vsto/common-tasks-in-office-programming.md).  
  
## Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Soluzioni Excel](../vsto/excel-solutions.md)   
 [Procedura dettagliata: creazione di una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)   
 [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)  
  
  