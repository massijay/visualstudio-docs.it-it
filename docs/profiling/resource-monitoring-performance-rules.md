---
title: "Regole di prestazioni relative al monitoraggio delle risorse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Regole di prestazioni relative al monitoraggio delle risorse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I messaggi sulle prestazioni nella categoria monitoraggio risorse offrono dati aggiuntivi sulle prestazioni dell'applicazione.  È possibile utilizzare questi dati per analizzare i problemi di prestazioni.  Queste regole sono informative e riportano ogni esecuzione della profilatura.  
  
|||  
|-|-|  
|[DA0501: Consumo medio CPU del processo sottoposto a profilatura.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|In questo messaggio viene indicata la percentuale di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione.  Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo profilato era attivo.|  
|[DA0502: Consumo massimo CPU del processo sottoposto a profilatura](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|In questo messaggio viene indicata la percentuale massima di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione.  Il valore indicato è il valore massimo segnalato fra tutti gli intervalli di misurazione nei quali il processo profilato era attivo.|  
|[DA0503: Working set medio in byte del processo sottoposto a profilatura](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Questo messaggio indica la quantità media di memoria fisica, in byte, utilizzata dal processo mentre era attiva la profilatura.  Questa misura di memoria fisica è denominata working set.|  
|[DA0504: Working set massimo in byte del processo sottoposto a profilatura](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Questo messaggio indica la quantità massima di memoria fisica, in byte, utilizzata dal processo mentre era attiva la profilatura.|  
|[DA0505: Byte privati medi allocati per il processo sottoposto a profilatura](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Questo messaggio indica la quantità media di memoria virtuale, in byte, allocata dal processo mentre era attiva la profilatura.  Questa misura di memoria virtuale è denominata *byte privati*.  I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.|  
|[DA0506: Byte privati massimi allocati per il processo sottoposto a profilatura](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Questo messaggio indica la quantità massima di memoria virtuale, allocata in byte privati dal processo mentre era attiva la profilatura.|