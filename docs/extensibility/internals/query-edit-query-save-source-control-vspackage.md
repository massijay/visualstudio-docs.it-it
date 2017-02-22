---
title: "Query modifica Query Salva (origine controllo VSPackage) | Microsoft Docs"
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
  - "Eventi QEQS"
  - "Eventi di modifica Query Salva query"
  - "pacchetti di controllo di origine, salvare Query modifica Query eventi"
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Query modifica Query Salva (origine controllo VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

gli editor di[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possono trasmettere per comunicare agli eventi di salvataggio di query di modifica \(QEQS\) della query.  lo stub del controllo del codice sorgente di[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementa il servizio di QEQS, in modo che sia il destinatario degli eventi di QEQS.  Questi eventi vengono quindi delegati attualmente il controllo del codice sorgente attivo VSPackage.  Il controllo del codice sorgente attivo VSPackage implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e i relativi metodi.  I metodi di interfaccia di `IVsQueryEditQuerySave2` in genere vengono chiamati immediatamente prima di un documento viene modificato per la prima volta e immediatamente prima di un documento viene salvato.  
  
## eventi di QueryEditQuerySave  
 Il controllo del codice sorgente VSPackage necessario gestire gli eventi di QEQS implementando l'interfaccia di `IVsQueryEditQuerySave2` e i metodi necessari.  In viene fornita una breve descrizione dei due metodi che il package VS deve implementare al minimo.  Dell'implementazione effettiva deve essere conforme alla logica del modello di controllo del codice sorgente.  
  
### metodo di QueryEditFiles  
 The <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> is called when any project or editor wants to modify a file.  In teoria, questo metodo viene chiamato *prima* che il file viene modificato e quando un file viene salvato.  Una volta chiamato, il metodo di `IVsQueryEditQuerySave2::QueryEditFiles` controlla se i file specificati siano nel controllo del codice sorgente, se devono essere verificati e se possono essere ricaricati.  Se le condizioni impediscono i file da essere modificabili, il metodo di `IVsQueryEditQuerySave2::QueryEditFiles` indica al programma chiamante di annullare la modifica.  È inoltre possibile che il chiamante di specificare una modalità di chiamata.  In modalità “invisibile all'utente„, questo metodo viene eseguita solo se non comporta alcuna interfaccia utente a essere visualizzato.  Se l'interfaccia utente è inevitabile, un flag deve essere restituito per indicare il problema.  
  
 Il metodo si comporta in modo transazionale; ovvero se la modifica viene annullata in un singolo file, la modifica viene annullata per tutti i file.  Al contrario, se la modifica è consentita, è consentito per tutti i file.  Se questo metodo consente una volta la modifica per un dato insieme di file, deve consentire sempre la modifica sulle chiamate successive dello stesso insieme di file.  Il ciclo di consentire\-modifica continua fino alla chiusura, salvato e sono ricaricatoe i file; fino alla modifica di attributi \(proprietà\); o fino al controllo del codice sorgente il pacchetto viene modificato.  I casi da considerare quando si implementa il metodo di `IVsQueryEditQuerySave2::QueryEditFiles` includono più file, i file speciali, l'annullamento dell'utente e le modifiche in memoria.  
  
### metodo di QuerySaveFiles  
 L'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles\(System.UInt32, System.Int32, System.String\[\], System.UInt32\[\], Microsoft.VisualStudio.Shell.Interop.VSQEQS\_FILE\_ATTRIBUTE\_DATA\[\], System.UInt32@\) viene chiamato quando una qualsiasi progetto o l'editor deve salvare un set di file.  Quando vengono richiamati, il metodo di `IVsQueryEditQuerySave2::QuerySaveFiles` se i file specificati sono di sola lettura e se nel controllo del codice sorgente.  Se i file devono essere verificati, la chiamata viene delegata il pacchetto del controllo del codice sorgente.  Se le condizioni impediscono i file venga salvato, il metodo di `IVsQueryEditQuerySave2::QuerySaveFiles` necessario che nell'editor di annullamento di salvataggio.  Come per il metodo di `IVsQueryEditQuerySave2::QueryEditFiles` , è possibile che il chiamante di specificare una modalità di chiamata.  In modalità “invisibile all'utente„, questo metodo viene eseguita solo se non comporta alcuna interfaccia utente a essere visualizzato.  Se l'interfaccia utente è inevitabile, un flag deve essere restituito per indicare il problema.  
  
 Questo metodo deve comportarsi in modalità transazionale; ovvero se i salvataggio vengono annullati in un singolo file, i salvataggio vengono annullati per tutti i file.  Al contrario, se i salvataggio sono consentiti, deve essere consentito per tutti i file.  Come per il metodo di `IVsQueryEditQuerySave2::QueryEditFiles` , i casi da considerare quando si implementa il metodo di `IVsQueryEditQuerySave2::QuerySaveFiles` includono più file, i file speciali, l'annullamento dell'utente e le modifiche in memoria.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>