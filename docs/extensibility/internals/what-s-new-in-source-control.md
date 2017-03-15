---
title: "Novit&#224; di controllo del codice sorgente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nuovo controllo del codice sorgente [Visual Studio SDK], novità"
  - "controllo del codice sorgente [Visual Studio SDK], novità"
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Novit&#224; di controllo del codice sorgente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] è possibile fornire una soluzione eccessivamente integrata del controllo del codice sorgente mediante l'implementazione di un controllo del codice sorgente VSPackage.  In questa sezione vengono descritte le funzionalità di controllo del codice sorgente Vspackage e vengono forniti cenni preliminari sui passaggi di implementazione.  
  
## Il controllo del codice sorgente VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due tipi di soluzioni del controllo del codice sorgente.  In tutte le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è comunque possibile integrare a un plug\-in basato sull'API di plug\-in controllo del codice sorgente.  È inoltre possibile creare un package VS per il controllo del codice sorgente che fornisce un'profondo\-integrazione, percorso di [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] appropriato per le soluzioni del controllo del codice sorgente che richiedono un elevato livello di elaborazione e dell'autonomia.  
  
 Un VSPackage possibile aggiungere qualsiasi tipo di funzionalità a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Un controllo del codice sorgente VSPackage fornisce una funzionalità del controllo del codice sorgente per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], dall'interfaccia utente inviato all'utente alla comunicazione di back\-end con il sistema di controllo del codice sorgente.  
  
 Distribuire un controllo del codice sorgente VSPackage non richiede un “tutto o nothing„ strategia.  L'autore di un controllo del codice sorgente VSPackage necessario inserire una quantità significativa di operazioni per distribuire un set di interfacce di controllo del codice sorgente e nuovi elementi di interfaccia utente \(finestre di dialogo, i menu e barre degli strumenti\) per coprire l'intera funzionalità di controllo del codice sorgente nonché le interfacce obbligatorie del pacchetto per integrare correttamente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 I passaggi seguenti fanno cenni preliminari su ciò che è necessario distribuire un pacchetto del controllo del codice sorgente.  Per informazioni dettagliate, vedere [Creazione di un pacchetto di controllo di origine](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Creare un package VS che offre un servizio di controllo del codice sorgente privato.  
  
2.  Implementare interfacce nei servizi correlati al controllo di origine che vengono offerti da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(ad esempio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> \).  
  
3.  Registrare il controllo del codice sorgente VSPackage.  
  
4.  Implementare un'interfaccia utente del controllo del codice sorgente, incluse le voci di menu, le finestre di dialogo, barre degli strumenti e menu di scelta rapida.  
  
5.  Tutti gli eventi correlati al controllo di origine vengono passati al controllo del codice sorgente VSackage quando è attivo e deve essere gestito dal package VS.  
  
6.  Il controllo del codice sorgente VSPackage deve ascoltare eventi come quelli che implementano l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> nonché eventi del documento \(TPD\) del progetto dell'indicatore \(implementato dall'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> \) e intraprendere azioni necessari.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Panoramica](../../extensibility/internals/source-control-integration-overview.md)   
 [Creazione di un pacchetto di controllo di origine](../../extensibility/internals/creating-a-source-control-vspackage.md)