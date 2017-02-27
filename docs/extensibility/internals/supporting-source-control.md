---
title: "Supporto di controllo del codice sorgente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo [Visual Studio SDK], supporto di origine"
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Supporto di controllo del codice sorgente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta le estrazioni dei file, le registrazioni e altre operazioni di controllo del codice sorgente per il progetto o editor.  Come client del controllo del codice sorgente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è progettato per interagire con un pacchetto del controllo del codice sorgente, come [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], che fornisce l'archiviazione, controllo della versione e funzionalità di controllo per un set di file definito dinamicamente.  
  
## In questa sezione  
 [Modello per i pacchetti di controllo di origine](../../extensibility/internals/model-for-source-control-packages.md)  
 Vengono descritte le interfacce che un tipo di progetto deve implementare per supportare il controllo del codice sorgente.  
  
 [Decisioni di progettazione](../../extensibility/internals/source-control-design-decisions.md)  
 Fornisce le applicazioni per cui le risposte modificano come implementare un tipo di progetto.  
  
 [Dettagli di configurazione](../../extensibility/internals/source-control-configuration-details.md)  
 Viene descritto come supporta le modifiche al controllo del codice sorgente l'implementazione di un tipo di progetto.  
  
 [Indicazioni aggiuntive per progetti ed editor](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Vengono illustrate le procedure consigliate per i tipi e gli editor.  
  
 [Dettagli di runtime](../../extensibility/internals/source-control-runtime-details.md)  
 Viene descritto come registrare un progetto quando un utente lo aggiunge a un sistema di controllo del codice sorgente.  
  
## Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica al pacchetto del controllo del codice sorgente o un ambiente che un file sta per essere modificato in memoria o salvato.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Consente i progetti e le gerarchie la registrazione sul controllo del codice sorgente e ottenere informazioni sullo stato del controllo del codice sorgente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Distribuito in un sistema di progetto per fornire controllo del codice sorgente per i file di progetto e di elementi di progetto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Utilizzato dai progetti eseguire una query l'ambiente per autorizzazione l'aggiunta, la rimozione, o rinominare un file o una directory in una soluzione.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica ai client delle modifiche apportate ai file di progetto o directory.  
  
## Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti cenni preliminari sui progetti come blocchi predefiniti di base dell'ambiente di sviluppo integrato di \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Vengono forniti collegamenti ad argomenti supplementari che descrivono come compilazione del controllo di progetti e codice da compilare.