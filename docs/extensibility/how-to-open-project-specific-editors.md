---
title: "Procedura: aprire gli editor specifici del progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipi di progetto, aprire un editor di progetto specifici"
  - "editor [Visual Studio SDK], apertura degli editor specifici del progetto"
  - "progetti [Visual Studio SDK], aprire le cartelle"
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Procedura: aprire gli editor specifici del progetto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se un file dell'elemento aperto da un progetto è associato intrinsecamente all'editor particolare per tale progetto, il progetto deve aprire il file utilizzando un editor specifico del progetto.  Il file non può essere delegato giù il meccanismo dell'IDE per selezionare un editor.  Ad esempio, anziché utilizzare un editor di immagini bitmap standard, è possibile utilizzare questa opzione progetto\-specifica dell'editor specificare un editor di immagini bitmap specifico che riconosce le informazioni nel file univoco al progetto.  
  
 L'ide chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> quando determina che un file deve essere aperto da un progetto specifico.  Per ulteriori informazioni, vedere [Visualizzazione di file utilizzando il comando Apri File](../extensibility/internals/displaying-files-by-using-the-open-file-command.md).  Utilizzare le seguenti linee guida per l'implementazione del metodo di `OpenItem` per disporre il progetto aprire un file utilizzando un editor specifico del progetto.  
  
### Per implementare il metodo di OpenItem con un editor specifico del progetto  
  
1.  Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> \(RDT\_EditLock\) per determinare se il file \(oggetto dati di documento\) è già aperto.  
  
    > [!NOTE]
    >  Per ulteriori informazioni sui dati del documento e gli oggetti visualizzazione del documento, vedere [Dati del documento e visualizzazione di documento nell'editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Se il file non è aperto, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> per eseguire una query su ogni progetto determinare quale progetto possibile aprire il file.  
  
     Se il file viene aperto e il documento è di proprietà da un progetto diverso dal progetto chiamante, verrà visualizzato un avviso all'utente che verrà aperto proviene da un altro progetto.  La finestra del file viene quindi sorta.  
  
3.  Se il buffer di testo \(oggetto dati di documento\) è già aperto e si desidera associare un'altra visualizzazione a, il responsabile del collegamento di tale visualizzazione.  Si consiglia di creare un'istanza di una visualizzazione \(oggetto visualizzazione di documento\) dal progetto, è la seguente:  
  
    1.  Chiamata `QueryService` sul servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> per ottenere un puntatore a un'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> .  
  
    2.  Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> per creare un'istanza della classe di visualizzazione del documento.  
  
4.  Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> , specificando l'oggetto visualizzato del documento.  
  
     Questo metodo ospita l'oggetto visualizzato del documento in una finestra del documento.  
  
5.  Eseguire chiamate appropriate per <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> o metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> .  
  
     In questa fase, la visualizzazione completamente deve essere inizializzata e pronto per essere aperte.  
  
6.  Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> per visualizzare e aprire la visualizzazione.  
  
## Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: aprire gli editor Standard](../extensibility/how-to-open-standard-editors.md)   
 [Procedura: aprire gli editor di documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)