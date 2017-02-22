---
title: "Procedura: Specificare l&#39;inizio del file binario | Microsoft Docs"
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
  - "vs.performance.property.itemlaunch"
helpviewer_keywords: 
  - "strumenti per la profilatura, avvio"
  - "strumenti per le prestazioni, avvio"
  - "sessioni di prestazioni, avvio"
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Specificare l&#39;inizio del file binario
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per profilare binari, ad esempio le DLL, è necessario immettere informazioni nella finestra di dialogo **Pagine delle proprietà di \<destinazione\>**.  Queste informazioni indicano dove il progetto DLL può reperire l'applicazione chiamante.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### Per specificare l'eseguibile da avviare  
  
1.  In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul binario di destinazione e quindi scegliere **Proprietà**.  
  
2.  Nella finestra di dialogo **Pagine delle proprietà** fare clic sulle proprietà **Avvio**.  
  
3.  Selezionare la casella di controllo **Eseguire l'override delle impostazioni progetto**.  
  
4.  Nella casella di testo **Eseguibile da avviare** specificare il percorso del file.  
  
5.  Nella casella di testo **Argomenti** specificare gli argomenti necessari per avviare l'applicazione.  
  
6.  Nella casella di testo **Cartella di lavoro** specificare il percorso della directory.  
  
7.  Scegliere **OK**.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)