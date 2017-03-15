---
title: "Visual Studio Shell | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "shell, Visual Studio"
  - "Visual Studio shell"
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Visual Studio Shell
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell è l'agente principale di integrazione in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. La shell fornisce la funzionalità necessaria per abilitare i package VS condividere i servizi comuni. Poiché l'obiettivo dell'architettura di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consiste nell'assegnazione funzionalità principale in VS, la shell è un framework per fornire funzionalità di base e supportare la comunicazione incrociata tra il componente del package VS.  
  
## Responsabilità della shell  
 La shell ha le responsabilità principali seguenti:  
  
-   Supporto \(tramite le interfacce COM\) elementi di base dell'interfaccia utente \(UI\). Questi includono predefinito menu e barre degli strumenti, le cornici della finestra di documento o finestre figlio di interfaccia a documenti multipli \(MDI\) e le cornici della finestra dello strumento e il supporto di ancoraggio.  
  
-   Gestire un elenco di tutti i documenti aperti in una tabella di documento \(RDT\) in esecuzione per coordinare la persistenza dei documenti e per garantire che di un documento non può essere aperto in più modo o in modalità compatibile.  
  
-   Che supporta l'interfaccia di routing di comandi e la gestione dei comandi, `IOleCommandTarget`.  
  
-   Caricamento VS in momenti appropriati. Caricamento ritardato un VSPackage è necessario per migliorare le prestazioni della shell.  
  
-   Gestione di determinati servizi, condivisi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, che fornisce funzionalità di base della shell, e <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, che fornisce le funzionalità di base di windowing.  
  
-   Gestione dei file di soluzione \(sln\). Le soluzioni contengono gruppi di progetti correlati, simili ai file dell'area di lavoro \(DSW\) in Visual C\+\+ 6.0.  
  
-   Selezione di shell a livello di rilevamento, il contesto e valuta. La shell registra i seguenti tipi di elementi:  
  
    -   Il progetto corrente  
  
    -   L'elemento del progetto corrente o l'ID elemento corrente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   La selezione corrente per il **proprietà** finestra o `SelectionContainer`  
  
    -   Contesto dell'interfaccia utente, ID o CmdUIGuids che controllano la visibilità dei comandi, menu e barre degli strumenti  
  
    -   Gli elementi attualmente attivi, ad esempio la finestra attiva, documento e gestore di annullamento  
  
    -   Gli attributi di contesto dell'utente che determinano la Guida dinamica  
  
 La shell di Media anche la comunicazione tra i package VS installati e i servizi correnti. Supporta le funzionalità di base della shell e li rende disponibili per i package VS integrato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Queste funzionalità di base includono i seguenti elementi:  
  
-   **Su** schermata iniziale e casella di dialogo  
  
-   **Aggiungi elemento esistente e aggiungere nuovi** le finestre di dialogo  
  
-   **Visualizzazione classi** finestra e **Visualizzatore oggetti**  
  
-   **Riferimenti** la finestra di dialogo  
  
-   **Struttura documento** finestra  
  
-   **Guida dinamica** finestra  
  
-   **Trovare** e **sostituire**  
  
-   **Apri progetto** e **Apri** delle finestre di dialogo nel **New** menu  
  
-   **Opzioni** della finestra di dialogo di **strumenti** menu  
  
-   **Proprietà** finestra  
  
-   **Esplora soluzioni**  
  
-   **Elenco attività** finestra  
  
-   **Casella degli strumenti**  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Package VS](../../extensibility/internals/vspackages.md)