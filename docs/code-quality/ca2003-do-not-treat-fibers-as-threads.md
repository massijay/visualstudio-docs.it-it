---
title: "CA2003: Non considerare i fiber come i thread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
helpviewer_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2003: Non considerare i fiber come i thread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotTreatFibersAsThreads|  
|CheckId|CA2003|  
|Category|Microsoft.Reliability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un thread gestito viene considerato come thread Win32.  
  
## Descrizione della regola  
 Non presupporre che un thread gestito sia un thread Win32.  È un fiber.  In CLR \(Common Language Runtime\) verranno eseguiti thread gestiti come fiber nel contesto dei thread reali gestiti da SQL.  Tali thread possono essere condivisi in AppDomains e persino nei database nell'elaborazione di SQL Server.  L'utilizzo dell'archiviazione locale dei thread gestiti funzionerà, ma potrebbe non essere possibile utilizzare tale sistema né supporre che il codice verrà eseguito nuovamente sul thread del sistema operativo corrente.  Non modificare impostazioni quali le impostazioni locali del thread.  Non chiamare CreateCriticalSection o CreateMutex tramite P\/Invoke perché richiedono che il thread che accede a un blocco esca anche da tale blocco.  Poiché questo caso non si verificherà quando si utilizzano i fiber, i mutex e le sezioni critiche di Win32 risulteranno inutili in SQL.  È possibile che si utilizzi in modo sicuro la maggior parte dello stato su un oggetto System.Thread gestito.  Sono incluse l'archiviazione locale del thread gestito e le impostazioni cultura dell'interfaccia utente \(IU\) correnti del thread.  Tuttavia, per motivi legati al modello di programmazione, non sarà possibile modificare le impostazioni di cultura correnti di un thread se si esegue SQL; ciò verrà imposto tramite una nuova autorizzazione.  
  
## Come correggere le violazioni  
 Esaminare l'utilizzo di thread e modificare il codice di conseguenza.  
  
## Esclusione di avvisi  
 Non escludere tale regola.