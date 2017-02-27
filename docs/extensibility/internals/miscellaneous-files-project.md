---
title: "Progetto di file esterni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "file, aggiunta di file esistenti alle soluzioni"
  - "Progetto di file esterni"
  - "Cartella elementi di soluzione"
  - "file, aprire il progetto di file esterni"
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Progetto di file esterni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando un utente apre gli elementi di progetto, assegnazione al progetto file esterni tutti gli elementi che non sono membri di alcuni progetti in una soluzione.  
  
 I progetti svolgono un ruolo significativo nella determinazione dell'editor viene utilizzato quando un utente apre un elemento di progetto.  Un progetto può essere progettato per aprire determinati file utilizzando un editor specifico del progetto o un editor standard.  
  
 Un editor specifico del progetto richiede in genere che l'utente abbia familiarità speciale o utilizzare le interfacce speciali dal progetto.  Per ulteriori informazioni, vedere [Procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Un editor standard possibile aprire i file di una determinata estensione in qualsiasi progetto.  È possibile personalizzare alcuni editor standard, quali l'editor di testo di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , per i progetti ma mantenere il carattere pubblico.  Gli editor standard vengono creati utilizzando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
 Se nessun progetto nella soluzione soddisfi che può aprire un elemento di progetto, l'ide fornisce un progetto speciale denominato il progetto file esterni che apre il file.  
  
 Questo progetto speciale si aspetta l'apertura di un file esterno del contesto di un progetto.  Durante l'elaborazione del metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> , i file esterni interpretato sempre conforme con molto bassa priorità.  Di conseguenza, i file esterni interpretato sempre produce a qualsiasi progetto priorità più elevata che può aprire i file.  
  
 Il progetto file esterni non richiede all'utente in modo esplicito di crearla con la finestra di dialogo di **nuovo progetto** .  Inoltre, il progetto file esterni non viene gestito in modo permanente un elenco dei membri del progetto.  Utilizza una funzionalità facoltativa per registrare un elenco dei file utilizzati di recente per ciascun utente.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md)   
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)