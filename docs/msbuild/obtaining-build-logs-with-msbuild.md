---
title: "Recupero di log di compilazione con MSBuild | Microsoft Docs"
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
  - "MSBuild, registrazione"
  - "registrazione [MSBuild]"
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 27
caps.handback.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Recupero di log di compilazione con MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tramite le opzioni con MSBuild, è possibile specificare quanti dati di compilazione si desidera esaminare e se si desidera salvare i dati di compilazione a uno o più file.  È inoltre possibile specificare un logger personalizzato per raccogliere i dati di compilazione.  Per informazioni sulle opzioni della riga di comando di MSBuild che questo argomento non vengono illustrati, vedere [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Se si compilano progetti utilizzando l'ide di Visual Studio, è possibile risolvere i problemi relativi a tali compilazioni verifica dei log di compilazione.  Per ulteriori informazioni, vedere [Procedura: visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## Impostare il livello di dettaglio  
 Quando si compila un progetto utilizzando MSBuild senza specificare un livello di dettaglio, vengono visualizzate le seguenti informazioni nel log di output:  
  
-   Errori, avvisi e messaggi suddivisi in categorie come estremamente importante.  
  
-   Alcuni eventi di stato.  
  
-   Un riepilogo della compilazione.  
  
 Utilizzando l'opzione di **\/verbosity** \(**\/v**\), è possibile controllare la quantità di dati visualizzati nel log di output.  I problemi, utilizzare un livello di dettaglio di `detailed` \(`d`\) o di `diagnostic` \(`diag`\), che fornisce la maggior parte delle informazioni.  
  
 Il processo di compilazione può essere più lenta quando si imposta **\/verbosity** a `detailed` e persino più lenta quando si imposta **\/verbosity** a `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## Salvare il log di compilazione in un file  
 È possibile utilizzare l'opzione di **\/fileLogger** \(**fl**\) per salvare i dati di compilazione in un file.  Nell'esempio salva i dati di compilazione in un file denominato `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 Nell'esempio seguente, il file di log è denominato `MyProjectOutput.log`e il livello di dettaglio output di log è impostato su `diagnostic`.  Specificare queste due impostazioni utilizzando l'opzione di **\/filelogparameters** \(`flp`\).  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Per ulteriori informazioni, vedere [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## Salvare l'output del log a più file  
 Nell'esempio salva l'intero log in `msbuild1.log`, solo gli errori a `JustErrors.log`e solo gli avvisi a `JustWarnings.log`.  L'esempio utilizza i numeri di file per ciascuno dei tre file.  I numeri di file specificati subito dopo le opzioni di **\/flp** e di **\/fl**, ad esempio `/fl1` e `/flp1`\).  
  
 Le opzioni di **\/filelogparameters** \(`flp`\) per i file 2 e 3 indicano quali denominazione ogni file e cosa includere in ogni file.  Non è specificato alcun nome per il file 1, pertanto il nome predefinito di `msbuild1.log` viene utilizzato.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Per ulteriori informazioni, vedere [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## Utilizzo di un logger personalizzato  
 Per scrivere un logger personalizzato, è sufficiente creare un tipo gestito che implementi l'interfaccia <xref:Microsoft.Build.Framework.ILogger>.  È possibile utilizzare un logger personalizzato, ad esempio, per inviare gli errori di compilazione in posta elettronica, per registrarli in un database, o per registrarli in un file XML.  Per ulteriori informazioni, vedere [Build Loggers](../msbuild/build-loggers.md).  
  
 Nella riga di comando di MSBuild, il logger personalizzato utilizzando l'opzione di **\/logger**.  È inoltre possibile utilizzare l'opzione di **\/noconsolelogger** per disabilitare il logger di console predefinito.  
  
## Vedere anche  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Build Loggers](../msbuild/build-loggers.md)   
 [Logging in a Multi\-Processor Environment](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Creating Forwarding Loggers](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)