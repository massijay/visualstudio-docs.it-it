---
title: "Configuring Targets and Tasks | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configuring Targets and Tasks
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile configurare le destinazioni e le attività di MSBuild per l'esecuzione out\-of\-process con MSBuild, in modo che si possano scegliere come destinazione contesti che differiscono da quello corrente.  Ad esempio, è possibile scegliere come destinazione un'applicazione .NET Framework 2.0 a 32 bit mentre nel computer di sviluppo è in esecuzione un sistema operativo .NET Framework 4.5 a 64 bit.  Inoltre, è possibile scegliere come destinazione computer che utilizzano .NET Framework 4 o versioni precedenti.  La combinazione tra 32 o 64 bit e la versione di .NET Framework specifica viene definito *contesto di destinazione*.  
  
## Installazione  
 Il .NET Framework 4.5 e i 4.5.1 sostituiscono il Common Language Runtime \(CLR\), destinazioni, attività e strumenti di .NET Framework 4 senza rinominarli.  Il .NET Framework 4.5.1 è installato come parte di [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].  
  
 Se si desidera installare separatamente MSBuild da Visual Studio, è possibile scaricare il pacchetto di installazione da [Download di MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745).  È inoltre necessario installare anche le versioni di .NET Framework che si desidera utilizzare.  
  
## Destinazioni e attività  
 MSBuild esegue alcune attività di compilazione out\-of\-process ad un più ampio set di contesti.  Ad esempio, un MSBuild a 32 bit può eseguire un'attività di compilazione in un processo a 64 bit destinato ad un computer a 64 bit.  Questa funzionalità è controllata dagli argomenti `UsingTask` e dai parametri `Task`.  Le destinazioni installate da .NET Framework 4.5 impostano questi argomenti e parametri e non è necessaria alcuna modifica per compilare applicazioni per i vari contesti di destinazione.  
  
 Se si desidera creare un contesto di destinazione, è necessario impostare questi argomenti e parametri in modo appropriato.  Esaminare il file di .NET Framework 4.5 Microsoft.Common.targets ed il file Microsoft.Common.Tasks per gli esempi.  Per informazioni su come creare un'attività personalizzata che può utilizzare contesti di destinazione multipli, o come modificare le attività esistenti, vedere [How to: Configure Targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## Vedere anche  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)