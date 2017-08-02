---
title: "Configurazione del progetto per la compilazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti [Visual Studio SDK], configurazione per la compilazione"
  - "configurazioni di progetto, creazione"
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Configurazione del progetto per la compilazione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'elenco delle configurazioni di soluzione per una determinata soluzione viene gestito tramite la finestra di dialogo configurazioni di soluzione.  
  
 Un utente può creare ulteriori configurazioni di soluzione, ciascuna con un nome univoco. Quando l'utente crea una nuova configurazione di soluzione, l'IDE per impostazione predefinita per il nome di configurazione corrispondente in progetti o di Debug se non esiste alcun nome corrispondente. L'utente può modificare la selezione per soddisfare esigenze specifiche, se necessario. L'unica eccezione a questo comportamento è quando il progetto supporta una configurazione che corrisponde al nome della nuova configurazione di soluzione. Si supponga ad esempio una soluzione che contiene Project1 e Progetto2. Project1 dispone di configurazioni di progetto Debug, finale e MyConfig1. Progetto2 dispone di configurazioni di progetto Debug, finale e MyConfig2.  
  
 Se l'utente crea una nuova configurazione di soluzione denominata MyConfig2, Project1 associa la configurazione di Debug per la configurazione della soluzione per impostazione predefinita. Progetto2 associa inoltre la configurazione MyConfig2 per la configurazione della soluzione per impostazione predefinita.  
  
> [!NOTE]
>  L'associazione è tra maiuscole e minuscole.  
  
 Quando l'utente seleziona il **selezione multipla** elemento nell'elenco di riepilogo a discesa configurazione, l'ambiente consente di visualizzare una finestra di dialogo che fornisce l'elenco delle configurazioni disponibili.  
  
 ![Configurazioni multiple](~/docs/extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Configurazioni multiple  
  
 In questa finestra di dialogo, l'utente può selezionare una o più configurazioni. Una volta selezionato, i valori delle proprietà visualizzati nella finestra di dialogo Pagine delle proprietà riflettono l'intersezione dei valori per le configurazioni selezionate.  
  
 Vedere [Configurazione di soluzione](../../extensibility/internals/solution-configuration.md) per le informazioni relative all'aggiunta e ridenominazione di configurazioni per soluzioni e progetti.  
  
 Dipendenze progetto e l'ordine di compilazione sono indipendenti dalla configurazione della soluzione:, ovvero è possibile impostare solo della struttura di una dipendenza per tutti i progetti nella soluzione. Pulsante destro del mouse la soluzione o il progetto e quindi scegliere il **Dipendenze progetto** o **ordine compilazione progetto** opzione verrà visualizzata la la **Dipendenze progetto** la finestra di dialogo. Può anche essere aperta dal **progetto** menu.  
  
 ![Dipendenze progetto](~/docs/extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Dipendenze progetto  
  
 Dipendenze progetto determinano l'ordine in cui i progetti vengano compilati. Utilizzare la scheda di ordine di compilazione nella finestra di dialogo per visualizzare l'ordine esatto in cui i progetti all'interno di una soluzione di compilazione e la scheda Dipendenze consente di modificare l'ordine di compilazione.  
  
> [!NOTE]
>  I progetti nell'elenco le caselle di controllo selezionate ma vengono visualizzate in grigio sono stati aggiunti dall'ambiente a causa di dipendenze esplicite specificato dalla <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfacce e non può essere modificato. Ad esempio, aggiungere un riferimento al progetto da un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto a un altro progetto aggiunge automaticamente una dipendenza di compilazione che può essere rimossa solo eliminando il riferimento. Impossibile selezionare progetti cui caselle di controllo sono chiare e vengono visualizzate in grigio perché in questo modo verrà creato un ciclo di dipendenza \(ad esempio, Project1 sarebbe dipende Progetto2 e Progetto2 sarebbe dipende Project1\), che verrebbe stallo la compilazione.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] processi di compilazione includono le operazioni di collegamento che vengano richiamate con un singolo comando di generazione e compilazione tipico. Due altri processi di compilazione possono anche essere supportati: un'operazione di pulizia per eliminare tutti gli elementi di output da una compilazione precedente e un controllo aggiornato per determinare se un elemento di output in una configurazione è stato modificato.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> gli oggetti restituiscono un oggetto corrispondente <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> \(restituiti da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>\) per gestire i processi di compilazione. Per segnalare lo stato di un'operazione di compilazione in corso, le configurazioni di effettuano chiamate a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, un'interfaccia implementata dall'ambiente e qualsiasi altro oggetto interessato eventi dello stato di compilazione.  
  
 Una volta creato, è possono utilizzare le impostazioni di configurazione per determinare se possono essere eseguiti sotto il controllo del debugger. Implementano configurazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> per supportare il debug.  
  
 Dopo avere implementato le dipendenze di progetto, è possibile modificare a livello di programmazione le dipendenze tramite il modello di automazione. Chiamare <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> nel modello di automazione. Non sono presenti interfacce a livello di API VSIP disponibili che consentono la modifica diretta delle configurazioni di manager di compilazione di soluzioni e le relative proprietà.  
  
 Inoltre, è possibile fornire una griglia nella finestra di dipendenze del progetto. Per altre informazioni, vedere [Proprietà Visualizza griglia](../../extensibility/internals/properties-display-grid.md).  
  
## Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione del progetto per la Gestione distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md)