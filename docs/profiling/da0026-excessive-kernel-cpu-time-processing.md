---
title: "DA0026: Tempo di elaborazione CPU kernel eccessivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0026"
  - "vs.performance.DA0026"
  - "vs.performance.26"
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0026: Tempo di elaborazione CPU kernel eccessivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|TODO|  
|Category|Utilizzo di strumenti di profilatura|  
|Metodo di profilatura|Campionamento|  
|Messaggio|È stato rilevato un elevato livello di tempo CPU in modalità kernel.  Per determinare la causa, abilitare il campionamento SysCall.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## Causa  
 Il tempo CPU proporzionale eseguito in modalità kernel ha superato la quantità di tempo trascorso in modalità utente.  Per determinare la causa degli elevati tempi di esecuzione in modalità kernel, eseguire di nuovo la profilatura e abilitare al campionamento del numero di chiamate di sistema \(syscalls\).  
  
## Descrizione della regola  
 La percentuale relativamente elevata del tempo impiegato dall'applicazione in modalità kernel può giustificare l'esecuzione di ulteriori analisi.  Un'applicazione in modalità utente passa alla modalità kernel per eseguire operazioni di I\/O, per attendere primitive di sincronizzazione di thread o processi o per eseguire chiamate di sistema.  È possibile analizzare i tipi di chiamate di sistema effettuati dall'applicazione e le funzioni responsabili di tali chiamate selezionando l'opzione per raccogliere stack di chiamate campione in base alle chiamate di sistema.  
  
## Come correggere le violazioni  
 Per analizzare i tipi di chiamate di sistema effettuati dall'applicazione, eseguire nuovamente il profilo e selezionare l'opzione per raccogliere campioni in base alle chiamate al sistema.  Se si eseguono gli strumenti di profilatura nell'IDE, vedere [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md) per ulteriori informazioni.  Se si eseguono gli strumenti di profilatura dalla riga di comando, vedere la sezione **Sampling Interval Options** dell'argomento [VSPerfCmd](../profiling/vsperfcmd.md) nei riferimenti agli strumenti di profilatura della riga di comando.