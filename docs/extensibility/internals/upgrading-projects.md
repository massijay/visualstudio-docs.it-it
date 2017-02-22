---
title: "Aggiornamento di progetti | Microsoft Docs"
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
  - "aggiornamento di package VS"
  - "aggiornamento delle applicazioni, strategie"
  - "Package VS, supporto per l'aggiornamento"
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Aggiornamento di progetti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le modifiche al modello di progetto da una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] al e può richiedono che i progetti e le soluzioni vengano aggiornati in modo da poterli eseguire la versione più recente.  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornisce interfacce che possono essere utilizzate per implementare il supporto di aggiornamento in per contenere i progetti.  
  
## strategie di aggiornamento  
 Per supportare un aggiornamento, l'implementazione del sistema del progetto deve definire e implementare una strategia di aggiornamento.  Nella determinazione della strategia, è possibile scegliere per supportare il backup affiancato \(SxS\), il backup di copia, o entrambi.  
  
-   Il backup di SxS significa che un progetto copia solo i file che devono aggiornare sul posto, aggiungere un suffisso appropriato di nome file, ad esempio, OLD.  
  
-   Il backup della copia significa che un progetto copia tutti gli elementi di progetto all'forniti dal percorso di backup.  I file rilevanti nella posizione originale del progetto vengono aggiornati.  
  
## come aggiornamento Works  
 Quando una soluzione creata in una versione precedente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene aperta in una versione più recente, l'ide controlla il file di soluzione per determinare se deve essere aggiornato.  Se l'aggiornamento è obbligatorio, **aggiornamento guidato** viene automaticamente avviato per accedere all'utente con il processo di aggiornamento.  
  
 Quando una soluzione necessario aggiornare, eseguendo una query su ogni factory di progetto per la strategia di aggiornamento.  La strategia determina se i contenuti multimediali factory di progetto copiare il backup o il ripristino di SxS.  Le informazioni vengono inviate a **aggiornamento guidato**, che raccolgono informazioni necessarie per il backup e sono elencate le opzioni applicabili all'utente.  
  
### soluzioni composte da più progetti  
 Se una soluzione contiene più progetti e le strategie di aggiornamento differenti, ad esempio quando un progetto c\+\+ che supporta solo il backup di SxS e un progetto Web che solo il backup della copia di supporto, factory di progetto deve negoziare la strategia di aggiornamento.  
  
 La soluzione eseguendo una query su ogni factory di progetto per <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>.  Chiama quindi l'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject  **aggiornamento guidato** quindi viene richiamato.  
  
 After the user completes the wizard, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> is called on each project factory to perform the actual upgrade.  Per facilitare il backup, i metodi di IVsProjectUpgradeViaFactory forniscono al servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> per registrare i dettagli del processo di aggiornamento.  Questo servizio non può essere memorizzato nella cache.  
  
 Dopo avere aggiornato tutti i file globali relativi, ogni factory di progetto può scegliere di creare un'istanza di un progetto.  L'implementazione del progetto deve supportare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  Il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> viene quindi chiamato per aggiornare tutti gli elementi di progetto appropriate.  
  
> [!NOTE]
>  Il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> non fornisce al servizio di SVsUpgradeLogger.  questo servizio può essere ottenuto chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## Suggerimenti  
 Utilizzare il servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> per controllare se è possibile modificare un file prima di modificarlo e consente salvarlo prima di salvarlo.  Ciò consentirà il backup e migliorare le implementazioni gestire i file di progetto al controllo del codice sorgente, file con autorizzazioni insufficienti, e così via.  
  
 Utilizzare il servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante le fasi di backup e migliorare per fornire informazioni sull'esito positivo o negativo del processo di aggiornamento.  
  
 Per ulteriori informazioni sul backup e su come migliorare i progetti, vedere i commenti per IVsProjectUpgrade in vsshell2.idl.  
  
## Vedere anche  
 [Progetti](../../extensibility/internals/projects.md)   
 [Aggiornamento di progetti personalizzati](../../misc/upgrading-custom-projects.md)   
 [Aggiornamento degli elementi di progetto](../../misc/upgrading-project-items.md)