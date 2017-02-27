---
title: "Iniziare a sviluppare estensioni di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Getting started, integrazione di Visual Studio"
  - "Visual Studio integration"
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Iniziare a sviluppare estensioni di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se non si è mai scritto un'estensione di Visual Studio prima, è probabile che alcune domande. È stato elencate alcune delle cause più comuni di seguito. Se le informazioni che si sta cercando non viene visualizzato, utilizzare i pulsanti \(**questa pagina è stata utile?** nella parte inferiore della schermata\) per chiedere a quello desiderato.  
  
## Il software necessario per lo sviluppo di estensioni di Visual Studio?  
 È necessario installare Visual Studio 2015 SDK oltre a Visual Studio 2015 per lo sviluppo di estensioni di Visual Studio.   È possibile installare Visual Studio 2015 SDK come parte del programma di installazione normale, o è possibile installarlo in un secondo momento. Per ulteriori informazioni sull'installazione di Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Tipi di elementi può fare con le estensioni di Visual Studio?  
 Il cielo 's il limite di quando è possibile immaginare di diverse estensioni di Visual Studio. Naturalmente, la maggior parte delle estensioni hanno a che fare con la scrittura di codice, ma che non deve necessariamente essere il caso. Di seguito sono riportati alcuni esempi dei tipi di estensioni che è possibile compilare:  
  
-   Supporto per lingue che non sono inclusi in Visual Studio, con supporto del compilatore ed eseguire il debug, IntelliSense e la colorazione della sintassi  
  
-   Strumenti di produttività che estendono le principali IDE esperienza con altri modelli, finestre di dialogo codice refactoring, nuovo o finestre degli strumenti  
  
-   Finestre di progettazione specifico di dominio per gli scenari come il supporto di progettazione o area dati  
  
 Per esempi di estensioni, consultare la [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/). È anche possibile esaminare [Visual Studio aprire origine estensioni](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).  
  
## Le funzionalità di Visual Studio è possibile estendere?  
 In teoria, è possibile estendere praticamente qualsiasi parte di Visual Studio: menu, barre degli strumenti, comandi, windows, soluzioni, progetti, gli editor e così via.  
  
 In pratica, si è constatato che le funzionalità da estendere la maggior parte delle persone sono comandi, menu e barre degli strumenti, windows, IntelliSense e progetti. Di seguito sono forniti collegamenti a sezioni pertinenti:  
  
-   [Estensione menu e comandi](../extensibility/extending-menus-and-commands.md): aggiungere elementi personalizzati a Visual Studio menu e barre degli strumenti. È possibile utilizzare tali avviare nuove funzionalità di Visual Studio o le proprie applicazioni di supporto esterna. È anche possibile fornire collegamenti personalizzati per voci di menu.  
  
-   [Estensione e personalizzazione di finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md): estendere finestre degli strumenti esistenti o creare finestre degli strumenti. Ad esempio, è possibile aggiungere nuove proprietà per il **proprietà**, oppure è possibile creare una nuova finestra degli strumenti per aggiungere ulteriori funzionalità.  
  
-   [Editor e le estensioni del servizio di linguaggio](../extensibility/editor-and-language-service-extensions.md): aggiungere le proprie personalizzazioni gli elementi IntelliSense forniti per i linguaggi di Visual Studio o creare il supporto per nuovi linguaggi di programmazione. È possibile creare nuovi completamento delle istruzioni, suggerimenti e le descrizioni comandi informazioni rapide di nuovo. Con le lampadine, è possibile aggiungere suggerimenti refactoring e correzioni di codice per supportare nuovi linguaggi di programmazione.  
  
-   [Estensione di progetti](../extensibility/extending-projects.md)  
  
-   [Opzioni e impostazioni utente estensione](../extensibility/extending-user-settings-and-options.md)  
  
-   [Estensione di proprietà e la finestra proprietà](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio isolato Shell](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> I modelli di progetto forniti da VSSDK?  
 I due tipi principali di estensioni sono estensioni VSPackage e MEF. In generale, le estensioni VSPackage vengono utilizzate per le estensioni che utilizzano o estendono i comandi, finestre degli strumenti e progetti. Estensioni MEF sono utilizzate per estendere o personalizzare l'editor di Visual Studio.  
  
 Per le estensioni di Visual c\# e Visual Basic, VSSDK fornisce un modello di progetto VSIX vuoto che è possibile utilizzare insieme i nuovi modelli di elemento che creano i comandi di menu, finestre degli strumenti e le estensioni dell'editor. Per altre informazioni, vedere [Novità di Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md). È inoltre possibile utilizzare questo modello per i modelli di progetto del pacchetto, frammenti di codice e altri elementi per la distribuzione ad altri utenti.  
  
 Per C\+\+, la procedura guidata VSPackage fornisce il codice per aggiungere i comandi di menu e finestre degli strumenti editor personalizzati.  
  
 Il modello della Shell isolata viene utilizzato per un'estensione in una shell di Visual Studio che è possibile personalizzare e distribuire la versione del pacchetto. Gli argomenti seguenti viene illustrato come iniziare a utilizzare ogni tipo di estensione:  
  
-   Comandi di menu: [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Finestre degli strumenti: [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Estensioni dell'editor: [Creazione di un'estensione con un modello di elemento di Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Package VS base: [Creazione di un'estensione con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Modello di progetto VSIX: [Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio isolato shell: [Procedura dettagliata: Creazione di un'applicazione di base Shell isolata](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## Come? my extension simile a Visual Studio  
 Ottenere suggerimenti per la progettazione dell'interfaccia utente per l'estensione in [Linee guida sull'esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## Dove è possibile trovare esempi di codice VSSDK?  
 Ciascuno dei collegamenti elencati nella sezione precedente sono dettagliate che illustrano come implementare le funzionalità specifiche. È anche possibile trovare Apri origine esempi VSSDK in GitHub all'indirizzo [esempi di Visual Studio](https://aka.ms/vs2015sdksamples).  
  
## Come è possibile distribuire l'estensione?  
 È possibile installare l'estensione in un altro computer o inviarlo ai tuoi amici come file con estensione VSIX, che si installa facendovi doppio clic. È possibile trovare ulteriori informazioni sui pacchetti VSIX presso [Distribuzione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 È anche possibile pubblicare l'estensione in Visual Studio Gallery, che rende visibile a un numero elevato di clienti di Visual Studio. Per un esempio di creazione del pacchetto un'estensione per la raccolta, vedere [Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Per ulteriori informazioni sui requisiti necessari per pubblicare nella raccolta, vedere [prodotti ed estensioni per Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).