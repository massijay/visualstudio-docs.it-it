---
title: "Panoramica dello sviluppo di soluzioni Office (VSTO)"
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
  - "assembly di interoperabilità primari, Office"
  - "sviluppo per Office in Visual Studio, informazioni sullo sviluppo di soluzioni"
ms.assetid: 5dfc519f-a851-4661-8d2b-47e0d221e10e
caps.latest.revision: 69
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 68
---
# Panoramica dello sviluppo di soluzioni Office (VSTO)
  Utilizzando Microsoft Office come front\-end per soluzioni, è possibile sfruttare i classici strumenti e interfacce utente di Microsoft Office, quali le funzionalità di elaborazione di testo, di analisi dei dati di Excel e di gestione della posta elettronica di Outlook. È possibile sviluppare soluzioni in Visual Studio per personalizzare le applicazioni di Office e aggiungere le funzionalità specifiche necessarie per i processi aziendali. Ad esempio, è possibile trasformare Word in un generatore di contratti che assembla contratti da parti preesistenti che possono essere rese modificabili o meno. Excel consente di creare un foglio di lavoro automatizzato relativo al budget, personalizzato per progetti diversi. Gli utenti possono inoltre usare soluzioni Office offline che rendono le soluzioni complesse più pratiche di quanto sarebbero se si utilizzasse un'architettura basata su Web.  
  
 In questo argomento viene fornita una panoramica dei tipi di soluzioni Office che è possibile creare tramite i modelli di Visual Studio Tools per Office \(VSTO\) disponibili negli strumenti di sviluppo di Office in Visual Studio. Per informazioni generali sullo sviluppo con Office, vedere [Office Developer Center](https://dev.office.com/).  
  
## Scelta di un tipo di progetto di Office  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornisce i seguenti tipi di modelli di progetto per lo sviluppo di Office basato su VSTO:  
  
-   Le **personalizzazioni a livello di documento** sono associate a un documento specifico.  
  
-   I **VSTO Add\-ins** sono associati all'applicazione stessa.  
  
 Per decidere quale di questi tipi di progetto è ottimale per la soluzione, è necessario stabilire se si desidera che il codice venga eseguito solo quando un documento specifico è aperto o che invece sia disponibile ogni volta che l'applicazione è in esecuzione. Per altre informazioni sui modelli di progetto, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
 I tipi di progetti che è possibile creare dipendono dalle applicazioni di Office installate nel computer di sviluppo. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### Personalizzazioni a livello di documento  
 Le personalizzazioni a livello di documento sono costituite da un assembly associato a un singolo documento, a una cartella di lavoro o a un modello di Microsoft Office Word o Microsoft Office Excel. L'assembly viene caricato quando viene aperto il documento associato. Le funzionalità delle personalizzazioni create sono disponibili solo quando il documento associato viene aperto. Le personalizzazioni non possono apportare modifiche a livello di applicazione come, ad esempio, la visualizzazione di una nuova voce di menu o della scheda della barra multifunzione quando un documento è aperto.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include strumenti che consentono di creare personalizzazioni a livello di documento. Il documento personalizzato è ospitato come area di progettazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], che consente di progettare il documento trascinando e rilasciando controlli su di esso. Molte altre funzionalità di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono disponibili nei progetti a livello di documento, ad esempio controlli Windows Form, associazione dati mediante trascinamento e un debugger integrato.  
  
 Per altre informazioni sulle personalizzazioni, vedere i seguenti argomenti:  
  
-   [Guida introduttiva alla programmazione di personalizzazioni a livello di documento per Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)  
  
-   [Guida introduttiva alla programmazione delle personalizzazioni a livello di documento per Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)  
  
-   [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)  
  
### Componenti aggiuntivi VSTO  
 I componenti aggiuntivi VSTO sono costituiti da un assembly associato a un'applicazione di Microsoft Office. In genere, il componente aggiuntivo VSTO viene eseguito quando si avvia l'applicazione associata. Gli utenti possono caricare componenti aggiuntivi VSTO anche quando l'applicazione è già in esecuzione. Le funzionalità dei componenti aggiuntivi VSTO creati dall'utente sono disponibili per l'applicazione stessa, indipendentemente dai documenti aperti.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include strumenti che permettono di creare componenti aggiuntivi VSTO. I progetti di componente aggiuntivo includono una classe generata automaticamente che rappresenta il componente aggiuntivo VSTO. Questa classe fornisce proprietà ed eventi che è possibile usare per accedere al modello a oggetti dell'applicazione host ed eseguire codice quando il componente aggiuntivo VSTO viene caricato e arrestato. Nei progetti di componente aggiuntivo VSTO sono disponibili molte altre funzionalità di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], tra cui Windows Form e un debugger integrato.  
  
 Per altre informazioni sui componenti aggiuntivi VSTO, vedere gli argomenti seguenti:  
  
-   [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
## Automatizzare applicazioni di Office tramite assembly di interoperabilità primari  
 A livello di codice, è possibile incorporare le funzionalità di un'applicazione di Office nella soluzione scrivendo codice che accede al modello a oggetti dell'applicazione. I modelli a oggetti sono disposizioni di classi che espongono funzionalità tramite alcuni metodi e proprietà. Il modello a oggetti di ogni applicazione di Office è diverso.  
  
 Per usare il modello a oggetti di un'applicazione di Office da una soluzione creata mediante gli strumenti di sviluppo di Office in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], è necessario usare l'assembly di interoperabilità primario dell'applicazione. L'assembly di interoperabilità primario consente l'interazione tra il codice gestito e il modello a oggetti basato su COM di un'applicazione di Microsoft Office.  
  
 Per eseguire la maggior parte delle attività di sviluppo, gli assembly di interoperabilità primari di Office devono essere installati e registrati nella Global Assembly Cache del computer di sviluppo. Per altre informazioni, vedere [Configurazione di un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Gli assembly di interoperabilità primari di Office non sono richiesti per l'esecuzione di soluzioni VSTO per Office nei computer degli utenti finali. Per altre informazioni, vedere [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Per altre informazioni sull'utilizzo di assembly di interoperabilità primari in soluzioni VSTO per Office, vedere gli argomenti seguenti:  
  
-   [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)  
  
-   [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)  
  
## Esecuzione di soluzioni VSTO per Microsoft Office nei computer dell'utente finale  
 Quando si crea una soluzione VSTO per Office, tenere in considerazione il modo in cui i requisiti di distribuzione potrebbero influire sulle scelte di sviluppo.  
  
### Opzioni di distribuzione  
 Usare ClickOnce o Windows Installer per distribuire soluzioni create mediante gli strumenti di sviluppo di Office in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. La distribuzione ClickOnce consente di creare soluzioni con aggiornamento automatico che possono essere installate ed eseguite in modalità parzialmente automatica. I file di Windows Installer \(.msi\) possono essere facilmente distribuiti ai computer degli utenti finali o distribuiti tramite Systems Management Server \(SMS\). Per altre informazioni sulla distribuzione di soluzioni VSTO per Office, vedere [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
### Installazione dei prerequisiti  
 Prima che gli utenti finali possano eseguire una soluzione creata usando gli strumenti di sviluppo di Office in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], i rispettivi computer devono disporre di determinati prerequisiti. Se si distribuisce la soluzione tramite ClickOnce o creando un file Windows Installer, questi prerequisiti possono essere installati con la soluzione. Per altre informazioni, vedere [Prerequisiti per la distribuzione delle soluzioni Office](http://msdn.microsoft.com/it-it/9f672809-43a3-40a1-9057-397ce3b5126e) e [Procedura: Installare i prerequisiti nei computer degli utenti finali per l'esecuzione delle soluzioni Office](http://msdn.microsoft.com/it-it/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
### Sicurezza  
 La sicurezza per le soluzioni VSTO per Office viene garantita da una serie di controlli di sicurezza che [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] effettua quando installa e carica la soluzione. Questi controlli consentono di verificare se il percorso del manifesto di distribuzione è attendibile o se il certificato usato per firmare il manifesto della distribuzione è attendibile. Per altre informazioni, vedere [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md).  
  
## Vedere anche  
 [Guida introduttiva &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Guida introduttiva alla programmazione di personalizzazioni a livello di documento per Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Guida introduttiva alla programmazione delle personalizzazioni a livello di documento per Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  