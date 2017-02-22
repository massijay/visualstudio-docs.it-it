---
title: "Finestra Esplora prestazioni | Microsoft Docs"
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
  - "vs.performanceexplorer"
  - "vs.performance.explorer"
helpviewer_keywords: 
  - "strumenti per le prestazioni, Esplora prestazioni"
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Finestra Esplora prestazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La finestra **Esplora prestazioni** nell'ambiente di sviluppo integrato \(IDE\) di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di configurare e avviare sessioni di prestazioni tramite gli Strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## Barra degli strumenti di Esplora prestazioni  
 Sulla barra degli strumenti di **Esplora prestazioni** sono disponibili le seguenti opzioni:  
  
-   **Avvia Creazione guidata sessione di prestazioni** \- Visualizza la Creazione guidata sessione di prestazioni che consente di aggiungere una nuova sessione di prestazioni alla finestra Esplora prestazioni.  
  
-   **Nuova sessione di prestazioni** \- Aggiunge una sessione di prestazioni vuota nella finestra Esplora prestazioni.  
  
-   **Avvia** : l'elenco del pulsante di comando **Avvia** consente di avviare l'applicazione di destinazione con la profilatura immediatamente abilitata \(**Avvio con profilatura**\) o con la profilatura in sospeso **Avvio con profilatura sospeso**.  
  
-   **Metodo** \- Specifica se il metodo di analisi della sessione è campionamento o strumentazione.  
  
-   **Interrompi** \- Chiude immediatamente l'applicazione di destinazione e il profiler.  
  
-   **Connetti\/Disconnetti** \- Visualizza la finestra di dialogo **Connettere profiler a processo** che consente di selezionare un processo in esecuzione a cui connettere il profiler.  
  
## Finestra Esplora prestazioni  
 La finestra **Esplora prestazioni** contiene un controllo struttura ad albero che visualizza i binari e i file di dati dei report di una o più sessioni di prestazioni.  
  
-   **Nome sessione** \- La radice del controllo struttura ad albero contiene il nome della sessione.  Fare clic con il pulsante destro del mouse sul nome della sessione per impostare le proprietà della sessione o avviare il profiler e l'applicazione di destinazione.  
  
-   **Destinazioni** \- Visualizza i nomi dei binari specificati che devono essere profilati nella sessione.  Fare clic con il pulsante destro del mouse su **Destinazioni** per aggiungere o rimuovere un binario, un progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o un sito Web.  Fare clic con il pulsante destro del mouse su un nome di destinazione per impostare le proprietà per il singolo binario.  
  
-   **Report** \- Visualizza i nomi dei file di dati del profiler generati per la sessione.  Fare clic con il pulsante destro del mouse su **Report** per aggiungere un report esistente o confrontare due file di dati del profiler.  Fare clic con il pulsante destro del mouse su un nome di report per aprire, rimuovere o esportare un file di dati del profiler.  
  
## Vedere anche  
 [Cenni preliminari](../profiling/overviews-performance-tools.md)   
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)