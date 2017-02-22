---
title: "Configurazione di soluzione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurazioni di soluzione"
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Configurazione di soluzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le configurazioni di soluzione archiviano proprietà a livello di soluzione. Indicano il comportamento della **Start** chiave \(F5\) e **Build** comandi. Per impostazione predefinita, questi comandi compilare e avviare la configurazione di debug. Entrambi i comandi vengono eseguite nel contesto di una configurazione di soluzione. Ciò significa che l'utente può attendersi F5 per avviare e qualsiasi soluzione attiva viene configurata tramite le impostazioni di compilazione. L'ambiente è progettata per ottimizzare per soluzioni anziché progetti quando si tratta di compilazione e l'esecuzione.  
  
 Barra degli strumenti standard di Visual Studio contiene un pulsante di avvio e una configurazione di soluzione elenco a discesa a destra del pulsante Start. Questo elenco consente agli utenti di scegliere la configurazione deve essere avviata quando si preme F5, creare le proprie configurazioni di soluzione o modificare una configurazione esistente.  
  
> [!NOTE]
>  Non sono presenti interfacce di estensibilità per creare o modificare le configurazioni della soluzione. È necessario utilizzare `DTE.SolutionBuilder`. Tuttavia, esistono API di estensibilità per la compilazione della soluzione di gestione. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Ecco come è possibile implementare le configurazioni di soluzione supportate dal tipo di progetto:  
  
-   Progetto  
  
     Visualizza i nomi dei progetti inclusi nella soluzione corrente.  
  
-   Configurazione  
  
     Per fornire l'elenco delle configurazioni supportate per il tipo di progetto e visualizzato nelle pagine delle proprietà, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
     La colonna di configurazione viene visualizzato il nome della configurazione di progetto da compilare in questa configurazione di soluzione e vengono elencate tutte le configurazioni di progetto quando si fa clic sul pulsante freccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> metodo per compilare questo elenco. Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metodo indica che il progetto supporta la modifica della configurazione, nuovo o modifica selezioni vengono inoltre visualizzate sotto l'intestazione di configurazione. Ognuna di queste impostazioni avviare le finestre di dialogo che chiamano metodi di `IVsCfgProvider2` interfaccia per modificare le configurazioni del progetto.  
  
     Se un progetto non supporta le configurazioni, la colonna di configurazione viene visualizzato Nessuno ed è disabilitata.  
  
-   Piattaforma  
  
     Visualizza la piattaforma di compilazioni per la configurazione di progetto selezionato e vengono elencate tutte le piattaforme disponibili per il progetto quando si fa clic sul pulsante freccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> metodo per compilare questo elenco. Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metodo indica che il progetto supporta la modifica della piattaforma, nuovo o modifica selezioni vengono anche visualizzate sotto l'intestazione di piattaforma. Ognuna di queste impostazioni avviare le finestre di dialogo chiamano `IVsCfgProvider2` metodi per modificare le piattaforme disponibili del progetto.  
  
     Se un progetto non supporta piattaforme, nella colonna piattaforma per il progetto viene visualizzato Nessuno ed è disabilitata.  
  
-   Compilazione  
  
     Specifica se il progetto viene compilato dalla configurazione della soluzione corrente. Progetti non selezionati non vengono generati quando vengono richiamati i comandi di compilazione a livello di soluzione nonostante le dipendenze di progetto che contengono. Progetti non selezionati per essere compilato sono ancora inclusi nel debug, esecuzione, l'assemblaggio e distribuzione della soluzione.  
  
-   Distribuisci  
  
     Specifica se il progetto verrà distribuito quando vengono utilizzati i comandi di avvio o distribuire con la configurazione di compilazione della soluzione. La casella di controllo per questo campo sarà disponibile se il progetto supporta la distribuzione mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> oggetto.  
  
 Dopo aver aggiunto una nuova configurazione di soluzione, l'utente può selezionarlo dalla casella di riepilogo Configurazione soluzione sulla barra degli strumenti standard per compilare e\/o avviare la configurazione.  
  
## Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md)