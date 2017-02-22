---
title: "Persistenza del progetto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistenza, progetti"
  - "persistenza di progetti [Visual Studio SDK]"
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Persistenza del progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La persistenza rappresenta un aspetto principale di progettazione per il progetto.  La maggior parte degli elementi di progetto di utilizzo di progetti che rappresentano i file; di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta i progetti anche dei cui dati vengono non based file.  I file delle proprietà dal progetto e dal file di progetto devono essere resi persistenti.  L'ide indica al progetto stesso o un elemento di progetto.  
  
 Modelli per i progetti vengono passati alla factory del progetto.  I modelli devono supportare l'inizializzazione di tutti gli elementi di progetto a seconda dei requisiti del tipo di progetto specifico.  Questi modelli possono successivamente essere salvati come file di progetto e gestiti dall'IDE nella soluzione.  Per ulteriori informazioni, vedere [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) e [Soluzioni](../../extensibility/internals/solutions.md).  
  
 Gli elementi di progetto possono essere basati su file o non based file:  
  
-   gli elementi basati su file possono essere locali o remoti.  Nei progetti Web in c\#, ad esempio, le connessioni ai file in un sistema remoto vengono mantenuti in locale, mentre i file stessi vengono mantenuti nel sistema remoto.  
  
-   a elementi Non based file possono salvare gli elementi in un database o in un repository.  
  
## modelli di commit  
 Dopo la decisione in cui gli elementi di progetto vengono individuati, è necessario scegliere il modello appropriato di commit.  Ad esempio, in un modello basato su file con i file locali, ogni progetto può essere salvato autonomamente.  In un modello di repository, è possibile salvare diversi elementi in una transazione.  Per ulteriori informazioni, vedere [Decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
 Per determinare le estensioni di file, progetti implementano l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> , che fornisce informazioni del client di un oggetto per implementare la finestra di dialogo di **Salva con nome** casella\-che è, compilati nell'elenco a discesa di **Salva con nome tipo** e gestire l'estensione di file iniziale.  
  
 L'IDE chiama il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>.  Di conseguenza, l'oggetto possiede tutti gli aspetti del file e il formato.  Ciò include il nome del formato dell'oggetto.  
  
 Nel caso in cui gli elementi non sono file, `IPersistFileFormat` è ancora come a elementi non based file vengono salvati in modo permanente.  I file di progetto, ad esempio file di VBP per i progetti [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o i file di vcproj per i progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , devono essere mantenuti.  
  
 Per le operazioni di salvataggio, l'ide esamina la tabella in esecuzione il documento \(RDT\) e la gerarchia passa i controlli a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> e interfacce di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> .  Il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> viene implementato per determinare se l'elemento è stato modificato.  Se l'elemento è, il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> viene implementato per salvare l'elemento modificato.  
  
 I metodi e di `IVsPersistHierarchyItem2` vengono utilizzati per determinare se un elemento può essere ricaricatoe e, se l'elemento può essere, ad ricaricarlo.  Inoltre, il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> può essere implementato per riordinare gli elementi modificati per essere eliminata senza essere salvato.  
  
## Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)