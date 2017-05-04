---
title: "Guida introduttiva alla programmazione delle personalizzazioni a livello di documento per Word | Microsoft Docs"
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
  - "Word (progetti) [sviluppo per Office in Visual Studio], introduzione"
  - "Word (soluzioni in Visual Studio)"
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Guida introduttiva alla programmazione delle personalizzazioni a livello di documento per Word
  Chi sta iniziando ad creazione di personalizzazioni a livello di documento per Microsoft Office Word utilizzando Visual Studio, ecco cosa è necessario conoscere.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## Funzionamento delle personalizzazioni a livello di documento per Word  
 Ogni personalizzazione per Word creata è basata su un singolo documento.  Per iniziare a utilizzare la personalizzazione, l'utente finale apre il documento o lo crea da un modello di Word.  Gli eventi presenti nel documento, ad esempio lo spostamento del cursore in aree specifiche o la scelta di pulsanti e voci di menu, possono chiamare metodi di gestione degli eventi nell'assembly.  Quando il documento viene chiuso, le funzionalità fornite dalla personalizzazione non sono più disponibili in Word.  
  
 Per ulteriori informazioni, vedere [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
## Creazione di progetti a livello di documento per Word  
 Per creare una personalizzazione a livello di documento per Word, utilizzare il modello di progetto relativo al documento o al modello di Word nella finestra di dialogo **Nuovo progetto**.  Questi modelli includono riferimenti ad assembly e file di progetto necessari.  
  
 Per ulteriori informazioni su come creare un progetto a livello di documento per Word, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Per ulteriori informazioni sui modelli di progetto, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
## Programmazione di documenti di Word utilizzando controlli host di elementi host  
 Gli *elementi host* e i *controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento.  
  
 Gli elementi host forniscono un punto di ingresso per il codice e possono funzionare da contenitori per i controlli host e Windows Form.  Nei progetti a livello di documento di Word, l'elemento host viene rappresentato dalla classe `ThisDocument`.  
  
 I controlli host sono basati su oggetti Word nativi, ad esempio controlli del contenuto, segnalibri e nodi XML.  I controlli host, oltre a presentare funzionalità analoghe a quelle degli oggetti Word nativi, forniscono anche il supporto della finestra di progettazione nonché nuovi eventi e funzionalità di associazione dati.  Tali controlli vengono visualizzati come oggetti di primaria importanza nel codice del progetto e in IntelliSense, il che rende più semplice fare riferimento a oggetti specifici direttamente nel codice senza dover ricorrere al modello a oggetti di Word.  
  
 Per ulteriori informazioni, vedere i seguenti argomenti:  
  
-   [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)  
  
-   [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
## Personalizzazione dell'interfaccia utente di Word  
 Nella maggior parte delle soluzioni di Microsoft Office, l'interfaccia utente \(UI, User Interface\) dell'applicazione di Office viene modificata allo scopo di consentire agli utenti di interagire con la soluzione.  Una personalizzazione a livello di documento consente di modificare vari aspetti dell'interfaccia utente di Word.  Ad esempio, è possibile aggiungere controlli alla barra multifunzione e visualizzare un riquadro azioni.  Per ulteriori informazioni, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
 È inoltre possibile aprire il documento associato direttamente al progetto in Visual Studio.  Quando il documento viene aperto in Visual Studio, è possibile modificare il documento tramite l'interfaccia utente di Word.  È inoltre possibile utilizzare il documento come un'area di progettazione che consente di trascinare i controlli su di esso.  Per ulteriori informazioni, vedere [Progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Associazione dei controlli ai dati  
 I controlli del contenuto e il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> sono nell'elenco dei controlli trascinabili dalla finestra **Origini dati**.  Aggiungendo controlli del contenuto e segnalibri in questo modo, li si associa automaticamente all'origine dati impostata utilizzando la finestra.  Senza scrivere codice, è possibile visualizzare i dati da database, servizi e oggetti business.  Per ulteriori informazioni, vedere [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## Passaggi successivi  
 Per informazioni su come creare una personalizzazione a livello di documento per Word, vedere [Procedura dettagliata: creazione di una personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md).  In questa procedura dettagliata vengono introdotti gli strumenti di sviluppo di Office in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Word.  
  
 Per un elenco degli argomenti che analizzano alcune delle comuni attività nei progetti di Word, vedere [Attività comuni nella programmazione con Office](../vsto/common-tasks-in-office-programming.md).  
  
## Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Soluzioni Word](../vsto/word-solutions.md)   
 [Procedura dettagliata: creazione di una personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)  
  
  