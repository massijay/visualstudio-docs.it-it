---
title: "Procedura: utilizzare la finestra Thread GPU | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.gputthreads"
  - "vs.debug.gputhreads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, GPU (finestra dei thread)"
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: utilizzare la finestra Thread GPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra Thread GPU è possibile esaminare e utilizzare i thread in esecuzione nella GPU nell'applicazione sottoposta a debug.  Per ulteriori informazioni sulle applicazioni eseguite nella GPU, vedere [Cenni preliminari su C\+\+ AMP](/visual-cpp/parallel/amp/cpp-amp-overview).  
  
 La finestra Thread GPU contiene una tabella in cui ogni riga rappresenta un set di thread GPU che hanno gli stessi valori in tutte le colonne.  È possibile ordinare, riordinare, rimuovere e raggruppare gli elementi presenti nelle colonne.  È possibile contrassegnare, rimuovere i flag, bloccare \(sospendere\) e sbloccare \(riprendere\) i thread dalla finestra Thread GPU.  Le colonne seguenti sono visualizzate nella finestra Thread GPU:  
  
-   Colonna flag, nella quale è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.  
  
-   Colonna del thread attivo, nella quale una freccia gialla indica un thread attivo.  Una freccia indica un thread nel quale l'esecuzione si è interrotta nel debugger.  
  
-   Colonna **Conteggio thread**, che visualizza il numero di thread nella stessa posizione.  
  
-   Colonna **Riga** che visualizza la riga di codice in cui si trova ciascun gruppo di thread.  
  
-   Colonna **Indirizzo** che visualizza l'indirizzo dell'istruzione in cui si trova ciascun gruppo di thread.  Per impostazione predefinita, questa colonna è nascosta.  
  
-   Colonna **Posizione**, che indica la posizione nel codice sorgente.  
  
-   Colonna **Stato**, che indica se il thread è attivo, bloccato, non avviato o completo.  
  
-   Colonna **Sezione**, che indica l'indice della sezione per i thread nella riga.  
  
 Nell'intestazione della tabella sono indicati il riquadro e il thread visualizzati.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Per visualizzare la finestra Thread GPU  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e scegliere **Proprietà**.  
  
2.  Nella finestra **Pagine delle proprietà** per il progetto, in **Proprietà di configurazione** scegliere **Debug**.  
  
3.  Nell'elenco **Debugger da avviare** selezionare **Debugger Windows locale**.  Nell'elenco **Tipo di debugger** selezionare **Solo GPU**.  È necessario scegliere questo debugger per l'interruzione in corrispondenza dei punti di interruzione nel codice in esecuzione sulla GPU.  
  
4.  Fare clic sul pulsante **OK**.  
  
5.  Impostare un punto di interruzione nel codice della GPU.  
  
6.  Sulla barra dei menu scegliere **Debug**, **Avvia debug**.  Attendere che l'applicazione raggiunga il punto di interruzione.  
  
7.  Nella barra dei menu scegliere **Debug**, **Windows**, **Thread GPU**.  
  
### Per passare a un altro thread attivo  
  
-   Fare doppio clic sulla colonna. Sulla tastiera selezionare la riga e premere INVIO.  
  
### Per visualizzare un riquadro e un thread specifici  
  
1.  Scegliere il pulsante **Espandi selezione thread** nella finestra Thread GPU.  
  
2.  Immettere i valori del riquadro e del thread nelle caselle di testo.  
  
3.  Scegliere il pulsante con la freccia.  
  
### Per visualizzare o nascondere una colonna  
  
-   Aprire il menu di scelta rapida per la finestra Thread GPU, scegliere **Colonne**, quindi scegliere la colonna da visualizzare o nascondere.  
  
### Per ordinare per colonna  
  
-   Selezionare l'intestazione della colonna.  
  
### Per raggruppare i thread  
  
-   Aprire il menu di scelta rapida per la finestra Thread GPU, scegliere **Raggruppa**, quindi scegliere uno dei nomi di colonna visualizzati.  Scegliere **Nessuno** per separare i thread.  
  
### Per bloccare o sbloccare una riga di thread  
  
-   Aprire il menu di scelta rapida per la riga e scegliere **Blocca** o **Sblocca**.  
  
### Per contrassegnare o rimuovere il flag da una riga di thread  
  
-   Selezionare la colonna dei flag per il thread o aprire il menu di scelta rapida per il thread e scegliere **Contrassegna** o **Rimuovi flag**.  
  
### Per visualizzare solo i thread con flag  
  
-   Scegliere il pulsante del flag nella finestra Thread GPU.  
  
## Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: utilizzare la finestra Espressione di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Procedura dettagliata: Debug di un'applicazione C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)