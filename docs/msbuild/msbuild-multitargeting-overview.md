---
title: "MSBuild Multitargeting Overview | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# MSBuild Multitargeting Overview
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tramite MSBuild è possibile compilare un'applicazione per essere eseguita in una qualunque delle tante versioni di .NET Framework e in una qualunque delle tante piattaforme di sistema.  Ad esempio, è possibile compilare un'applicazione per essere eseguita in .NET Framework 2.0 su un sistema a 32 bit e compilare la stessa applicazione per essere eseguita in .NET Framework 4.5 su un sistema a 64 bit.  
  
> [!IMPORTANT]
>  Nonostante il nome "multitargeting", un progetto può essere destinato a un solo framework e a una sola piattaforma per volta.  
  
 Di seguito sono riportate alcune delle funzionalità di targeting di MSBuild:  
  
-   È possibile sviluppare un'applicazione destinata a una precedente versione di .NET Framework, ad esempio le versioni 2.0, 3.5 o 4.  
  
-   È possibile avere un framework di destinazione diverso da .NET Framework, ad esempio Silverlight.  
  
-   L'applicazione può essere destinata a un *profilo del framework*, vale a dire un sottoinsieme predefinito di un framework di destinazione.  
  
-   In caso di rilascio di un Service Pack per la versione corrente di .NET Framework, è possibile destinare l'applicazione a tale Service Pack.  
  
-   Il targeting di MSBuild garantisce che un'applicazione utilizzi solo le funzionalità disponibili nel framework e nella piattaforma di destinazione.  
  
## Framework di destinazione e piattaforma di destinazione  
 Un *framework di destinazione* è la versione di .NET Framework per la quale un progetto è stato compilato appositamente e una *piattaforma di destinazione* è la piattaforma di sistema per la quale il progetto è stato compilato appositamente.  Ad esempio, è preferibile destinare un'applicazione a .NET Framework 2.0 per eseguirla su una piattaforma a 32 bit compatibile con la famiglia di processori 802x86 \(x86\).  La combinazione di framework di destinazione e piattaforma di destinazione è nota come *contesto di destinazione*.  Per ulteriori informazioni, vedere [Target Framework and Target Platform](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## Set di strumenti \(ToolsVersion\)  
 Un Set di strumenti comprende gli strumenti, le attività e le destinazioni utilizzate per creare l'applicazione.  Un set di strumenti include compilatori come csc.exe e vbc.exe, il file di destinazioni comuni \(microsoft.common.targets\) e il file delle attività comuni \(microsoft.common.tasks\).  Il Set di strumenti 4.5 può essere utilizzato per creare progetti destinati a .NET Framework versioni 2.0, 3.0, 3.5, 4 e 4.5. Tuttavia, il Set di strumenti 2.0 consente soltanto di scegliere come destinazione .NET Framework versione 2.0.  Per ulteriori informazioni, vedere [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## Assembly di riferimento  
 Gli assembly di riferimento specificati nel Set di strumenti aiutano a progettare e sviluppare un'applicazione.  Questi assembly di riferimento non solo consentono una specifica compilazione delle destinazioni, ma limitano anche i componenti e le funzionalità dell'IDE di Visual Studio a quelli compatibili con la destinazione.  Per ulteriori informazioni, vedere [Resolving Assemblies at Design Time](../msbuild/resolving-assemblies-at-design-time.md).  
  
## Configurazione di destinazioni e attività  
 È possibile configurare le destinazioni e le attività di MSBuild per l'esecuzione out\-of\-process con MSBuild, in modo che si possano scegliere come destinazione contesti notevolmente diversi da quello corrente.  Ad esempio, è possibile scegliere come destinazione un'applicazione .NET Framework 2.0 a 32 bit mentre nel computer di sviluppo è in esecuzione .NET Framework 4.5 su una piattaforma a 64 bit. Per ulteriori informazioni, vedere [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md).  
  
## Risoluzione dei problemi  
 Possono verificarsi errori se si tenta di fare riferimento a un assembly che non fa parte del contesto di destinazione.  Per ulteriori informazioni su questi errori e su come agire al riguardo, consultare [Troubleshooting .NET Framework Targeting Errors](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).