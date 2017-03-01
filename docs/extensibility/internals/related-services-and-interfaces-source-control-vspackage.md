---
title: Servizi correlati e le interfacce (origine controllo VSPackage) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6d16e8eb229cd5187ae91630d9330a0e0f24eda2
ms.lasthandoff: 02/22/2017

---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfacce (origine controllo VSPackage) e servizi correlati
In questa sezione sono elencati tutti il controllo origine interfacce correlate VSPackage il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Il controllo del codice sorgente VSPackage implementa alcune di queste interfacce e altri utilizza per effettuare attività di controllo di origine.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfacce implementate da e per origine controllo VSPackage  
 Le interfacce seguenti sono descritti nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], e il controllo del codice sorgente VSPackage implementa un sottoinsieme di essi in base al relativo set di funzionalità desiderata. Alcune interfacce sono contrassegnate come obbligatorio e deve essere implementata da ogni controllo del codice sorgente VSPackage.  
  
 Per tali interfacce che non implementano un pacchetto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un'implementazione predefinita. Si noti che l'implementazione predefinita è progettato per i casi, quando non viene registrata alcuna VSPackage e non viene controllato alcun progetto. Un controllo del codice sorgente scritto correttamente VSPackage implementa tutte le necessarie interfacce anziché lasciare l'implementazione predefinita di tali interfacce.  
  
 Un controllo del codice sorgente VSPackage deve implementare un servizio privato che incapsula alcune o tutte le interfacce seguenti.  
  
 Le interfacce sono:  
  
-   Richiesta: L'entità appropriata (controllo del codice sorgente VSPackage Stub di controllo di origine, project) deve implementare l'interfaccia.  
  
-   Consigliato: L'entità deve implementare questa interfaccia. controllo del codice sorgente in caso contrario, potrebbe risultare limitato.  
  
-   Facoltativo: l'entità può implementare questa interfaccia per fornire un set di funzionalità più avanzato.  
  
|Interfaccia|Scopo|Implementato da|Implementare?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Editor di chiamano questa interfaccia prima di modificare o salvare un file. Il controllo del codice sorgente VSPackage è possibile estrarre il file o negare l'operazione se l'estrazione ha esito negativo.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Questa interfaccia fornisce funzionalità di controllo di base per i progetti, ad esempio la registrazione e annullamento della registrazione di progetti con controllo del codice sorgente e il supporto per i glifi di controllo di base.|Controllo del codice sorgente VSPackage|Richiesto|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Questa interfaccia viene ottenuta dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>utilizzando il <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>funzione, o semplicemente il cast dell'oggetto che implementa `IVsHierarchy` a `IVsSccProject2`.</xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Viene utilizzato per ottenere i file di controllo del codice sorgente in un progetto o per informare il progetto del percorso o lo stato del controllo di origine corrente.|Progetto|Richiesto|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Il modulo di integrazione utilizza questa interfaccia per impostare il package VS attivo corrente.|Controllo del codice sorgente VSPackage|Richiesto|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Questa interfaccia si basa su un modello di sottoscrizione. Qualsiasi VSPackage può segnalare che si desidera ricevere eventi di documento e informato sugli eventi che stanno per verificarsi dalla shell. Viene implementata e gestita da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], che a sua volta passa gli eventi che implementa il `IVsTrackProjectDocumentsEvents2` a VSPackage.|Stub di controllo di origine|Richiesto|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Questa interfaccia fornisce l'elaborazione batch, operazioni di lettura/scrittura sincronizzati e un avanzato `OnQueryAddFiles` metodo.|Stub di controllo di origine|Richiesto|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Esplora soluzioni** e progetti chiamano questa interfaccia vengono aggiunti nuovi file per i progetti, o quando i file e cartelle vengono rinominate o eliminate da progetti. Il controllo del codice sorgente VSPackage può estrarre il file di progetto o annullare l'operazione.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Esplora soluzioni** e progetti di chiamano questa interfaccia in risposta alle chiamate ai metodi dell'interfaccia IVstrackProjectDocuments3. Operazioni di lettura/scrittura, il controllo del codice sorgente VSPackage può tenere traccia delle operazioni in batch, sincronizzate e lavorare con più avanzate `OnQueryAddFiles` metodo.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Questa interfaccia fornisce supporto di gestione di integrazione per progetti Web.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Questa interfaccia viene utilizzata per recuperare le descrizioni comandi per i file di controllo del codice sorgente nei progetti.|Controllo del codice sorgente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Questa interfaccia fornisce il supporto di estensione dello spazio dei nomi.|Controllo del codice sorgente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage Usa questa interfaccia per integrare un'estensione dello spazio dei nomi nel **New**, **aprire**, o **salvare** finestre di dialogo. Di conseguenza, i progetti possono essere automaticamente aggiunto al controllo del codice sorgente al momento della creazione o aggiunti al controllo del codice sorgente quando si salva un operazione è attiva.|Controllo del codice sorgente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage Usa questa interfaccia per definire i glifi aggiuntivi come icone di controllo di origine per i nodi **Esplora**.|Controllo del codice sorgente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|Il **Aggiungi** la finestra di dialogo per i progetti Web Usa questa interfaccia. Fornisce metodi per la visualizzazione per un percorso di controllo di origine e per l'apertura di un progetto Web aggiunto in precedenza nel repository di controllo di origine in tale posizione.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Questa interfaccia fornisce supporto per il caricamento asincrono (in background) dei progetti dal controllo del codice sorgente.|Controllo del codice sorgente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Questa interfaccia consente ai progetti di seguire l'avanzamento del caricamento asincrono avviato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Progetto|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Questa interfaccia consente all'IDE di query sul controllo di origine attiva VSPackage. L'IDE di una query il valore delle impostazioni di controllo di origine che hanno un significato anche quando non esiste alcun controllo del codice sorgente active che VSPackage registrato. Questa interfaccia viene implementata e gestita da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Stub di controllo di origine|Richiesto|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Questa interfaccia viene utilizzata la registrazione di controllo del codice sorgente VSPackage.|Stub di controllo di origine|Richiesto|  
|<xref:EnvDTE.SourceControl></xref:EnvDTE.SourceControl>|Questa interfaccia viene utilizzata nel modello di automazione. Di conseguenza, espone solo le funzioni che possono essere eseguite senza visualizzare l'interfaccia utente.|Controllo del codice sorgente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Questa interfaccia viene utilizzata per salvare l'origine delle impostazioni di controllo nel file di soluzione (sln). Le impostazioni includono il percorso di controllo di origine e il flag di stato di controllo di origine.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Questa interfaccia viene utilizzata per salvare le impostazioni di controllo di origine nel file di opzioni (Options) della soluzione. Ciò può includere impostazioni di controllo di origine specifici dell'utente, ad esempio il percorso di integrazione dell'utente corrente.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Questa interfaccia viene utilizzata per monitorare gli eventi per eseguire operazioni come la ricerca nei file di progetto prima della chiusura di soluzioni, o per ottenere nuovi file dal controllo del codice sorgente quando si apre un progetto.|Controllo del codice sorgente VSPackage|Consigliato|  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
