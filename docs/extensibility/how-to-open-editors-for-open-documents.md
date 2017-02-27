---
title: "Procedura: aprire gli editor di documenti aperti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], apertura di documenti aperti"
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Procedura: aprire gli editor di documenti aperti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Prima di un progetto apra una finestra del documento, il progetto innanzitutto necessario determinare se il file è già aperto nella finestra del documento per un altro editor.  Il file può essere aperto in un editor specifico del progetto, o in uno degli editor standard registrati con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Aprire un editor specifico del progetto  
 Utilizzare la procedura riportata di seguito per aprire un editor specifico del progetto per un file già aperto.  
  
#### Per aprire un editor specifico del progetto per un file aperto  
  
1.  Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  
  
     Questo puntatori dei risultati della chiamata alla gerarchia del documento, all'elemento della gerarchia e alla struttura della finestra, se necessario.  
  
2.  Se il documento è aperto, il progetto deve verificare se un solo oggetto dati del documento esista, o se un oggetto visualizzazione del documento è presente anche.  
  
    -   Se un oggetto visualizzazione del documento esistente e questa visualizzazione è per una gerarchia o un elemento differente della gerarchia, il progetto viene utilizzato il puntatore alla struttura della finestra di visualizzazione per eseguire nuovamente la finestra esistente.  
  
    -   Se un oggetto visualizzazione del documento esistente e questa visualizzazione è per la stessa gerarchia e elemento della gerarchia, il progetto può aprire una seconda visualizzazione se possibile associare all'oggetto dati sottostante del documento.  In caso contrario, il progetto deve utilizzare il puntatore alla struttura della finestra di visualizzazione per eseguire nuovamente la finestra esistente.  
  
    -   Se solo l'oggetto dati del documento presente, il progetto deve determinare se possibile utilizzare l'oggetto dati del documento per la visualizzazione corrispondente.  Se l'oggetto dati del documento è compatibile, completare i passaggi illustrati in [Aprire un editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).  
  
     Se l'oggetto dati del documento non è compatibile, un errore dovrebbe essere visualizzato all'utente che indica che il file è attualmente in uso.  Questo errore può essere visualizzato solo in casi temporanei, ad esempio quando un file viene compilato contemporaneamente l'utente sta tentando di aprire il file utilizzando un editor diverso da quello dell'editor di testo di base di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  L'editor di testo principale possibile condividere l'oggetto dati del documento con il compilatore.  
  
3.  Se il documento non è aperto in quanto non esiste un oggetto dati del documento o oggetto visualizzazione del documento, completare i passaggi in [Aprire un editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).  
  
## aprire un editor standard  
 Utilizzare la procedura riportata di seguito per aprire un editor standard per un file già aperto.  
  
#### Per aprire un editor standard per un file aperto  
  
1.  Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Questo metodo verifica innanzitutto si verifica che il documento non sia già aperto dall'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen\(Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy, System.UInt32, System.String, System.Guid@, System.UInt32 Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy@, System.UInt32\[\], Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame@, System.Int32@\) chiamante.  Se il documento è già aperto, la relativa finestra dell'editor viene rieseguita la superficie di.  
  
2.  Se il documento non è aperto, quindi completare i passaggi in [Procedura: aprire gli editor Standard](../extensibility/how-to-open-standard-editors.md).  
  
## Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: aprire gli editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: aprire gli editor Standard](../extensibility/how-to-open-standard-editors.md)