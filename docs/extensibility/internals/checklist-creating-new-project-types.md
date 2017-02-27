---
title: "Elenco di controllo: Creazione di nuovi tipi di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creazione di nuovi tipi di progetti [Visual Studio SDK]"
  - "elenco di controllo per la creazione di tipi di progetto"
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Elenco di controllo: Creazione di nuovi tipi di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È necessario completare diverse attività per creare un nuovo tipo di progetto. Il seguente elenco fornisce una Guida alle attività.  
  
1.  Progettare la funzionalità per il nuovo tipo di progetto. Per altre informazioni, vedere [Decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Determinare quale editor vengono utilizzati per codice e altri elementi del progetto. È possibile utilizzare l'editor standard o core oppure è possibile creare e utilizzare gli editor specifici del progetto. Per altre informazioni, vedere [Creazione di finestre di progettazione ed editor personalizzati](../../extensibility/creating-custom-editors-and-designers.md) e [Procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Determinare il livello di partecipazione saranno presenti gli elementi del progetto di **Visualizzazione classi** e **Visualizzatore oggetti**. Per altre informazioni, vedere [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Derivare nuove classi in base alle decisioni di progettazione effettuate in precedenza per il progetto e gli elementi di progetto.  
  
5.  Scrivere il codice per i componenti di tipo di progetto seguenti:  
  
    -   Factory del progetto, per gestire la creazione di nuovi progetti e aprire progetti esistenti. Per altre informazioni, vedere [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Gerarchia del progetto e la gestione dei comandi. Per ulteriori informazioni, vedere [non incluso nella compilazione: utilizzo di classi di progetto HierUtil7 per implementare un tipo di progetto \(C\+\+\)](http://msdn.microsoft.com/it-it/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md), [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md) e [Confronto tra oggetti MenuCommand e OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Gestione elementi di progetto, inclusa l'aggiunta del progetto per il **Nuovo progetto** la finestra di dialogo. Per altre informazioni, vedere [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md) e [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistenza dello stato di progetto e i singoli elementi. Per altre informazioni, vedere [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md). Per la persistenza di informazioni sulla soluzione, vedere [Soluzioni](../../extensibility/internals/solutions.md).  
  
    -   Proprietà indipendenti di configurazione da visualizzare nella finestra Proprietà. Per altre informazioni, vedere [Estensione delle proprietà](../../extensibility/internals/extending-properties.md).  
  
    -   Proprietà di configurazione del progetto come implementato nelle pagine delle proprietà per visualizzare le proprietà dipendenti dalla configurazione. Per altre informazioni, vedere [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Enumerazione di output per la distribuzione. Per altre informazioni, vedere [Configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Servizi di avvio del progetto. Per altre informazioni, vedere [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md) e [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).  
  
    -   Gli oggetti o le classi derivate da `IDispatch`, disponibile per l'automazione.  
  
    -   File XML comando tabella \(vsct\). Per altre informazioni, vedere [Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Test, eseguire il debug e avviare il tipo di progetto.  
  
7.  Visualizzare il progetto nel **progetto** scheda della finestra di **Aggiungi riferimento** la finestra di dialogo impostando `VARIANT_TRUE` come valore per `VSHPROPID_ShowProjInSolutionPage`. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Creare il file di Microsoft Installer \(MSI\) per l'installazione del package VS. Per altre informazioni, vedere [L'installazione di VS con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Registrazione di un tipo di progetto](../../extensibility/internals/registering-a-project-type.md) e [Package VS](../../extensibility/internals/vspackages.md).  
  
## Vedere anche  
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)