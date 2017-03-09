---
title: "Procedura: utilizzare la finestra Espressione di controllo in parallelo | Microsoft Docs"
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
  - "vs.debug.parallelwatch"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, espressioni di controllo (finestra parallela)"
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: utilizzare la finestra Espressione di controllo in parallelo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra Espressione di controllo in parallelo è possibile visualizzare contemporaneamente i valori di un'espressione utilizzata in più thread.  Ogni riga rappresenta un thread in esecuzione in un'applicazione, ma un thread può essere rappresentato su più righe.  In particolare, ogni riga rappresenta una chiamata di funzione la cui firma della funzione corrisponde alla funzione nello stack frame corrente.  È possibile ordinare, riordinare, rimuovere e raggruppare gli elementi presenti nelle colonne.  È possibile aggiungere flag, rimuovere flag, bloccare \(sospendere\) e sbloccare \(riprendere\) i thread.  Le colonne seguenti vengono visualizzate nella finestra **Espressione di controllo in parallelo**:  
  
-   Colonna flag, nella quale è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.  
  
-   Colonna frame, in cui una freccia indica il frame selezionato.  
  
-   Colonna configurabile che consente di visualizzare il computer, il processo, la sezione, l'attività e il thread.  
  
    > [!TIP]
    >  È necessario aprire la finestra **Attività in parallelo** per visualizzare le informazioni sulle attività nella finestra **Espressione di controllo in parallelo**.  
  
-   Colonna **\<Aggiungi espressione\>**, in cui è possibile immettere espressioni di controllo.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Per visualizzare la finestra Espressione di controllo in parallelo  
  
1.  Impostare un punto di interruzione nel codice.  
  
2.  Sulla barra dei menu scegliere **Debug**, **Avvia debug**.  Attendere che l'applicazione raggiunga il punto di interruzione.  
  
3.  Sulla barra dei menu scegliere **Debug**, **Windows**, **Espressione di controllo in parallelo** e scegliere una finestra Espressione di controllo.  È possibile aprire un massimo di quattro finestre.  
  
### Per aggiungere un'espressione di controllo  
  
-   Selezionare **\<Aggiungi espressione\>** e specificare un'espressione di controllo.  
  
### Per aggiungere o rimuovere flag che contrassegnano un thread  
  
-   Selezionare la colonna flag per la riga o aprire il menu di scelta rapida relativo e scegliere **Contrassegna** o **Rimuovi flag**.  
  
### Per visualizzare solo i thread con flag  
  
-   Scegliere il pulsante Mostra solo thread con flag nell'angolo superiore sinistro della finestra **Espressione di controllo in parallelo**.  
  
### Per passare da un frame a un altro  
  
-   Fare doppio clic sulla colonna frame. \(tastiera: selezionare la riga e premere INVIO\).  
  
### Per ordinare una colonna  
  
-   Selezionare l'intestazione della colonna.  
  
### Per raggruppare i thread  
  
-   Aprire il menu di scelta rapida per la finestra Espressione di controllo in parallelo, scegliere **Raggruppa**, quindi scegliere la voce del sottomenu appropriata.  
  
### Per bloccare o sbloccare i thread  
  
-   Aprire il menu di scelta rapida per la riga e scegliere **Blocca** o **Sblocca**.  
  
### Per esportare i dati nella finestra Espressione di controllo in parallelo  
  
-   Scegliere il pulsante **Apri in Excel** e scegliere **Apri in Excel** o **Esporta in CSV**.  
  
### Per filtrare in base a un'espressione booleana  
  
-   Immettere un'espressione booleana nella casella **Filtra per espressione booleana**.  Il debugger valuta l'espressione per ogni contesto del thread.  Vengono visualizzate solo le righe in cui valore è `true`.  
  
## Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: utilizzare la finestra Thread GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Procedura dettagliata: Debug di un'applicazione C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)