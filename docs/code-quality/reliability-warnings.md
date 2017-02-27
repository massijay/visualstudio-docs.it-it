---
title: "Avvisi di affidabilit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.reliabilityrules"
helpviewer_keywords: 
  - "avvisi, affidabilità"
  - "avvisi di affidabilità"
  - "avvisi dell'analisi del codice gestito, avvisi di affidabilità"
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# Avvisi di affidabilit&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di affidabilità supportano l'affidabilità di librerie e applicazioni, ad esempio l'utilizzo corretto di memoria e thread.  
  
## In questa sezione  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA2000: Eliminare gli oggetti prima di perdere l'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Poiché è possibile che si verifichi un evento eccezionale che impedisca l'esecuzione del finalizzatore di un oggetto, è opportuno eliminare in modo esplicito l'oggetto prima che tutti i riferimenti a tale oggetto siano esterni all'ambito.|  
|[CA2001: Evitare le chiamate a metodi problematici](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Un membro chiama un metodo potenzialmente pericoloso o problematico.|  
|[CA2002: Non bloccare oggetti con identità debole](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione.  Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto.|  
|[CA2003: Non considerare i fiber come i thread](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un thread gestito viene considerato come thread Win32.|  
|[CA2004: Rimuovere le chiamate a GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Se si effettua la conversione all'utilizzo di SafeHandle, rimuovere tutte le chiamate a GC.KeepAlive \(oggetto\).  In questo caso non sarebbe necessario per le classi chiamare GC.KeepAlive, presupponendo che non dispongano di un finalizzatore ma si affidino a SafeHandle per finalizzare l'handle OS al loro posto.|  
|[CA2006: Utilizzare SafeHandle per incapsulare le risorse native](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|L'utilizzo di IntPtr nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità.  Tutte le occorrenze di IntPtr devono essere esaminate per stabilire se al loro posto è necessario utilizzare SafeHandle o una tecnologia simile.|