---
title: "Regole di prestazioni per l&#39;utilizzo di .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Regole di prestazioni per l&#39;utilizzo di .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le regole delle prestazioni nella categoria di utilizzo di .NET Framework identificano metodi specifici che è possibile ottimizzare nonché modelli di utilizzo più generali, quali Garbage Collection e conflitti di blocco, che è possibile analizzare per individuare problemi di prestazioni.  
  
|||  
|-|-|  
|[DA0001: Utilizzare StringBuilder per le concatenazioni](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Le chiamate a <xref:System.String.Concat%28System.String%2CSystem.String%29?displayProperty=fullName> sono una percentuale significativa dei dati di profilatura.  Considerare l'utilizzo della classe <xref:System.Text.StringBuilder> per costruire stringhe da più segmenti.|  
|[DA0005: Raccolte GC2 frequenti](../profiling/da0005-frequent-gc2-collections.md)|Un numero relativamente elevato di oggetti di memoria .NET viene recuperato in un'operazione di Garbage Collection di generazione 2.  Se troppi oggetti di breve durata vengono conservati dopo la Garbage Collection di generazione 1, il costo di gestione della memoria può facilmente divenire eccessivo.|  
|[DA0006: Eseguire l'override di Equals\(\) per i tipi di valore](../profiling/da0006-override-equals-parens-for-value-types.md)|Le chiamate al metodo `Equals` o agli operatori di uguaglianza di un tipo di valore pubblico sono una percentuale significativa dei dati di profilatura.  Considerare l'implementazione di un metodo più efficiente.|  
|[DA0007: Evitare di utilizzare eccezioni per il flusso di controllo](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Nei dati di profilatura sono stati chiamati gestori di eccezioni .NET Framework con una frequenza elevata.  Considerare l'utilizzo di un'altra logica del flusso di controllo per ridurre il numero di eccezioni generate.|  
|[DA0010: Funzione GetHashCode dispendiosa](../profiling/da0010-expensive-gethashcode.md)|Le chiamate al metodo `GetHashCode` del tipo costituiscono una percentuale significativa dei dati di profilatura oppure il metodo `GetHashCode` alloca memoria.  Ridurre la complessità del metodo.|  
|[DA0011: Funzione compareTo dispendiosa](../profiling/da0011-expensive-compareto.md)|Il metodo `CompareTo` del tipo è dispendioso o alloca memoria.  Ridurre la complessità del metodo `CompareTo`.|  
|[DA0012: Utilizzo elevato della reflection](../profiling/da0012-significant-amount-of-reflection.md)|Le chiamate ai metodi <xref:System.Reflection?displayProperty=fullName> quali <xref:System.Reflection.IReflect.InvokeMember%2A> e <xref:System.Reflection.IReflect.GetMember%2A> o ai metodi di tipo quali <xref:System.Type.InvokeMember%2A> costituiscono una percentuale significativa dei dati di profilatura.  Quando è possibile, considerare la possibilità di sostituire questi metodi con associazione anticipata ai metodi di assembly dipendenti.|  
|[DA0013: Utilizzo elevato di String.Split\/String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Le chiamate ai metodi <xref:System.String.Split%2A?displayProperty=fullName> o <xref:System.String.Substring%2A> costituiscono una percentuale significativa dei dati di profilatura.  Se si sta verificando l'esistenza di una sottostringa in una stringa, considerare l'utilizzo di <xref:System.String.IndexOf%2A> o <xref:System.String.IndexOfAny%2A>.|  
|[DA0018: Applicazione a 32 bit in esecuzione al limite di memoria gestito dal processo](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|I dati di sistema raccolti durante l'esecuzione della profilatura indicano che gli heap di memoria di .NET Framework hanno quasi raggiunto la dimensione massima consentita per gli heap gestiti in un processo a 32 bit.  Considerare la possibilità di eseguire di nuovo la profilatura utilizzando il metodo di profilatura della memoria di .NET e ottimizzare l'utilizzo delle risorse gestite dall'applicazione.|  
|[DA0021: Frequenza elevata di Garbage Collection di generazione 1](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Un numero relativamente elevato di oggetti di memoria .NET viene recuperato in un'operazione di Garbage Collection di generazione 1.  Se troppi oggetti di breve durata vengono conservati dopo la Garbage Collection di generazione 0, il costo di gestione della memoria può facilmente divenire eccessivo.|  
|[DA0022: Frequenza elevata di Garbage Collection di generazione 2](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Un numero elevato di oggetti di memoria .NET viene recuperato in un'operazione di Garbage Collection di generazione 2.  Se troppi oggetti di breve durata vengono conservati dopo la Garbage Collection di generazione 1, il costo di gestione della memoria può facilmente divenire eccessivo.  Questa regola viene attivata quando la frequenza di conflitti di blocco supera il valore soglia superiore della regola DA0005.|  
|[DA0024: Tempo CPU GC elevato](../profiling/da0023-high-gc-cpu-time.md)|I dati relativi alle prestazioni del sistema raccolti durante la profilatura indicano che la quantità di tempo impiegato nell'operazione di Garbage Collection è significativa rispetto al tempo di elaborazione totale dell'applicazione.|  
|[DA0024: Tempo CPU GC eccessivo](../profiling/da0024-excessive-gc-cpu-time.md)|I dati relativi alle prestazioni di sistema raccolti durante la profilatura indicano che la quantità di tempo impiegato nell'operazione di Garbage Collection risulta eccessivamente alta rispetto al tempo di elaborazione totale dell'applicazione.  Questa regola viene attivata quando la quantità di tempo impiegata per l'operazione di Garbage Collection supera il valore soglia superiore della regola DA0023.|  
|[DA0038: Frequenza elevata di conflitti di blocco](../profiling/da0038-high-rate-of-lock-contentions.md)|I dati relativi alle prestazioni di sistema raccolti con i dati di profilatura indicano che si è verificata una frequenza significativamente elevata di conflitti di blocco durante l'esecuzione dell'applicazione.  Considerare la possibilità di eseguire di nuovo la profilatura utilizzando il metodo di profilatura della concorrenza per individuare la causa dei conflitti.|  
|[DA0039: Frequenza molto elevata di conflitti di blocco](../profiling/da0039-very-high-rate-of-lock-contentions.md)|I dati relativi alle prestazioni di sistema raccolti con i dati di profilatura indicano che si è verificata una frequenza eccessivamente elevata di conflitti di blocco durante l'esecuzione dell'applicazione.  Considerare la possibilità di eseguire di nuovo la profilatura utilizzando il metodo di profilatura della concorrenza per individuare la causa dei conflitti.  Questa regola viene attivata quando la frequenza di conflitti di blocco supera il valore soglia superiore della regola DA0038.|