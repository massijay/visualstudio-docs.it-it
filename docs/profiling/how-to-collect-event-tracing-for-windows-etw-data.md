---
title: "Procedura: Raccogliere dati ETW (Event Tracing for Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.events"
helpviewer_keywords: 
  - "provider di traccia eventi, strumenti per le prestazioni"
  - "strumenti per la profilatura, provider di traccia eventi"
  - "strumenti per le prestazioni, abilitazione di provider di traccia eventi"
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Raccogliere dati ETW (Event Tracing for Windows)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Event Tracing for Windows \(ETW\) è un'efficace funzione di traccia a livello di kernel che consente al profiler di registrare eventi definiti dall'applicazione o kernel.  I dati raccolti dal provider di eventi possono essere visualizzati solo tramite l'opzione \/**Summary:ETW** dello strumento da riga di comando [VSPerfReport](../profiling/vsperfreport.md).  Questo rapporto consente di individuare i punti nell'applicazione in cui si verificano problemi di prestazioni.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### Per attivare i provider di traccia eventi  
  
1.  In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.  
  
2.  In **Pagine delle proprietà** scegliere le proprietà **Eventi Windows**.  
  
3.  Dall'elenco **Selezionare i provider di traccia eventi per raccogliere dati da** scegliere i provider di eventi da utilizzare per l'analisi dell'applicazione.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)