---
title: "Procedura: Specificare opzioni di strumentazione aggiuntive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.advanced"
helpviewer_keywords: 
  - "strumentazione, opzioni"
  - "strumenti per la profilatura, opzioni sessione"
  - "sessioni di prestazioni, opzioni"
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura: Specificare opzioni di strumentazione aggiuntive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile instrumentare i binari dall'ambiente di sviluppo integrato \(IDE\) di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] o mediante gli strumenti della riga di comando.  Nel primo caso è possibile controllare il volume dei dati raccolti durante la strumentazione mediante la specifica di opzioni di strumentazione aggiuntive nello strumento [VSInstr](../profiling/vsinstr.md).  Tali opzioni sono disponibili a livello di sessione o di destinazione.  Per includere o escludere funzioni specifiche durante il processo di strumentazione, è ad esempio possibile utilizzare l'opzione di strumentazione aggiuntiva a livello di destinazione.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!IMPORTANT]
>  Ogni controlli inserito modifica leggermente il comportamento del programma originale  causando un sovraccarico in fase di analisi.  Sebbene un'approssimazione di tale sovraccarico venga sottratta, si verificano comunque effetti minimi in termini di tempo sulle applicazioni multithreading.  Le opzioni dello strumento [VSInstr](../profiling/vsinstr.md) consentono di controllare la raccolta dei dati durante la creazione dei profili.  
  
### Per specificare un'opzione di strumentazione aggiuntiva  
  
1.  In **Esplora prestazioni** selezionare la **Sessione prestazioni** e quindi fare clic con il pulsante destro del mouse e scegliere **Proprietà**.  
  
2.  In **Pagine delle proprietà** scegliere le proprietà della scheda **Avanzate**.  
  
3.  Digitare le opzioni nella casella **Opzioni di strumentazione aggiuntive**.  
  
     Ad esempio, utilizzare \/CONTROL:THREAD per specificare il livello di analisi.  Per un elenco completo di opzioni, vedere [VSInstr](../profiling/vsinstr.md).  
  
4.  Fare clic su **OK**.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)