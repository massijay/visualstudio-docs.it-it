---
title: "Procedura dettagliata: debug di un&#39;applicazione multithreading | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug con multithreading, procedura dettagliata"
  - "procedure dettagliate, debug con multithreading"
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura dettagliata: debug di un&#39;applicazione multithreading
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] fornisce una finestra **Thread** migliorata e altri miglioramenti all'interfaccia utente per semplificare il debug delle applicazioni multithreading.  Il completamento di questa procedura dettagliata richiede solo alcuni minuti, ma è utile per familiarizzare con le nuove funzionalità dell'interfaccia per il debug delle applicazioni multithreading.  
  
 Per iniziare questa procedura dettagliata, è necessario un progetto di applicazione multithreading.  Per creare tale progetto, attenersi alla procedura qui indicata.  
  
#### Per creare il progetto necessario per la procedura dettagliata  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
2.  Nella casella **Tipi progetto** scegliere il linguaggio desiderato: **Visual Basic**, **Visual C\#** o **Visual C\+\+**.  
  
3.  Nella casella **Modelli** scegliere **Applicazione console** o **Applicazione console CLR**.  
  
4.  Nella casella **Nome** digitare il nome MyThreadWalkthroughApp.  
  
5.  Scegliere **OK**.  
  
     Verrà visualizzato un nuovo progetto console.  Dopo aver creato il progetto, viene visualizzato un file di origine.  A seconda del linguaggio scelto, il nome del file di origine potrebbe essere Module1.vb, Program.cs o MyThreadWalkthroughApp.cpp  
  
6.  Eliminare il codice visualizzato nel file di origine e sostituirlo con il codice di esempio visualizzato nella sezione "Creazione di un thread" dell'argomento [Creating Threads and Passing Data at Start Time](../Topic/Creating%20Threads%20and%20Passing%20Data%20at%20Start%20Time.md).  
  
7.  Scegliere **Salva tutto** dal menu **File**.  
  
#### Per iniziare la procedura dettagliata  
  
-   Nella finestra di origine cercare il codice seguente:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```c#  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### Per avviare il debug  
  
1.  Fare clic con il pulsante destro del mouse sull'istruzione `Console.WriteLine`, scegliere **Punto di interruzione**, quindi fare clic su **Inserisci punto di interruzione**.  
  
     All'estrema sinistra della finestra di origine viene visualizzata una sfera rossa  che indica l'impostazione di un punto di interruzione in tale posizione.  
  
2.  Scegliere **Avvia debug** dal menu **Debug**.  
  
     Viene avviato il debug e viene avviata l'esecuzione dell'applicazione che viene quindi interrotta in corrispondenza del punto di interruzione.  
  
3.  Se a questo punto la finestra dell'applicazione console ha lo stato attivo, fare clic nella finestra di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per ripristinare lo stato attivo di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Nella finestra di origine trovare la riga che contiene il codice seguente:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```c#  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
#### Per individuare il marcatore del thread  
  
1.  Fare clic con il pulsante destro del mouse sulla finestra **Thread**, quindi fare clic su **Mostra thread nell'origine**.  
  
2.  All'estrema sinistra della finestra,  in corrispondenza di questa riga, verrà visualizzata un'icona con due fili,  uno rosso e uno blu.  Il marcatore del thread indica l'interruzione di un thread in questa posizione.  È possibile, pertanto, che un thread venga interrotto in questa posizione.  
  
3.  Posizionare il puntatore del mouse sul marcatore del thread.  Viene visualizzato un suggerimento dati  in cui è indicato il nome e il numero ID di ciascun thread interrotto.  In questo caso, l'interruzione si è verificata in un solo thread denominato `<noname>`.  
  
4.  Fare clic con il pulsante destro del mouse sul marcatore del thread  per visualizzare un menu di scelta rapida.  
  
 L'icona del *marcatore del thread* è simile alla seguente:  
  
 ![Marcatore del thread](../debugger/media/threadmarker.png "ThreadMarker")  
  
## Impostazione e rimozione dei flag dei thread  
 In [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] è possibile impostare i flag dei thread a cui si desidera attribuire particolare attenzione.  L'impostazione dei flag dei thread è un ottimo strumento per tenere traccia dei thread importanti e per ignorare quelli a cui non si desidera prestare attenzione.  
  
#### Per impostare i flag dei thread  
  
1.  Scegliere **Barre degli strumenti** dal menu **Visualizza**.  
  
     Verificare che sia selezionata la barra degli strumenti **Posizione di debug**.  
  
2.  Nella barra degli strumenti **Posizione di debug** selezionare l'elenco **Thread**.  
  
    > [!NOTE]
    >  In questa barra degli strumenti sono presenti tre elenchi principali: **Processo**, **Thread** e **Stack frame**.  
  
3.  Osservare il numero di thread visualizzati nell'elenco.  
  
4.  Tornare alla finestra di origine e fare nuovamente clic con il pulsante destro del mouse sul marcatore **Thread**.  
  
5.  Scegliere **Imposta flag** dal menu di scelta rapida, quindi scegliere il nome e il numero ID del thread.  
  
6.  Tornare alla barra degli strumenti **Posizione di debug** e fare nuovamente clic sull'elenco **Thread**.  
  
     Nell'elenco viene visualizzato ora solo il thread con flag.  Il pulsante del flag si trova a destra dell'elenco **Thread**.  L'icona del flag sul pulsante che prima era visualizzata in grigio  è ora di colore rosso.  
  
7.  Posizionare il puntatore del mouse sull'icona del flag.  
  
     Viene visualizzato un popup  in cui è indicato che l'elenco **Thread** è in modalità **Mostra solo thread con flag**.  
  
8.  Fare clic sul pulsante del flag per passare di nuovo alla modalità **Mostra tutti i thread**.  
  
9. Fare nuovamente clic sull'elenco **Thread** e verificare che ora sono visualizzati di nuovo tutti i thread.  
  
10. Fare clic sul pulsante del flag per passare di nuovo alla modalità **Mostra solo thread con flag**.  
  
11. Scegliere **Finestre** dal menu **Debug**, quindi **Thread**.  
  
     Verrà visualizzata la finestra **Thread** in cui è presente un thread con un'icona del flag associata.  
  
12. Nella finestra di origine fare nuovamente clic con il pulsante destro del mouse sul marcatore del thread.  
  
     Osservare ora le scelte disponibili nel menu di scelta rapida.  Invece di **Imposta flag**, sarà ora disponibile **Rimuovi flag**.  Non scegliere **Rimuovi flag**.  
  
13. Passare alla procedura successiva in cui viene descritto come rimuovere i flag dei thread.  
  
#### Per rimuovere i flag dei thread  
  
1.  Nella finestra **Thread** fare clic con il pulsante destro del mouse sulla riga che corrisponde al thread con flag.  
  
     Verrà visualizzato un menu di scelta rapida.  Sono disponibili le opzioni **Rimuovi flag** e **Rimuovi flag di tutti i thread**.  
  
2.  Per rimuovere i flag dei thread, fare clic **Rimuovi flag**.  
  
3.  Fare clic sull'icona del flag rossa.  
  
4.  Osservare nuovamente la barra degli strumenti **Posizione di debug**.  Il pulsante del flag è nuovamente in grigio.  È stato rimosso il flag dall'unico thread con flag.  Poiché non sono disponibili thread con flag, la barra degli strumenti è tornata alla modalità **Mostra tutti i thread**.  Fare clic sull'elenco **Thread** e verificare che sono visualizzati tutti i thread.  
  
5.  Tornare alla finestra **Thread** ed esaminare le colonne informazioni.  
  
     La maggior parte dei pulsanti situati all'inizio di ogni colonna dispone di titoli che identificano la colonna.  Nella prima colonna a sinistra però non è presente alcun titolo,  bensì un'icona con il profilo di una bandiera.  Si noterà lo stesso profilo in ogni riga dell'elenco di thread.  Il profilo indica la rimozione del flag del thread.  
  
6.  Fare clic sui profili di due thread, il secondo e terzo dalla fine dell'elenco.  
  
     Le icone del flag con profili vuoti vengono sostituite da icone di colore rosso.  
  
7.  Fare clic sul pulsante nella parte superiore della colonna dei flag.  
  
     Quando si fa clic su questo pulsante, cambia l'ordine dell'elenco di thread  visualizzando ora i thread con flag all'inizio.  
  
8.  Fare nuovamente clic sul pulsante nella parte superiore della colonna dei flag.  
  
     L'ordine cambia di nuovo.  
  
## Ulteriori informazioni sulla finestra Thread  
  
#### Per ulteriori informazioni sulla finestra Thread  
  
1.  Nella finestra **Thread** esaminare la terza colonna da sinistra.  Il pulsante all'inizio di questa colonna è **ID**.  
  
2.  Fare clic su **ID**.  
  
     L'elenco di thread viene ora ordinato in base al numero ID del thread.  
  
3.  Fare clic con il pulsante destro del mouse su un thread dell'elenco.  Scegliere **Visualizzazione esadecimale** dal menu di scelta rapida.  
  
     Il formato dei numeri ID del thread cambia.  
  
4.  Posizionare il puntatore del mouse su un thread dell'elenco.  
  
     Verrà visualizzato un suggerimento dati  con uno stack di chiamate parziale per il thread.  
  
5.  Osservare la quarta colonna da sinistra denominata **Categoria**.  I thread vengono classificati in categorie.  
  
     Il primo thread creato in un processo è denominato thread principale.  Individuarlo nell'elenco di thread.  
  
6.  Fare clic con il pulsante destro del mouse sul thread principale, quindi fare clic su **Passa al thread**.  
  
     Verrà visualizzata una finestra di dialogo di avviso  in cui viene indicato che non è possibile visualizzare il codice sorgente per il thread principale in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Scegliere **OK**.  
  
7.  Osservare la finestra **Stack di chiamate** e la barra degli strumenti **Posizione di debug**.  
  
     Il contenuto della finestra **Stack di chiamate** è cambiato.  
  
## Passaggio al thread attivo  
  
#### Per passare da un thread all'altro  
  
1.  Nella finestra **Thread** esaminare la seconda colonna da sinistra.  Il pulsante all'inizio di questa colonna non presenta alcun testo o icona.  Si tratta della colonna **Thread attivo**.  
  
2.  Osservare la colonna **Thread attivo** e notare che tale thread ha una freccia gialla  per indicare che si tratta dell'*indicatore del thread attivo*.  
  
3.  Annotare il numero ID del thread dove è posizionato l'indicatore del thread attivo.  Spostare l'indicatore del thread attivo in un altro thread, riportandolo però nella posizione originaria al termine dell'operazione.  
  
4.  Fare clic con il pulsante destro del mouse su un altro thread, quindi scegliere **Passa al thread**.  
  
5.  Osservare la finestra **Stack di chiamate** nella finestra di origine.  Il contenuto è cambiato.  
  
6.  Osservare la barra degli strumenti **Posizione di debug**.  Anche il thread attivo è cambiato.  
  
7.  Passare alla barra degli strumenti **Posizione di debug**.  Fare clic sulla casella **Thread** e scegliere un altro thread dall'elenco a discesa.  
  
8.  Osservare la finestra **Thread**.  L'indicatore del thread attivo è cambiato.  
  
9. Nella finestra di origine fare nuovamente clic con il pulsante destro del mouse su un marcatore del thread.  Scegliere **Passa a** dal menu di scelta rapida, quindi scegliere il nome e il numero ID di un thread.  
  
     Sono stati analizzati tre modi di modifica del thread attivo: mediante la finestra **Thread**, la casella **Thread** della barra degli strumenti **Posizione di debug** e l'indicatore del thread nella finestra di origine.  
  
     Con l'indicatore del thread è possibile passare solo ai thread che sono stati interrotti in quella determinata posizione.  Con la finestra **Thread** e la barra degli strumenti **Posizione di debug** è possibile passare a tutti i tipi di thread.  
  
## Blocco e sblocco dell'esecuzione dei thread  
  
#### Per bloccare e sbloccare i thread  
  
1.  Nella finestra **Thread** fare clic con il pulsante destro del mouse su un thread, quindi scegliere **Blocca**.  
  
2.  Osservare la colonna dei thread attivi.  Vengono visualizzate ora due barre verticali.  Queste due barre blu indicano che il thread è bloccato.  
  
3.  Osservare la colonna **Sospendi**.  Il conteggio di sospensione per il thread ora è 1.  
  
4.  Fare clic con il pulsante destro del mouse sul thread bloccato, quindi fare clic su **Sblocca**.  
  
     La colonna dei thread attivi e la colonna **Sospendi** cambiano.  
  
## Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)