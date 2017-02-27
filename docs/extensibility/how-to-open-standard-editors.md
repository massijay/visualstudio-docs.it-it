---
title: "Procedura: aprire gli editor Standard | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], apertura"
  - "progetti [Visual Studio SDK], apertura degli editor standard"
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Procedura: aprire gli editor Standard
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si apre un editor standard, si lascia l'ide determinare un editor standard per un tipo di file selezionato, anziché specificare un editor specifico del progetto per il file.  
  
 completare la procedura riportata di seguito per implementare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> .  Verrà visualizzato un file di progetto nell'editor standard.  
  
### Per implementare il metodo di OpenItem con un editor standard  
  
1.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> \(`RDT_EditLock`\) per determinare se il file oggetto dati del documento è già aperto.  
  
2.  Se il file è già aperto, eseguire nuovamente la superficie del file chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> , specificando un valore di `IDO_ActivateIfOpen` per il parametro di `grfIDO` .  
  
     Se il file viene aperto e il documento è di proprietà da un progetto diverso dal progetto chiamante, il progetto riceve un messaggio che verrà aperto proviene da un altro progetto.  La finestra del file viene quindi sorta.  
  
3.  Se il documento non è aperto o non nella tabella in esecuzione di documento, chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> \(`OSE_ChooseBestStdEditor`\) per aprire un editor standard per il file.  
  
     Quando si chiama il metodo, l'ide esegue le attività seguenti:  
  
    1.  L'ide analizza la sottochiave degli editori {} guidEditorType \/Extensions nel Registro di sistema per determinare quale editor possibile aprire il file e ha la priorità più elevata a tale scopo.  
  
    2.  Dopo che l'ide ha determinato quale editor possibile aprire il file, l'ide chiama l'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance\(System.UInt32, System.String, System.String, Microsoft.VisualStudio.Shell.Interop.IVsHierarchy, System.UInt32, System.IntPtr, System.IntPtr@, System.IntPtr@, System.String@, System.Guid@, System.Int32@\).  L'implementazione dell'editor di questo metodo restituisce le informazioni che sono necessarie  l'ide di chiamare l'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow\(System.UInt32, System.String, Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy, System.UInt32, System.IntPtr, System.IntPtr, System.Guid@, System.String, System.Guid@, Microsoft.VisualStudio.OLE.Interop.IServiceProvider, System.String, System.String, System.Int32\[\], Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame@\) e posizionare l'oggetto documento appena aperto.  
  
    3.  Infine, l'ide carica il documento tramite l'interfaccia comune di persistenza, come <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Se l'ide ha precedentemente determinato che la gerarchia o l'elemento della gerarchia è disponibile, l'ide chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> nel progetto ottenere un puntatore di <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> di contesto a livello di progetto a passare nuovamente con la chiamata al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> .  
  
4.  Return an <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> pointer to the IDE when the IDE calls <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> on your project if you want to let the editor get context from your project.  
  
     Eseguire questo passaggio consente ai servizi aggiuntivi offrono di progetto all'editor.  
  
     Se la visualizzazione del documento o l'oggetto visualizzato del documento correttamente è stato collocato in una struttura della finestra, l'oggetto viene inizializzato con i dati chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: aprire gli editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: aprire gli editor di documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Visualizzazione di file utilizzando il comando Apri File](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)