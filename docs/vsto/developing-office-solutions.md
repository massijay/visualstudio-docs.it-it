---
title: "Sviluppo di soluzioni Office"
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
  - "sviluppo per Office in Visual Studio, informazioni sullo sviluppo di soluzioni"
  - "soluzioni [sviluppo per Office in Visual Studio], sviluppo"
  - "soluzioni Office [sviluppo per Office in Visual Studio], sviluppo"
ms.assetid: 7361cfe0-dee4-48d7-a066-232f87f093ca
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Sviluppo di soluzioni Office
  Dopo aver progettato un progetto usando gli strumenti di sviluppo di Office in Visual Studio e configurato i file di progetto, è possibile iniziare a concentrarsi sull'implementazione del codice e dell'interfaccia utente personalizzata.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Modello di programmazione delle soluzioni Office  
 Il modello a oggetti Office espone una serie di oggetti programmabili. Ogni volta che è possibile programmare soluzioni Office usando codice gestito, è necessario scrivere codice che usa tipi negli assembly di interoperabilità primari di Office. Nelle soluzioni create mediante i modelli di progetto di Office in Visual Studio, è inoltre possibile scrivere il codice direttamente per le classi generate del progetto. Per altre informazioni, vedere [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md).  
  
## Programmazione di tipi diversi di soluzioni Office  
 Il tipo di soluzione che si sta creando determina le funzionalità che è possibile usare nel progetto. Ad esempio, è possibile aggiungere controlli Windows Form e controlli estesi di Office \(denominato *controlli host*\) alle personalizzazioni a livello di documento trascinando gli elementi dalla **casella degli strumenti** in Visual Studio in fase di progettazione. Tuttavia, se si sviluppa un componente aggiuntivo VSTO, è possibile aggiungere questi tipi di controlli solo a documenti in fase di esecuzione, mediante la scrittura di codice.  
  
 Per altre informazioni sulle funzionalità specifiche di tipi diversi di soluzioni, vedere gli argomenti seguenti:  
  
-   [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).  
  
-   [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
 Per informazioni generali utili per pianificare le procedure e soluzioni Office per creare progetti, vedere [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)|Vengono descritti diversi aspetti della scrittura del codice nelle soluzioni Office.|  
|[Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)|Offre una panoramica del modello di programmazione dei componenti aggiuntivi VSTO e delle attività di programmazione correlate.|  
|[Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)|Viene fornita una panoramica del modello di programmazione delle personalizzazioni a livello di documento e delle attività di programmazione correlate.|  
|[Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)|Descrive i diversi modi in cui è possibile personalizzare l'interfaccia utente delle applicazioni di Office mediante componenti aggiuntivi VSTO e personalizzazioni a livello di documento.|  
|[Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)|Vengono descritti i diversi modi in cui è possibile usare i dati nelle soluzioni Office come, ad esempio, l'associazione dei dati ai controlli e la memorizzazione nella cache di dati in personalizzazioni a livello di documento.|  
|[Risoluzione dei problemi relativi alle soluzioni Office](../vsto/troubleshooting-office-solutions.md)|Vengono forniti suggerimenti per la risoluzione dei problemi comuni che possono verificarsi durante la creazione di soluzioni Office.|  
|[Supporto del threading in Office](../vsto/threading-support-in-office.md)|Viene fornita una panoramica dell'utilizzo di più thread nelle soluzioni Office.|  
|[Accessibilità nei progetti di Office](../vsto/accessibility-in-office-projects.md)|Vengono descritte le funzionalità di accessibilità disponibili nelle soluzioni Office.|  
  
## Vedere anche  
 [Procedura: Creare e modificare proprietà personalizzate di un documento](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Procedura: Leggere e scrivere nelle proprietà dei documenti](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Procedura: utilizzare l'interfaccia utente multilingue &#40;MUI&#41; di Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Procedura dettagliata: creazione di una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Procedura dettagliata: creazione di una personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  