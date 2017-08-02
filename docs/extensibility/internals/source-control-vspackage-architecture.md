---
title: "Architettura di origine del controllo VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti di controllo di origine, architettura"
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Architettura di origine del controllo VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un pacchetto del controllo del codice sorgente è un package VS che utilizza i servizi che l'ide di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v5.0.  In cambio, un pacchetto del controllo del codice sorgente fornisce la funzionalità come servizio di controllo del codice sorgente.  Inoltre, un pacchetto del controllo del codice sorgente è un'alternativa più versatile che un plug\-in controllo del codice sorgente per il controllo del codice sorgente integrazione in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Un plug\-in controllo del codice sorgente che implementa il plug\-in controllo del codice sorgente API si attiene a un contratto rigido.  Ad esempio, un plug\-in non può sostituire UI predefinita di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(UI\).  Inoltre, il plug\-in controllo del codice sorgente API non consente a un plug\-in per implementare il proprio modello di controllo del codice sorgente.  Un pacchetto del controllo del codice sorgente, tuttavia, supera entrambe limitazioni.  Un pacchetto del controllo del codice sorgente dispone di controllo completo sulle operazioni di controllo del codice sorgente in un utente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Inoltre, un pacchetto del controllo del codice sorgente possibile utilizzare il proprio modello e logica di controllo del codice sorgente e può definire tutte le interfacce utente controllo\-correlate di origine.  
  
## Componenti del pacchetto del controllo del codice sorgente  
 Come illustrato nel diagramma dell'architettura, una parte di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] denominato lo stub del controllo del codice sorgente è un package VS che integra un pacchetto del controllo del codice sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Lo stub del controllo del codice sorgente gestisce le attività seguenti.  
  
-   Fornisce l'interfaccia utente comune che è obbligatorio per la registrazione del pacchetto del controllo del codice sorgente.  
  
-   Carica un pacchetto del controllo del codice sorgente.  
  
-   Imposta un pacchetto del controllo del codice sorgente come attiva\/inattivo.  
  
 Lo stub del controllo del codice sorgente viene trovato il servizio attivo per il pacchetto del controllo del codice sorgente e vengono indicate tutte le chiamate al servizio in ingresso dall'IDE al pacchetto.  
  
 Il pacchetto di adattatori di controllo del codice sorgente è un pacchetto del controllo del codice sorgente speciale che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v5.0.  Questo pacchetto è il componente centrale per il supporto dei collegamenti del controllo del codice sorgente in base al plug\-in controllo del codice sorgente API.  Quando un plug\-in controllo del codice sorgente è il plug\-in attivo, lo stub del controllo del codice sorgente invia i relativi eventi al pacchetto di adattatori di controllo del codice sorgente.  A sua volta, il pacchetto di adattatori di controllo del codice sorgente comunica con il plug\-in controllo del codice sorgente mediante il plug\-in controllo del codice sorgente API e fornisce un'interfaccia utente predefinita che è comune a tutti i collegamenti del controllo del codice sorgente.  
  
 Quando un pacchetto del controllo del codice sorgente è il pacchetto attivo, invece, lo stub del controllo del codice sorgente direttamente comunica con il pacchetto tramite le interfacce del pacchetto del controllo del codice sorgente di [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .  Il pacchetto del controllo del codice sorgente è responsabile dell'hosting della propria interfaccia utente del controllo del codice sorgente.  
  
 ![Rappresentazione grafica dell'architettura di controllo del codice sorgente](~/extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Per un pacchetto del controllo del codice sorgente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non fornisce il codice del controllo del codice sorgente o un'api per l'integrazione.  In contrapposizione con l'approccio descritto [Creazione di plug\-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md) in cui il plug\-in controllo del codice sorgente necessario implementare un insieme di funzioni rigido i callback.  
  
 Come per qualsiasi altro package VS, un pacchetto del controllo del codice sorgente è un oggetto COM che può essere creato utilizzando `CoCreateInstance`.  Il package VS è rende disponibili dell'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  Quando un'istanza è stata creata, un VSPackage riceve un puntatore di sito e un'interfaccia di<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> che fornisce l'accesso di un VSPackage servizi e le interfacce disponibili nell'IDE.  
  
 La scrittura di un pacchetto VS base del controllo del codice sorgente richiede la competenza più avanzata di programmazione che scrive in un plug\-in controllo del codice sorgente al plug\-in basato sull'API.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-vspackages.md)