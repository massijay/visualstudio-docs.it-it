---
title: "Elementi di un modello di progetto | Microsoft Docs"
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
  - "progetti [Visual Studio SDK], considerazioni sull'implementazione"
  - "modelli di progetto"
  - "progetti [Visual Studio SDK], gli elementi"
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Elementi di un modello di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

le interfacce e le implementazioni di tutti i progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] condividono una struttura di base: il modello di progetto per il tipo di progetto.  Nel modello di progetto, ovvero il package VS si sta sviluppando, creare gli oggetti che seguono le decisioni di progettazione e del lavoro con funzionalità globale fornita dall'IDE.  Sebbene controllare come un elemento di progetto viene salvato in modo permanente, ad esempio, non viene notifica di controllo che un file deve essere salvato in modo permanente.  Quando un utente concentrare l'attenzione su un elemento di progetto aperto e selezionare **Salvare** il menu File nella barra dei menu di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , il codice di tipo di progetto deve rilevare il comando IDE, mantiene il file e viene inviata la notifica di nuovo a che il file non è più modificato.  
  
 Il package VS interagisce con l'ide tramite i servizi che consentono l'accesso alle interfacce dell'IDE.  Ad esempio, tramite servizi particolari, monitorare e i controlli e fornite informazioni sul contesto per le selezioni effettuate nel progetto.  Tutte le funzionalità generale dell'IDE necessaria per il pacchetto VS è fornita dai servizi.  per ulteriori informazioni sui servizi, vedere [Procedura: ottenere un servizio](../Topic/How%20to:%20Get%20a%20Service.md).  
  
 altre considerazioni di implementazione:  
  
-   un singolo modello di progetto può contenere più di un tipo di progetto.  
  
-   I tipi di progetto e le factory relative di progetto vengono registrati indipendente dai GUID.  
  
-   Ogni progetto deve disporre di un file modello o una procedura guidata per inizializzare il nuovo file di progetto quando un utente crea un nuovo progetto con l'interfaccia utente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Ad esempio, i modelli di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] inizializzano cosa che diventano i file di vcproj.  
  
 Nella figura seguente sono illustrate le interfacce primarie, servizi e oggetti che costituiscono l'implementazione di progetto tipica.  È possibile utilizzare l'helper di applicazione, HierUtil7, per creare gli oggetti sottostanti e altre boilerplate di programmazione.  Per ulteriori informazioni sul supporto dell'applicazione HierUtil7, vedere [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/it-it/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Rappresentazione grafica dei modelli di progetto Visual Studio](../../extensibility/internals/media/vsprojectmodel.png "vsProjectModel")  
modello di progetto  
  
 Per ulteriori informazioni sulle interfacce e servizi elencati nel diagramma precedente e altre interfacce facoltative allegati al diagramma, vedere [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).  
  
 I progetti possono supportare i controlli e pertanto devono implementare l'interfaccia di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> di partecipare al comando dal routing al contesto GUID del comando.  
  
## Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/it-it/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)   
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Procedura: ottenere un servizio](../Topic/How%20to:%20Get%20a%20Service.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)