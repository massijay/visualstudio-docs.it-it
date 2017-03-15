---
title: "CA2006: Utilizzare SafeHandle per incapsulare le risorse native | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2006"
  - "UseSafeHandleToEncapsulateNativeResources"
helpviewer_keywords: 
  - "UseSafeHandleToEncapsulateNativeResources"
  - "CA2006"
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2006: Utilizzare SafeHandle per incapsulare le risorse native
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|Category|Microsoft.Reliability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Il codice gestito utilizza <xref:System.IntPtr> per accedere alle risorse native.  
  
## Descrizione della regola  
 L'utilizzo di `IntPtr` nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità.  Tutte le occorrenze di `IntPtr` devono essere esaminate per stabilire se al loro posto è necessario utilizzare <xref:System.Runtime.InteropServices.SafeHandle> o una tecnologia simile.  Si verificheranno problemi nel caso in cui `IntPtr` rappresenti risorse native quali memoria, handle di file, socket a cui si considera che appartenga il codice gestito.  Se il codice gestito possiede la risorsa, è necessario rilasciare anche le risorse native a esso associate, poiché una mancata riuscita di tale operazione determinerebbe la perdita della risorsa.  
  
 In scenari di questo tipo si verificheranno anche problemi di sicurezza o affidabilità nel caso in cui sia consentito l'accesso multithread a `IntPtr` e sia fornito un sistema per il rilascio della risorsa rappresentato da `IntPtr`.  Tali problemi riguardano il riciclo del valore `IntPtr` sul rilascio della risorsa mentre in un altro thread la risorsa viene utilizzata contemporaneamente.  Questo può determinare race condition nel caso in cui un thread sia in grado di leggere o scrivere dati associati alla risorsa sbagliata.  Se nel tipo, ad esempio, è memorizzato un handle del sistema operativo come `IntPtr` e viene consentito agli utenti di chiamare **Close** e qualsiasi altro metodo che utilizza tale handle simultaneamente e senza alcun tipo di sincronizzazione, il codice presenterà un problema di riciclo dell'handle.  
  
 Questo problema di riciclo dell'handle può causare il danneggiamento dei dati e, spesso, una vulnerabilità di sicurezza.  `SafeHandle` e la classe di pari livello <xref:System.Runtime.InteropServices.CriticalHandle> forniscono un meccanismo per incapsulare un gestore nativo in una risorsa, in modo da evitare tali problemi di threading.  È inoltre possibile utilizzare `SafeHandle` e la relativa classe `CriticalHandle` di pari livello per altri problemi di threading, ad esempio per controllare con attenzione la durata degli oggetti gestiti che contengono una copia del gestore nativo nelle chiamate ai metodi nativi.  In questa situazione è spesso possibile rimuovere le chiamate a `GC.KeepAlive`.  Il sovraccarico delle prestazioni che si verifica durante l'utilizzo di `SafeHandle` e, a livello inferiore, di `CriticalHandle`, può spesso essere ridotto attraverso un'attenta progettazione.  
  
## Come correggere le violazioni  
 Convertire l'utilizzo di `IntPtr` in `SafeHandle` per gestire in modo sicuro l'accesso alle risorse native.  Per esempi vedere l'argomento di riferimento <xref:System.Runtime.InteropServices.SafeHandle>.  
  
## Esclusione di avvisi  
 Non escludere tale avviso.  
  
## Vedere anche  
 <xref:System.IDisposable>