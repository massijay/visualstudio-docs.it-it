---
title: "Regole di utilizzo degli strumenti di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Regole di utilizzo degli strumenti di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le regole delle prestazioni nella categoria di utilizzo degli strumenti di profilatura forniscono indicazioni sull'utilizzo del profiler per una raccolta più efficiente dei dati.  
  
|||  
|-|-|  
|[DA0002: VSPerfCorProf.dll mancante](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|La profilatura dalla riga di comando può contenere dati incompleti per i file binari di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Questa situazione può essere causata dalla mancata impostazioni delle variabili di ambiente corrette.|  
|[DA0003: Numero elevato di campioni del kernel](../profiling/da0003-many-kernel-samples.md)|Sono stati registrati molti esempi di profilatura che si sono verificati all'esterno dell'esecuzione del binario di destinazioni.  Per raccogliere dati più accurati, considerare l'utilizzo del metodo di strumentazione.|  
|[DA0004: Utilizzo elevato del processore](../profiling/da0004-high-processor-usage.md)|I dati di profilatura indicano che i processori sono stati occupati in modo costante durante l'esecuzione della profilatura.  Per raccogliere dati più accurati, considerare l'utilizzo del metodo di campionamento.|  
|[DA0008: Numero ridotto di campioni raccolti](../profiling/da0008-few-samples-collected.md)|Il numero di campioni raccolti nell'esecuzione della profilatura non è sufficiente per essere statisticamente significativo.  Valutare di eseguire nuovamente la profilatura mantenendo l'applicazione in esecuzione per un periodo di tempo maggiore.  Considerare inoltre l'utilizzo del metodo di strumentazione per la raccolta dei dati.|  
|[DA0026: Tempo di elaborazione CPU kernel eccessivo](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|L'esecuzione della profilatura in modalità kernel del processore ha richiesto un periodo di tempo notevole.  Considerare di eseguire il campionamento utilizzando v le chiamate di sistema anziché il tempo.|  
|[DA0029: Versione CLR non supportata](../profiling/da0029-unsupported-clr-version.md)|Il file binario profilato utilizza una versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] non supportata dal profiler.  Il profiler indica che non è possibile risolvere i nomi dei simboli.|  
|[DA0030: Raccogli misurazioni di interazione tra livelli per i progetti di database](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|È stato raccolto un numero notevole di chiamate ai metodi nello spazio dei nomi <xref:System.Data?displayProperty=fullName>.  Per includere dati sulle chiamate di database, considerare la raccolta dei dati sull'interazione tra livelli nelle esecuzioni di profilatura.|