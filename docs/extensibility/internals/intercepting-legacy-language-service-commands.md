---
title: "Intercettazione di comandi del servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandi, intercettazione di servizio di linguaggio"
  - "servizi di linguaggio, intercettazione di comandi"
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Intercettazione di comandi del servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è possibile che il servizio di linguaggio che ordina l'intercettazione della visualizzazione di testo gestirebbe in caso contrario.  Ciò si rivela utile per il comportamento specifico del linguaggio che la visualizzazione di testo non gestisce.  È possibile intercettare tali controlli aggiungendo uno o più filtri di comando alla visualizzazione di testo dal servizio di linguaggio.  
  
## Acquisizione e risolve il comando  
 Un filtro di comando è un oggetto di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> che consente di monitorare determinate sequenze di caratteri o i controlli principali.  È possibile associare più di un filtro di comando con un'unica visualizzazione di testo.  Ogni visualizzazione di testo gestisce i filtri di una catena di comando.  Dopo avere creato un nuovo filtro di comando, aggiungere il filtro alla catena per la visualizzazione di testo appropriata.  
  
 Chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per aggiungere il filtro del comando nella catena.  When you call <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] returns another command filter to which you can pass the commands that your command filter does not handle.  
  
 Sono disponibili le opzioni seguenti per la gestione del comando:  
  
-   Gestire il comando e passare il comando al filtro seguente dal comando nella catena.  
  
-   Gestire il comando e non passare il comando al filtro seguente dal comando.  
  
-   Non gestire il comando, ma passare il comando al filtro seguente dal comando.  
  
-   Ignorare il comando.  Non è in grado di gestire il filtro corrente e non passarlo al filtro seguente.  
  
 Per informazioni sui comandi il servizio di linguaggio deve gestire, vedere [Comandi importanti per i filtri di servizio di linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).