---
title: "Visualizzazione Thread (prestazioni in parallelo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.threadblocking"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, visualizzazione Thread (prestazioni in parallelo)"
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Visualizzazione Thread (prestazioni in parallelo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visualizzazione thread è la visualizzazione più dettagliata e avanzata disponibile nel visualizzatore della concorrenza.  Tramite questa visualizzazione, è possibile identificare se i thread sono in esecuzione o bloccati a causa di operazioni di sincronizzazione o di I\/O o per altri motivi.  
  
 Durante l'analisi del profilo vengono esaminati, tramite il visualizzatore della concorrenza, tutti gli eventi context\-switch del sistema operativo per ciascun thread di un'applicazione.  I cambi di contesto possono verificarsi per molti motivi, ad esempio questi:  
  
-   Un thread è bloccato su una primitiva di sincronizzazione.  
  
-   Il quantum di un thread scade.  
  
-   Un thread esegue una richiesta di I\/O del blocco.  
  
 Nella visualizzazione thread viene assegnata una categoria a ogni cambio di contesto quando l'esecuzione di un thread si arresta.  Le categorie vengono visualizzate nella legenda nella parte inferiore sinistra della visualizzazione.  Il visualizzatore della concorrenza classifica gli eventi context\-switch tramite la ricerca dello stack di chiamate del thread per API di blocco conosciute.  Se non viene rilevata alcuna corrispondenza dello stack di chiamate, il motivo di attesa fornito da [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] viene utilizzato.  Tuttavia, la categoria [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] può essere basata su un dettaglio implementativo e può non riflettere lo scopo dell'utente.  Ad esempio, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] indica il motivo dell'attesa per bloccare il blocco in lettura\-scrittura nativo come I\/O anziché come sincronizzazione.  Nella maggior parte dei casi, è possibile identificare la causa radice di un evento di blocco esaminando gli stack di chiamate che corrispondono agli eventi di cambio di contesto.  
  
 Nella visualizzazione thread vengono inoltre mostrate le dipendenze tra thread.  Ad esempio, se si identifica un thread bloccato su un oggetto di sincronizzazione, è possibile trovare il thread che lo ha sbloccato, e sarà possibile analizzare l'attività nello stack di chiamate per il thread nel punto in cui ha sbloccato l'altro.  
  
 Quando i thread sono in esecuzione, il visualizzatore della concorrenza raccoglie esempi.  Nella visualizzazione thread, è possibile analizzare quale codice viene eseguito da uno o più thread durante il segmento di esecuzione.  È inoltre possibile esaminare i rapporti di blocco e i rapporti che profilano l'esecuzione della struttura ad albero dello stack di chiamate.  
  
## Utilizzo  
 Ecco alcuni metodi con cui è possibile utilizzare la visualizzazione thread:  
  
-   Identificazione dei motivi per cui l'interfaccia utente di un'app non risponde durante alcune fasi di esecuzione.  
  
-   Identificazione della quantità di tempo trascorso in un blocco dovuto a sincronizzazione, operazioni di I\/O, errori di pagina e altri eventi.  
  
-   Identificazione del grado di interferenza da altri processi in esecuzione nel sistema.  
  
-   Identificazione dei problemi di bilanciamento del carico per l'esecuzione parallela.  
  
-   Identificazione delle cause di scalabilità non ottimale o assente, ad esempio i motivi per cui le prestazioni di un'app parallela non migliorano quando sono disponibili più core logici.  
  
-   Individuazione del livello di concorrenza nell'app, per agevolare la parallelizzazione.  
  
-   Individuazione delle dipendenze tra thread di lavoro e percorsi critici di esecuzione.  
  
## Analisi dei thread e degli intervalli di tempo specifico  
 La visualizzazione dei thread mostra una sequenza temporale.  È possibile ingrandire e scorrere all'interno della sequenza temporale per esaminare gli intervalli specifici e i thread dell'applicazione.  Sull'asse x viene rappresentato il tempo mentre sull'asse y vi sono diversi canali:  
  
-   Due canali I\/O per ogni unità disco nel sistema, un canale per la lettura e uno per la scrittura.  
  
-   Un canale per ciascun thread nel processo.  
  
-   Canali del marcatore, se ci sono eventi del marcatore nella traccia.  I canali del marcatore vengono inizialmente visualizzati nei canali di thread che hanno generato questi eventi.  
  
-   Canali della GPU  
  
 Di seguito è riportata una descrizione della visualizzazione thread:  
  
 ![Visualizzazione thread](~/docs/profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
Visualizzazione Thread  
  
 Inizialmente i thread sono disposti nell'ordine in cui vengono creati, in modo che il thread dell'applicazione principale sarà il primo.  È possibile utilizzare l'opzione di ordinamento presente nell'angolo superiore sinistro della visualizzazione per ordinare i thread in base a un altro criterio \(ad esempio, secondo i thread che svolgono la maggior quantità di lavoro di esecuzione\).  
  
 Successivamente, è quindi possibile nascondere i thread che non stanno eseguendo alcun lavoro selezionandone i nomi nella colonna a sinistra e scegliendo il bottone **Nasconde i thread selezionati** nella barra degli strumenti.  È consigliabile disattivare i thread che sono completamente bloccati perché le relative statistiche sono irrilevanti e potrebbero intasare i rapporti.  
  
 Per identificare thread aggiuntivi da nascondere, nella legenda attiva, scegliere il rapporto **Riepilogo per thread** nella scheda **Rapporto profili**.  Verrà visualizzato il grafico Suddivisione esecuzione, che indica lo stato dei thread per l'intervallo di tempo attualmente selezionato.  A determinati livelli di zoom, alcuni thread potrebbero non essere visualizzati.  In questo caso, vengono visualizzati dei puntini di sospensione sulla destra.  
  
 Dopo aver selezionato un intervallo di tempo e di alcuni thread in esso contenuti, è possibile avviare l'analisi delle prestazioni.  
  
## Strumenti di analisi  
 Questa sezione descrive i report e altri strumenti di analisi.  
  
### Dettagli sul blocco dei thread  
 Per ottenere informazioni su un evento di blocco in una particolare area di un thread, posizionare il puntatore in tale area per visualizzare una descrizione dei comandi.  Contiene informazioni come categoria,l'ora di inizio dell'area, la durata del blocco e un'API di blocco se presente.  Selezionando l'area del blocco, lo stack a quel momento viene visualizzato nel riquadro inferiore, insieme alle stesse informazioni visualizzate nella descrizione del comando.  Esaminando lo stack di chiamate, è possibile determinare la ragione sottostante per l'evento di blocco del thread.  È possibile ottenere informazioni aggiuntive sui thread e sui processi selezionando il segmento ed esaminando la Scheda corrente.  
  
 Un percorso di esecuzione potrebbe avere più eventi di blocco.  È possibile esaminare questi per categoria di blocco in modo da trovare più rapidamente le aree problematiche.  È sufficiente scegliere una delle categorie di blocco nella legenda sulla sinistra.  
  
### Dipendenze tra thread  
 Il visualizzatore della concorrenza può visualizzare le dipendenze tra thread nel processo in modo da stabilire cosa sta tentando di eseguire un thread bloccato e ottenere informazioni su quale altro thread ne ha abilitato l'esecuzione.  Per determinare quale thread ha sbloccato un altro thread, selezionare il segmento di blocco attinente.  Se il visualizzatore della concorrenza è in grado di determinare il thread di sblocco, disegna una linea tra il thread di sblocco e il segmento di esecuzione che segue il segmento di blocco.  Inoltre, la scheda **Stack di sblocco** mostra lo stack di chiamate attinente.  
  
### Dettagli sull'esecuzione dei thread  
 Nel grafico della sequenza temporale di un thread, i segmenti verdi mostrano quando stava eseguendo codice.  È possibile ottenere ulteriori informazioni su un segmento di esecuzione.  
  
 Quando si seleziona un punto in un segmento di esecuzione, il visualizzatore della concorrenza cerca il punto nello stack di chiamate attinente e successivamente visualizza un cursore nero sopra il punto selezionato nel segmento di esecuzione e lo stesso stack di chiamate viene visualizzato nella scheda **Stack corrente**.  È possibile selezionare più punti nel segmento di esecuzione.  
  
> [!NOTE]
>  Il visualizzatore di concorrenza potrebbe non essere in grado di risolvere una selezione in un segmento di esecuzione.  In genere, ciò si verifica quando la durata del segmento è inferiore ad un millisecondo.  
  
 Per ottenere un profilo di esecuzione per tutti i thread abilitati \(non nascosti\) nell'intervallo di tempo attualmente selezionato, scegliere il pulsante **Esecuzione** nella legenda attiva.  
  
### Grafico cronologia  
 Nel grafico della sequenza temporale viene mostrata l'attività di tutti i thread nel processo e di tutti i dispositivi disco fisici nel computer host.  Visualizza inoltre l'attività della GPU e gli eventi del marcatore.  È possibile eseguire lo zoom in per visualizzare ulteriori dettagli o zoom out per visualizzare un intervallo di tempo più lungo.  È inoltre possibile selezionare dei punti nel grafico per ottenere dettagli sulle categorie, i tempi di avvio, le durate e gli stati dello stack di chiamate.  
  
 Nel grafico della sequenza temporale, un colore indica lo stato di un thread in un determinato momento.  I segmenti verdi, ad esempio, erano in esecuzione, i segmenti rossi erano bloccati per la sincronizzazione, i segmenti gialli erano stati superati e quelli viola erano impegnati in attività di I\/O del dispositivo.  È possibile utilizzare questa visualizzazione per esaminare il bilanciamento del lavoro tra thread impegnati in un ciclo parallelo o in attività simultanee.  Se un thread sta richiedendo più tempo per completare degli altri, il lavoro potrebbe essere sbilanciato.  È possibile utilizzare queste informazioni per migliorare le prestazioni del programma distribuendo il lavoro più uniformemente tra i thread.  
  
 Se in quel momento un solo thread è verde \(in esecuzione\), l'app potrebbe non sfruttare completamente la concorrenza nel sistema.  È possibile utilizzare il grafico della sequenza temporale per esaminare le dipendenze tra thread e le relazioni temporali tra i thread di blocco e quelli bloccati.  Per riordinare i thread, selezionare un thread e quindi sulla barra degli strumenti, scegliere il pulsante verso l'alto o verso il basso.  Per nascondere i thread, selezionarli e quindi scegliere il pulsante **Nascondi thread**.  
  
### Rapporti Profilo  
 Il grafico della sequenza temporale seguente è un profilo della sequenza temporale e un riquadro con schede per vari rapporti.  I rapporti si aggiornano automaticamente non appena si cambia la Visualizzazione thread.  Per le grandi analisi, il riquadro dei rapporti potrebbe non essere disponibile mentre gli aggiornamenti vengono calcolati.  Ogni rapporto dispone di due opzioni di filtro: riduzione rumore e Solo codice utente.  Utilizzare riduzione rumore per filtrare voci della struttura ad albero delle chiamate in cui la quantità di tempo impiegato è limitata.  Il valore predefinito del filtro è 2%, ma può essere modificato impostando qualsiasi valore compreso tra 0% e 99%.  Per visualizzare solo la struttura ad albero delle chiamate per il codice, selezionare la casella di controllo **Just My Code**.  Per visualizzare tutte le strutture ad albero delle chiamate, deselezionala.  
  
#### Rapporto Profilo  
 Questa scheda mostra i rapporti corrispondenti alle voci nella legenda attiva.  Per visualizzare un report, scegliere una delle voci.  
  
#### Stack corrente  
 Questa scheda mostra lo stack di chiamate per un punto su un segmento di thread selezionato nei grafico della sequenza temporale.  Gli stack di chiamate vengono tagliati per mostrare solamente l'attività correlata al programma.  
  
#### Stack di sblocco  
 Per controllare quale thread ha sbloccato il thread selezionato, e in quale riga di codice, scegliere la scheda **Stack di sblocco**.  
  
#### Esecuzione  
 Il rapporto di esecuzione mostra la distribuzione del tempo dell'applicazione in esecuzione.  
  
 Per trovare la riga di codice in cui è trascorso il tempo di esecuzione, espandere la struttura ad albero delle chiamate e quindi, dal menu di scelta rapida per la voce di struttura ad albero di chiamata, scegliere **Visualizza origine** o **Visualizzare siti di chiamate**.  **Visualizza origine** consente di individuare la riga di codice eseguita.  **Visualizzare i siti di chiamate** consente di individuare la riga di codice che ha chiamato la riga di codice eseguita.  Se esiste un solo sito di chiamata, la sua riga di codice è evidenziata.  Se sono presenti più siti di chiamata, è possibile selezionare quello desiderato nella finestra di dialogo e quindi scegliere il pulsante **Vai all'origine** per evidenziare il codice del sito di chiamata.  È spesso molto utile localizzare il sito di chiamata con il maggior numero di istanze, i tempi più elevati o entrambi.  Per ulteriori informazioni, vedere [Report del profilo di esecuzione](../profiling/execution-profile-report.md).  
  
#### Sincronizzazione  
 Il rapporto di sincronizzazione mostra le chiamate responsabili dei blocchi di sincronizzazione con i tempi di blocco aggregati di ogni stack di chiamate.  Per ulteriori informazioni, vedere [Tempo di sincronizzazione](../profiling/synchronization-time.md).  
  
#### I\/O  
 Il rapporto di I\/O mostra le chiamate responsabili dei blocchi di I\/O con i tempi di blocco aggregati di ogni stack di chiamate.  Per ulteriori informazioni, vedere [Tempo di I\/O \(visualizzazione Thread\)](../profiling/i-o-time-threads-view.md).  
  
#### Sleep  
 Il rapporto di sospensione mostra le chiamate responsabili dei blocchi di sospensione con i tempi di blocco aggregati di ogni stack di chiamate.  Per ulteriori informazioni, vedere [Durata della sospensione](../profiling/sleep-time.md).  
  
#### Gestione della memoria  
 Il rapporto della gestione della memoria mostra le chiamate in cui si sono verificati blocchi di gestione della memoria, oltre ai tempi di blocco aggregati di ogni stack di chiamate.  È possibile utilizzare queste informazioni per identificare aree che hanno eccessivi problemi di Garbage Collection o di paging.  Per ulteriori informazioni, vedere [Tempo di gestione della memoria](../profiling/memory-management-time.md).  
  
#### Priorità  
 Il rapporto di precedenza mostra le istanze in cui i processi nel sistema si sono appropriati del processo corrente e i singoli thread che hanno sostituito i thread nel processo corrente.  È possibile utilizzare queste informazioni per identificare i processi e thread che sono più responsabili di prelazione.  Per ulteriori informazioni, vedere [Tempo di annullamento](../profiling/preemption-time.md).  
  
#### Elaborazione interfaccia utente  
 Il rapporto di elaborazione interfaccia mostra le chiamate responsabili dei blocchi di elaborazione interfaccia con i tempi di blocco aggregati di ogni stack di chiamate.  Per ulteriori informazioni, vedere [Tempo di elaborazione dell'interfaccia utente](../profiling/ui-processing-time.md).  
  
#### Riepilogo per thread  
 Questa scheda contiene una visualizzazione a colonne contraddistinte dal colore del tempo totale trascorso da ogni thread nell'esecuzione, blocco, I\/O e altri stati.  Le colonne sono identificate nella parte inferiore.  Quando si modifica il livello di zoom nel grafico della sequenza temporale, questa scheda viene aggiornata automaticamente.  A determinati livelli di zoom, alcuni thread potrebbero non essere visualizzati.  In questo caso, vengono visualizzati dei puntini di sospensione sulla destra.  Se il thread desiderato non è presente, è possibile nascondere gli altri thread.  Per ulteriori informazioni, vedere [Report di riepilogo per thread](../profiling/per-thread-summary-report.md).  
  
#### Operazioni su disco  
 Questa scheda mostra quale i processi e thread sono coinvolti in operazioni di I\/O su disco per conto del processo corrente, quali file verranno interessati \(ad esempio, DLL che sono state caricate\), il numero di byte letti, e altre informazioni.  È possibile utilizzare questo rapporto per valutare il tempo impiegato nell'accesso ai file durante l'esecuzione, specialmente se il processo presenta in apparenza vincoli di I\/O.  Per ulteriori informazioni, vedere [Report delle operazioni su disco](../profiling/disk-operations-report-threads-view.md).  
  
## Vedere anche  
 [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)