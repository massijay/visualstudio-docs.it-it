---
title: "Visualizzazione di file utilizzando l&#39;aperto con il comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipi di progetto, supporto comando Apri con"
  - "Comando Apri con"
  - "persistenza, supporto comando Apri con"
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Visualizzazione di file utilizzando l&#39;aperto con il comando
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un progetto può chiedere all'IDE per visualizzare la finestra di dialogo di **Apri con** .  Questa richiesta richiesto all'utente di aprire un file contenente una selezione degli editor standard.  Nei passaggi seguenti viene descritto il processo.  
  
1.  Il progetto chiama l'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor\(System.UInt32, System.String, System.Guid@, System.String, Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy, System.UInt32, System.IntPtr, Microsoft.VisualStudio.OLE.Interop.IServiceProvider, Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame@\), specificando un valore di OSE\_UseOpenWithDialog  il parametro di `OSEOpenDocEditor` .  
  
2.  In base all'estensione di file di documento, l'ide determina quale editor elencati nel Registro Di Sistema può aprire il documento specificato e visualizzare tali informazioni nella finestra di dialogo di **Apri con** .  
  
    > [!NOTE]
    >  I progetti con un editor intrinseco che deve essere incluso nella finestra di dialogo di **Apri con** deve registrare una factory dell'editor per ciascuna editor.  Gli editor intrinseci funzionano solo con un particolare tipo di progetto, applicata nell'implementazione del metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .  L'ide ha una factory incorporata dell'editor per l'editor di testo principale e l'editor binario.  L'ide viene inoltre creata un'istanza di una factory dell'editor per conto di ogni associazione registrata file di Windows.  Un esempio di tale file è Microsoft Word.  
  
3.  Non appena l'utente seleziona un elemento dalla finestra di dialogo di **Apri con** , l'ide quindi aprire il documento con il metodo chiamante di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  Per ulteriori informazioni, vedere [Procedura: aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md).  
  
## Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Visualizzazione di file utilizzando il comando Apri File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Procedura: aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md)