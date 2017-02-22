---
title: "Configurazione del progetto per la Gestione distribuzione | Microsoft Docs"
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
  - "configurazioni di progetto, gestione della distribuzione"
  - "progetti [Visual Studio SDK], configurazione per la Gestione distribuzione"
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Configurazione del progetto per la Gestione distribuzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La distribuzione implica fisicamente di spostare gli elementi di output da un processo di compilazione nella posizione prevista per il debug e installazione.  Ad esempio, un'applicazione Web potrebbe essere compilata in un computer locale e quindi essere inserita nel server.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due modi per i progetti possono fare parte della distribuzione:  
  
-   Come argomento del processo di distribuzione.  
  
-   Come amministratore del processo di distribuzione.  
  
 Prima che le soluzioni possono essere distribuite, è innanzitutto necessario aggiungere un progetto di distribuzione configurare le opzioni di distribuzione.  Se il progetto di distribuzione non esiste, viene richiesto se si desidera creare uno quando si seleziona **soluzione di distribuzione** dal menu di **Compilazione** o fare clic con il pulsante destro del mouse sulla soluzione.  Fare clic **sì** visualizzata la finestra di dialogo di **aggiungere il nuovo progetto** con il progetto **procedura guidata remota di distribuzione** selezionato.  
  
 La procedura guidata remota di distribuzione richiede il tipo di applicazione \(windows o web, i gruppi di output del progetto di importazione, tutti i file aggiuntivi che si desidera importare e il computer remoto si desidera distribuire in.  L'ultima pagina della procedura guidata viene visualizzato un riepilogo delle opzioni selezionate.  
  
 Progetti inclusi l'argomento di elementi di output di distribuzione dei prodotti di processo che devono essere spostati in un ambiente alternativo.  Questi elementi di output sono descritti come parametri per l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , il cui scopo primario se nel consentire ai progetti raggruppare gli output.  Per ulteriori informazioni relativi all'implementazione di `IVsProjectCfg2`, vedere [Configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md).  
  
 I progetti di distribuzione, che gestisce il processo di distribuzione, abilitare il comando di distribuzione e rispondono quando questo comando è selezionato.  I progetti di distribuzione implementano l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> per eseguire la distribuzione e per effettuare chiamate all'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> per segnalare gli eventi dello stato di distribuzione.  
  
 Le configurazioni possono specificare le dipendenze che influiscono sulle relative operazioni di compilazione o distribuzione.  Le dipendenze di compilazione o distribuzione sono progetti che devono essere compilati o distribuiti prima o dopo le configurazioni sono la compilazione o la distribuzione.  Le dipendenze di compilazione tra i progetti vengono descritte con l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> e le dipendenze di distribuzione con <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> collegamento.  Per ulteriori informazioni, vedere [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md).  
  
## Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md)