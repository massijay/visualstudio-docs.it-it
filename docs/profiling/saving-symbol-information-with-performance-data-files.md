---
title: "Salvataggio delle informazioni sui simboli con i file di dati di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "packsymbols, in report degli strumenti per la profilatura"
  - "strumenti per la profilatura, packsymbols"
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Salvataggio delle informazioni sui simboli con i file di dati di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si utilizza l'ambiente di sviluppo integrato \(IDE\) di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per analizzare i file e si intende spostare il file VSP in un altro computer, è necessario configurare le impostazioni del progetto relative alle prestazioni per salvare o *serializzare* i simboli nel file di rapporto.  In questo modo viene incrementata la dimensione di un file di rapporto.  La serializzazione dei simboli è necessaria per due motivi:  
  
-   Per incorporare i simboli del codice in un rapporto di prestazioni prima che gli assembly di destinazione vadano persi dal loro percorso di archiviazione temporanea.  
  
-   Per conservare i simboli in modo che il rapporto di prestazioni sia portabile dal computer profilato e restituisca le stesse informazioni se viene aperto per l'analisi su un altro computer che potrebbe avere simboli diversi.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 È possibile serializzare i simboli dall'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o dalla riga di comando.  
  
-   Per serializzare simboli nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], scegliere **Strumenti** sulla barra dei menu, quindi fare clic su **Opzioni**.  Nella finestra **Opzioni** selezionare **Strumenti di prestazioni** quindi selezionare la casella di controllo **Serializzare automaticamente le informazioni sui simboli**.  
  
-   PACKSYMBOLS è l'opzione della riga di comando equivalente per salvare file di report.  Per serializzare i simboli, digitare vsperfreport \/summary:all \/packsymbols filename.vsp.  
  
## Risoluzione dei problemi relativi ai simboli  
 Se non viene visualizzato alcun simbolo nel codice, sono disponibili alcune soluzioni comuni:  
  
-   Eseguire vsperfreport \/debugsympath dalla riga di comando per visualizzare un elenco completo delle posizioni in cui i componenti del profiler caricano le informazioni sui simboli e verificare se i file dei simboli utilizzati corrispondono ai file utilizzati dal progetto.  
  
-   Assicurarsi di eseguire vsperfreport con il flag \/PACKSYMBOLS o di aver selezionato nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'opzione di serializzazione delle informazioni sui simboli nelle opzioni generali di Esplora prestazioni.  
  
-   Se si raccolgono dati tipo, aggiungere \/SUMMARY:TYPE alla riga di comando vsperfreport.  
  
 Se i simboli non vengono visualizzati da Windows o da altri programmi Microsoft:  
  
-   Verificare di aver impostato il percorso della cache dei simboli di Windows.  Per impostare il percorso della cache dei simboli, eseguire una delle operazioni seguenti:  
  
    -   Impostare l'opzione Debugger\-\>Simboli nell'IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sul percorso corretto.  
  
    -   Aggiungere l'opzione \-symbolpath alla riga di comando di VSPerfReport per includere i simboli.  
  
-   Se in [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non viene visualizzato alcun simbolo, assicurarsi che il server dei simboli sia configurato correttamente per il server ASP.  
  
## Ricompressione dei simboli  
 Per comprimere nuovamente i simboli in un report, è possibile utilizzare lo strumento della riga di comando Vsperfreport.  Utilizzare le seguenti righe di comando:  
  
 Vsperfreport \- clearpackedsymbols nomefile.vsp  
  
 Vsperfreport \- packsymbols \- summary:all nomefile.vsp  
  
## Vedere anche  
 [Salvataggio ed esportazione dei dati degli strumenti per le prestazioni](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)