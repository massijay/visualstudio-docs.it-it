---
title: "QueryCounters | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# QueryCounters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **QueryCounters** elenca i contatori di prestazioni \(hardware\) della CPU disponibili nel computer.  
  
 **QueryCounters** deve essere l'unica opzione specificata nella riga di comando.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### Parametri  
 Nessuno  
  
## Note  
 Quando si utilizza il metodo di strumentazione, il profiler può raccogliere i valori di uno o più contatori di prestazioni della CPU a ogni evento di raccolta dei dati.  Quando si utilizza il metodo di profilo campione, è possibile specificare un evento di contatore e il numero di occorrenze dell'evento da utilizzare come intervallo di campionamento.  
  
 Processori diversi espongono contatori di prestazioni della CPU diversi.  Il profiler definisce un set di contatori generici che può essere utilizzato in quasi tutti i processori.  L'opzione **QueryCounters** elenca sia i nomi dei contatori generici sia i nomi dei contatori specifici del processore.  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)