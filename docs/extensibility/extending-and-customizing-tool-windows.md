---
title: "Estensione e personalizzazione di finestre degli strumenti | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfacce utente, essentials"
  - "finestre degli strumenti standard"
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Estensione e personalizzazione di finestre degli strumenti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio fornisce diversi tipi di windows, ad esempio le finestre degli strumenti, finestre di documento e le finestre di dialogo. Altre finestre, ad esempio la finestra Proprietà, la finestra di Output e la finestra Elenco attività, sono tipi di finestre degli strumenti.  
  
## Finestre degli strumenti  
 Le finestre di Visual Studio sono generalmente di sola lettura windows che non sono basate su file. In questo differiscono dalle finestre di documento, quale visualizzare i file in modalità lettura\-scrittura. Il **della casella degli strumenti**, **Esplora**, **proprietà** finestra e **Browser Web** sono esempi di finestre degli strumenti.  
  
 Per scoprire come creare una finestra degli strumenti semplici, vedere [Aggiunta di una finestra degli strumenti](../extensibility/adding-a-tool-window.md).  
  
 Per registrare una finestra degli strumenti di Visual Studio, vedere [Registrazione di una finestra degli strumenti](../extensibility/registering-a-tool-window.md).  
  
 Finestre degli strumenti sono a istanza singola per impostazione predefinita, vale a dire che solo un'istanza della finestra degli strumenti è possibile aprire contemporaneamente. Dopo l'apertura di una finestra degli strumenti a istanza singola, rimane aperto finché non si chiude l'IDE. Quando si chiude una finestra degli strumenti a istanza singola, viene modificata solo la visibilità. È possibile anche creare più istanze finestre degli strumenti, in modo che più istanze della finestra sono possibile aprire contemporaneamente. Per altre informazioni, vedere [Creazione di una finestra degli strumenti multi\-istanza](../extensibility/creating-a-multi-instance-tool-window.md).  
  
 Finestre degli strumenti possono essere *dinamica*, vale a dire che sono visibili, ogni volta che si applica al contesto dell'interfaccia utente correlato. L'utilizzo della visibilità automatico può ridurre la necessità di windows nell'IDE. Per altre informazioni, vedere [Aprire una finestra degli strumenti dinamica](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Finestre degli strumenti possono essere ancorata, mobile o a schede nella cornice del documento. La cornice della finestra dello strumento viene fornita dall'IDE e viene utilizzata per controllare le dimensioni, posizione, stato e altre proprietà persistente. Riquadro della finestra dello strumento consente di visualizzare il contenuto. Le dimensioni e posizione predefinite si applicano solo quando la finestra degli strumenti è aperto; Dopo che viene mantenuto lo stato della finestra dello strumento.  
  
 Riquadri della finestra dello strumento è possono ospitare i controlli utente WPF e supportare le barre degli strumenti. È possibile eseguire l'override di <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> per restituire l'handle del controllo ospitato.  
  
 È possibile aggiungere più funzionalità diverse per le finestre degli strumenti. Ad esempio, è possibile aggiungere una barra degli strumenti: [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) o un menu di scelta rapida: [Aggiunta di un Menu di scelta rapida in una finestra degli strumenti](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). È possibile aggiungere un controllo di ricerca che consente di cercare gli elementi all'interno di finestre: [Aggiunta di ricerca a una finestra degli strumenti](../extensibility/adding-search-to-a-tool-window.md).  
  
 È possibile sottoscrivere eventi finestra dello strumento: [Sottoscrizione a un evento](../extensibility/subscribing-to-an-event.md).  
  
## Estensione di finestre degli strumenti esistenti  
 È possibile aggiungere informazioni sulla finestra degli strumenti in un nuovo **Opzioni** pagina e una nuova impostazione nel **proprietà** pagina, scrivere il **elenco attività** e **Output** windows. Per altre informazioni, vedere [Estensione di proprietà, elenco attività, Output e le finestre di opzioni](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) e [Estensione di proprietà, elenco attività, Output e le finestre di opzioni](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## Finestre di dialogo modale  
 In un'estensione di Visual Studio è necessario creare finestre di dialogo modale tramite la derivazione da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, che consente di controllare queste e il resto dell'interfaccia utente. Per ulteriori informazioni, vedere.[Creazione e gestione di finestre di dialogo modale](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## Vedere anche  
 [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)