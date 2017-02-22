---
title: "Dettagli di configurazione di controllo di origine | Microsoft Docs"
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
  - "controllo del codice sorgente [Visual Studio SDK], i dettagli di configurazione"
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Dettagli di configurazione di controllo di origine
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Per implementare il controllo del codice sorgente, è necessario configurare correttamente il sistema del progetto o l'editor effettuare le operazioni seguenti:  
  
-   Autorizzazione di richiesta per la transizione allo stato modificato  
  
-   Autorizzazione di richiesta di salvare un file  
  
-   Richiedere l'autorizzazione per aggiungere, rimuovere, o rinominare i file del progetto  
  
## Autorizzazione di richiesta per la transizione allo stato modificato  
 Aggiungere i controlli all'elemento vuoto <xref:System.Windows.Controls.Grid> per compilare la pagina iniziale personalizzata.  Each editor that implements <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> must call <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> and receive approval to change the document from the environment before returning `True` for `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`.  Un progetto è essenzialmente un editor per un file di progetto e di conseguenza, ha la stessa responsabilità dell'implementazione dello modificare\-stato che tiene traccia del file di progetto come un editor di testo fare per i file.  L'handle di ambiente lo stato modificato della soluzione, ma di è necessario gestire lo stato modificato di qualsiasi oggetto riferimenti di soluzione ma non archiviano, ad esempio un file di progetto o i relativi elementi.  Generalmente se il progetto o l'editor è responsabile della gestione della persistenza per un elemento, pertanto è responsabile dell'implementazione di tenere traccia dello modificare\-stato.  
  
 In risposta alla chiamata di `IVsQueryEditQuerySave2::QueryEditFiles` , l'ambiente possibile effettuare le operazioni seguenti:  
  
-   Rifiutare la chiamata per cambiare in questo caso, l'editor o il progetto deve rimanere nello stato \(pulito\) invariato.  
  
-   Indicare che i dati del documento devono essere ricaricati.  per un progetto, l'ambiente ricaricherà i dati per il progetto.  Un editor deve ricaricare i dati dal disco tramite l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> .  In entrambi i casi, il contesto nel progetto o l'editor possibile modificare quando i dati vengono ricaricati.  
  
 È un complesso e un'attività difficile implementare le chiamate appropriate di `IVsQueryEditQuerySave2::QueryEditFiles` su una codebase esistente.  Di conseguenza, queste chiamate devono essere inserite durante la creazione del progetto o dell'editor.  
  
## Autorizzazione di richiesta di salvare un file  
 Before a project or editor saves a file, it must call <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> or <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>.  Per i file di progetto, le chiamate vengono automaticamente completato dalla soluzione, in grado quando salvare un file di progetto.  Gli editor sono responsabili di apportare queste chiamate a meno che l'implementazione dell'editor di `IVsPersistDocData2` utilizza l'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile\(Microsoft.VisualStudio.Shell.Interop.VSSAVEFLAGS, System.Object, System.String, System.String@, System.Int32@\) di funzione di supporto.  Se nell'editor implementa `IVsPersistDocData2` in questo modo, la chiamata a `IVsQueryEditQuerySave2::QuerySaveFile` o a `IVsQueryEditQuerySave2::QuerySaveFiles` viene eseguita automaticamente.  
  
> [!NOTE]
>  fare sempre queste chiamate di prelazione\-che è, in un momento in cui l'editor può ricevere un annullamento.  
  
## Richiedere l'autorizzazione per aggiungere, rimuovere, o rinominare i file del progetto  
 Prima che un progetto sia aggiungere, rinominare, o rimuovere un file o una directory, è necessario chiamare il metodo appropriato di `IVsTrackProjectDocuments2::OnQuery*` per richiedere l'autorizzazione dall'ambiente.  Se l'autorizzazione viene concessa, il progetto deve completare l'operazione e quindi chiamare il metodo appropriato di `IVsTrackProjectDocuments2::OnAfter*` per notificare all'ambiente che l'operazione viene completata.  Il progetto deve chiamare i metodi di interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> per tutti i file, ad esempio file speciali\) e non solo i file padre.  Le chiamate di file sono obbligatorie, ma le chiamate della directory sono facoltative.  Se il progetto include informazioni sulla directory, è opportuno chiamare i metodi appropriati di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> , ma se non dispone di queste informazioni, nell'ambiente a desumere le informazioni sulla directory.  
  
 Il progetto non devono chiamare metodi di `IVsTrackProjectDocuments2` al progetto aperti o adiacenti.  I listener che desiderano queste informazioni all'avvio possono restare l'evento di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> e scorrere la soluzione per trovare le informazioni necessari.  Chiusura, queste informazioni non sono necessarie.  `IVsTrackProjectDocuments2` fornito da <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Per ognuno aggiungere, modificare e rimuovere l'azione, esiste un metodo di `OnQuery*` e un metodo di `OnAfter*` .  Chiamare il metodo di `OnQuery*` per richiedere l'autorizzazione per aggiungere, rinominare, o rimuovere il file o la directory.  Chiamare il metodo di `OnAfter*` dopo che il file o la directory è stato aggiunto, rinominato, o rimosso stato e lo stato del progetto rifletta il nuovo stato.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Supporto di controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)