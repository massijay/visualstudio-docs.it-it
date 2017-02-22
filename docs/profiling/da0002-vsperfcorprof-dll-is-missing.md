---
title: "DA0002: VSPerfCorProf.dll mancante | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0002"
  - "vs.performance.2"
  - "vs.performance.rules.DAVsPerfCorProfMissing"
  - "vs.performance.rules.DA0002"
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0002: VSPerfCorProf.dll mancante
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0002|  
|Category|Utilizzo di strumenti di profilatura|  
|Metodi di profilatura|Esecuzione del profilo mediante gli strumenti della riga di comando VSPerfCmd e VSPerfASPNETCmd|  
|Messaggio|Il file è stato raccolto senza impostare correttamente le variabili di ambiente con VSPerfCLREnv.cmd.  La risoluzione dei simboli per i file binari gestiti potrebbe non essere effettuata.|  
|Tipo regola|Informazioni|  
  
## Causa  
 Il profiler non ha trovato VSPerfCorProf.dll durante l'esecuzione del profilo.  Questo avviso si verifica quando gli strumenti da riga di comando per la raccolta di dati del profiler vengono utilizzati senza lo strumento VSPerfCLREnv.cmd per inizializzare le variabili di ambiente necessarie.  L'avviso può essere attivato anche se un altro profiler è in esecuzione all'avvio degli strumenti di profilatura.  
  
## Descrizione della regola  
 È necessario impostare variabili di ambiente specifiche prima dell'esecuzione della profilatura affinché il profiler risolva i simboli nei file binari di .NET Framework.  Questo avviso indica che lo strumento VSPerfCLREnv.cmd non è stato eseguito prima della raccolta dei dati di profilo.  È possibile che i simboli per i file binari gestiti non vengano risolti.  Per ulteriori informazioni sull'utilizzo degli strumenti di profilo dalla riga di comando, vedere [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## Come correggere le violazioni  
 Quando si profilano applicazioni gestite tramite gli strumenti da riga di comando di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], eseguire lo strumento da riga di comando [VSPerfCLREnv](../profiling/vsperfclrenv.md) prima di avviare la raccolta dei dati.