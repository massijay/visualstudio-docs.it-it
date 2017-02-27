---
title: "Struttura VSPackage (origine controllo VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Package VS, struttura"
  - "pacchetti di controllo di origine, cenni preliminari su VSPackage"
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Struttura VSPackage (origine controllo VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

il SDK di pacchetto di controllo di origine fornisce indicazioni per la creazione di un package VS che consentono a un responsabile del controllo di origine per integrare la propria funzionalità di controllo di origine con il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente. Un package VS è un componente COM che in genere viene caricato su richiesta per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato \(IDE\) in base ai servizi che vengono annunciati dal pacchetto nelle voci del Registro di sistema. Ogni VSPackage deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. In genere un VSPackage utilizza i servizi offerti dal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE e proffers alcuni servizi propri.  
  
 Un VSPackage dichiara le voci di menu e stabilisce uno stato dell'elemento predefinito tramite il file vsct. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE visualizza le voci di menu in questo stato finché non viene caricato il VSPackage. Successivamente, di VSPackage attuazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> viene chiamato per abilitare o disabilitare le voci di menu.  
  
## Caratteristiche del controllo del pacchetto di origine  
 Un controllo del codice sorgente VSPackage è integrato nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 La semantica di VSPackage include:  
  
-   Interfaccia che deve essere implementata in quanto un VSPackage \(il `IVsPackage` interfaccia\)  
  
-   Implementazione di comandi dell'interfaccia utente \(file vsct e implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia\)  
  
-   Registrazione del VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Il controllo del codice sorgente VSPackage deve comunicare con questi altri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entità:  
  
-   Progetti  
  
-   Editor  
  
-   Soluzioni  
  
-   Windows  
  
-   La tabella document in esecuzione  
  
### Servizi dell'ambiente Visual Studio che possono essere utilizzati  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Servizio SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### Interfacce VSIP implementazione e la chiamata  
 Un pacchetto di controllo di origine è un VSPackage e pertanto può interagire direttamente con altri package VS che sono registrati con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per garantire l'ampia gamma di controllo del codice sorgente, un controllo del codice sorgente VSPackage è possibile gestire con interfacce fornite da progetti o la shell.  
  
 Tutti i progetti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> a essere riconosciuto come un progetto all'interno di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Tuttavia, questa interfaccia è specializzata nella non sufficiente per controllo del codice sorgente. I progetti che si prevedono siano in origine controllano implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Questa interfaccia viene utilizzata per il controllo del codice sorgente VSPackage per eseguire query su un progetto per il relativo contenuto e fornire i glifi e informazioni di associazione \(le informazioni necessarie per stabilire una connessione tra il percorso del server e il percorso del disco di un progetto incluso nel controllo del codice sorgente\).  
  
 Il controllo del codice sorgente VSPackage implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, che a sua volta consente ai progetti di registrarsi per controllo del codice sorgente e recuperare le icone di stato.  
  
 Per un elenco completo di interfacce che è necessario prendere in considerazione un controllo del codice sorgente VSPackage, vedere [Interfacce e i servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Interfacce e i servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)