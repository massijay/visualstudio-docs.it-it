---
title: "Procedura: Configurare la riduzione del rumore nelle visualizzazioni report degli strumenti per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.noisereduction.dialog"
helpviewer_keywords: 
  - "strumenti per la profilatura, rimozione"
  - "strumenti per la profilatura, riduzione del rumore nei report"
  - "strumenti per la profilatura, riduzione"
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Configurare la riduzione del rumore nelle visualizzazioni report degli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I rapporti di prestazioni possono essere configurati per la riduzione del rumore limitando la quantità di dati presentati nelle visualizzazioni Struttura ad albero delle chiamate e Allocazione.  Utilizzando la riduzione del rumore, i problemi di prestazioni sono più rilevanti.  In questo modo è più semplice analizzare i rapporti di prestazioni.  
  
 Le opzioni di configurazione della riduzione del rumore includono le seguenti impostazioni:  
  
-   **Trimming** Quando un rapporto viene analizzato, la visualizzazione ometterà le funzioni che rientrano all'interno delle impostazioni di valore e soglia che sono state configuare, come descritto nella procedura di trimming che segue.  Il trimming è abilitato per impostazione predefinita.  
  
-   **Riduzione** Se si abilita la riduzione, le funzioni consecutive su un percorso che soddisfano le impostazioni configurate, verranno unite come descritto nella procedura di riduzione che segue.  La riduzione è abilitata per impostazione predefinita.  
  
### Per configurare il trimming per i report di prestazioni  
  
1.  Nella visualizzazione Struttura ad albero delle chiamate o Allocazione del rapporto generato, dal menu **Sviluppatore** fare clic su **Profiler** quindi fare clic su **Opzioni riduzione rumore**.  
  
     Verrà visualizzata la finestra di dialogo **Riduzione rumore**.  
  
2.  Per attivare il trimming, effettuare queste operazioni:  
  
    1.  Selezionare **Attiva trimming**.  Rappresenta l'impostazione predefinita.  
  
        > [!NOTE]
        >  Se la riduzione del rumore è attivata, una barra informazioni verrà visualizzata nel rapporto.  Per ulteriori informazioni, vedere [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view.md) e [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Configurare l'impostazione del valore utilizzando l'elenco a discesa **Valore** e scegliendo l'impostazione applicabile.  
  
    3.  Configurare l'impostazione di soglia desiderata digitando un valore percentuale nella casella di testo **Soglia**.  
  
    4.  Per attivare l'avviso di riduzione del rumore nel report generato, selezionare **Visualizza avviso se Riduzione rumore è attivato**.  Rappresenta l'impostazione predefinita.  
  
3.  Per disabilitare il trimming, deselezionare **Attiva trimming**.  
  
4.  Fare clic su **OK**.  
  
### Per configurare la riduzione per i report di prestazioni  
  
1.  Dal menu **Sviluppatore** fare clic su **Profiler** quindi fare clic su **Opzioni Riduzione rumore**.  
  
     Verrà visualizzata la finestra di dialogo **Riduzione rumore**.  
  
2.  Per abilitare la riduzione, effettuare queste operazioni:  
  
    1.  Selezionare **Attiva riduzione**.  Rappresenta l'impostazione predefinita.  
  
        > [!NOTE]
        >  Se la riduzione del rumore è attivata, una barra informazioni verrà visualizzata nel rapporto.  Per ulteriori informazioni, vedere [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view.md) e [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Configurare l'impostazione del valore utilizzando l'elenco a discesa **Valore** e scegliendo l'impostazione applicabile.  
  
    3.  Configurare l'impostazione di soglia desiderata digitando un valore percentuale nella casella di testo **Soglia**.  
  
    4.  Per attivare l'avviso di riduzione del rumore nel report generato, selezionare **Visualizza avviso se Riduzione rumore è attivato**.  Rappresenta l'impostazione predefinita.  
  
3.  Per disabilitare la riduzione, deselezionare **Attiva riduzione**.  
  
4.  Fare clic su **OK**.  
  
## Vedere anche  
 [Personalizzazione delle visualizzazioni dei rapporti sugli strumenti di profilatura](../profiling/customizing-performance-tools-report-views.md)   
 [Procedura: Escludere o includere funzioni brevi nella strumentazione](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view.md)   
 [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md)