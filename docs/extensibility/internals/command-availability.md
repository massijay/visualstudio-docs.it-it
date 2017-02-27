---
title: "Disponibilit&#224; dei comandi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contesto, comandi"
  - "voci di menu, i contesti di visibilità"
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# Disponibilit&#224; dei comandi
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il contesto di Visual Studio determina quali comandi sono disponibili. Il contesto può cambiare a seconda del progetto corrente, l'editor corrente, il package VS che vengono caricati e altri aspetti dell'ambiente di sviluppo integrato \(IDE\).  
  
## Contesti di comando  
 I contesti di comando seguenti sono le più comuni.  
  
-   **IDE** comandi forniti dall'IDE sono sempre disponibili.  
  
-   **VSPackage** VSPackage è possibile definire quando i comandi devono essere visualizzate o nascoste.  
  
-   **Progetto** progetto comandi vengono visualizzati solo per il progetto selezionato.  
  
-   **Editor** unico editor possono essere attive contemporaneamente. Sono disponibili comandi da editor attivo. Un editor lavora a stretto contatto con un servizio di linguaggio. Il servizio di linguaggio deve elaborare i comandi nel contesto dell'editor associato.  
  
-   **Tipo di file** un editor è possibile caricare più di un tipo di file. I comandi disponibili possono variare a seconda del tipo di file.  
  
-   **Finestra attiva** dell'ultima finestra di documento attivo imposta il contesto dell'interfaccia utente per i tasti di scelta rapida. Tuttavia, una finestra degli strumenti con una tabella di associazione di chiave che è simile al browser interno può anche impostare il contesto dell'interfaccia utente. Per finestre di documento più schede, ad esempio l'editor HTML, ogni scheda ha un contesto diverso comando GUID. Dopo la registrazione di una finestra degli strumenti, è sempre disponibile il **visualizzazione** menu.  
  
-   **Contesto dell'interfaccia utente** contesti dell'interfaccia utente vengono identificati dai valori della <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding> durante la compilazione, la soluzione o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging> quando il debugger è attivo. Più contesti dell'interfaccia utente possono essere attivi nello stesso momento.  
  
## Definizione di GUID di contesto personalizzato  
 Se un contesto di comando appropriato che GUID non è già stato definito, è possibile definire uno nel pacchetto Visual Studio e quindi programmare in modo che sia attivo o inattivo in base alle esigenze per controllare la visibilità dei comandi della.  
  
1.  Registrare i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metodo.  
  
2.  Ottenere lo stato di un GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo.  
  
3.  Attivare e disattivare i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metodo.  
  
    > [!CAUTION]
    >  Assicurarsi che il pacchetto Visual Studio non interferiscano con qualsiasi contesto esistente GUID perché altri package VS potrebbe dipendere da essi.  
  
## Vedere anche  
 [Selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md)   
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)