---
title: "ClickOnce Cache Overview | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Windows applications, ClickOnce deployemtn"
  - "ClickOnce applications, cache"
  - "ClickOnce deployment, cache"
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# ClickOnce Cache Overview
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Qualsiasi applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], installata in locale o disponibile online su un host remoto, viene memorizzata sul computer client nella *cache* delle applicazioni di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La cache di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consiste in un gruppo di sottodirectory nascoste nella directory Impostazioni locali, all'interno della cartella Documents and Settings dell'utente corrente.  In questa cache vengono memorizzati tutti i file dell'applicazione, inclusi assembly, file di configurazione, impostazioni dell'applicazione e degli utenti e directory Dati.  La cache è inoltre responsabile della migrazione della directory Dati dell'applicazione alla versione più recente.  Per ulteriori informazioni sulla migrazione dei dati, vedere [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Fornendo un unico percorso per la memorizzazione delle applicazioni, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente di gestire automaticamente l'installazione fisica di un'applicazione senza richiedere l'intervento dell'utente.  La cache consente inoltre di isolare le applicazioni tenendo separati gli assembly e i file di dati per tutte le applicazioni e le relative versioni.  Ad esempio, quando si aggiorna un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], tale versione e le relative risorse di dati vengono fornite con le rispettive directory nella cache.  
  
## Quota di archiviazione nella cache  
 La quantità di spazio che può essere occupata dalle applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ospitate online è limitata a una quota che definisce la dimensione della cache di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Questa limitazione viene applicata a tutte le applicazioni online dell'utente. Inoltre, un'applicazione online parzialmente attendibile può occupare al massimo metà di questa quota.  Le applicazioni installate non sono soggette ad alcuna limitazione di questo tipo e non vengono considerate nel conteggio del limite della cache.  Per tutte le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nella cache vengono mantenute solo la versione corrente e la precedente versione installata.  
  
 Per impostazione predefinita, nei computer client è prevista una quota di 250 MB per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] online.  I file di dati non vengono considerati ai fini del raggiungimento di questa quota.  Un amministratore di sistema può aumentare o ridurre questa quota su un determinato client modificando la chiave del Registro di sistema HKEY\_CURRENT\_USER\\Software\\Classes\\Software\\Microsoft\\Windows\\CurrentVersion\\Deployment\\OnlineAppQuotaInKB, un valore DWORD in cui la dimensione della cache è espressa in kilobyte.  Ad esempio, per ridurre la dimensione della cache a 50 MB, è necessario impostare questo valore su 51200.  
  
## Vedere anche  
 [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)