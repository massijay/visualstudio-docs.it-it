---
title: "Creating Forwarding Loggers | Microsoft Docs"
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
  - "MSBuild, forwarding loggers"
  - "MSBuild, logging"
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Creating Forwarding Loggers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I logger di inoltro consentono di migliorare l'efficienza della registrazione permettendo di scegliere gli eventi che si desidera controllare durante la compilazione di progetti in un sistema multiprocessore.  L'attivazione dei logger di inoltro consente di impedire che eventi indesiderati sommergano il logger centrale, rallentando i tempi di compilazione e ingombrando il log.  
  
 Per creare un logger di inoltro è possibile implementare l'interfaccia <xref:Microsoft.Build.Framework.IForwardingLogger> e quindi implementare manualmente i metodi, o utilizzare la classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> e i metodi preconfigurati.  La seconda modalità di creazione risulta appropriata per la maggior parte delle applicazioni.  
  
## Registrazione e risposta agli eventi  
 Un logger di inoltro raggruppa informazioni sugli eventi di compilazione man mano che vengono riportati dal motore di compilazione secondario che è un processo di lavoro creato dal processo di compilazione principale nel corso di una compilazione in un sistema multiprocessore.  Quindi il logger di inoltro seleziona eventi da inoltrare al logger centrale, in base alle istruzioni date.  
  
 È necessario registrare logger di inoltro per gestire gli eventi che si desidera controllare.  Per registrare gli eventi, i logger devono eseguire l'override del metodo <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>.  Questo metodo ora include un parametro facoltativo, `nodecount` che è possibile impostare sul numero di processori nel sistema.  Per impostazione predefinita, il valore è 1.  
  
 Esempi di eventi da monitorare sono <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 In un ambiente multiprocessore, i messaggi di evento verranno ricevuti probabilmente in ordine non corretto.  È pertanto necessario valutare gli eventi utilizzando il gestore eventi nel logger di inoltro e programmarlo affinché determini quali eventi passare al redirector per l'inoltro al logger centrale.  Per portare a termine questa attività è possibile utilizzare la classe <xref:Microsoft.Build.Framework.BuildEventContext> associata a ogni messaggio, per identificare gli eventi che si desidera inoltrare e quindi passare i nomi degli eventi alla classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> \(o una sottoclasse\).  Quando si utilizza questo metodo, nessuna altra codificazione specifica è richiesta per l'inoltro degli eventi.  
  
## Specificare un logger di inoltro  
 Dopo la compilazione di un logger di inoltro in un assembly, è necessario che [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] lo utilizzi durante le compilazioni.  A tale scopo, utilizzare le opzioni `/FileLogger`, `/FileLoggerParameters` e `/DistributedFileLogger` insieme a MSBuild.exe.  L'opzione `/FileLogger` indica a MSBuild.exe il logger è e collegato direttamente. L'opzione `/DistributedFileLogger` indica che è presente un file di log per nodo.  Per impostare parametri sul logger di inoltro, utilizzare l'opzione `/FileLoggerParameters`.  Per ulteriori informazioni su queste e altre nuove opzioni di MSBuild.exe, vedere [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## Logger compatibili con più processori  
 Quando si compila un progetto in un sistema multiprocessore, i messaggi di compilazione provenienti da ogni processore non vengono sottoposti automaticamente a interfoliazione in una sequenza unificata.  Invece, è necessario stabilire una priorità di raggruppamento dei messaggi utilizzando la classe <xref:Microsoft.Build.Framework.BuildEventContext> associata a ogni messaggio.  Per ulteriori informazioni sulla compilazione multiprocessore, vedere [Logging in a Multi\-Processor Environment](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## Vedere anche  
 [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Build Loggers](../msbuild/build-loggers.md)   
 [Logging in a Multi\-Processor Environment](../msbuild/logging-in-a-multi-processor-environment.md)