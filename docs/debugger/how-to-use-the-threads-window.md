---
title: "Procedura: utilizzare la finestra Thread | Microsoft Docs"
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
  - "vs.debug.threads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "threading [Visual Studio], debug"
  - "Thread.Name (proprietà)"
  - "debugger, finestra Thread"
  - "SetThreadName (funzione)"
  - "finestra Thread"
  - "@TIB"
  - "debug [Visual Studio], thread"
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 44
caps.handback.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: utilizzare la finestra Thread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra **Thread** è possibile esaminare e utilizzare i thread dell'applicazione sottoposta a debug.  
  
 La finestra **Thread** contiene una tabella in cui ogni riga rappresenta un thread nell'applicazione.  Per impostazione predefinita, nella tabella sono elencati tutti i thread dell'applicazione, ma è possibile filtrare l'elenco per visualizzare solo i thread che interessano.  Ogni colonna contiene un tipo di informazioni diverso.  È possibile inoltre nascondere alcune colonne.  Visualizzando tutte le colonne, vengono visualizzate le informazioni seguenti da sinistra verso destra:  
  
-   La colonna del contrassegno, dove è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.  Per informazioni su come contrassegnare un thread, vedere [Procedura: impostare e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   La colonna del thread attivo, dove una freccia gialla indica un thread attivo.  Il contorno di una freccia indica il thread nel quale l'esecuzione si è interrotta nel debugger.  
  
-   La colonna **ID**, che contiene il numero di identificazione per ogni thread.  
  
-   La colonna **ID gestito**, che contiene i numeri di identificazione gestiti per i thread gestiti.  
  
-   La colonna **Categoria**, che categorizza i thread come thread di interfaccia utente, gestori delle chiamate a procedura remota o thread di lavoro.  Una categoria speciale identifica il thread principale dell'applicazione.  
  
-   Colonna **Nome**, che identifica ogni thread in base al nome, se disponibile, o come \<Nessun nome\>.  
  
-   La colonna **Percorso**, che mostra il percorso nel quale viene eseguito il thread.  È possibile espandere questo percorso per visualizzare lo stack di chiamate completo per il thread.  
  
-   La colonna **Priorità**, che contiene la priorità o precedenza assegnata dal sistema a ogni thread.  
  
-   La colonna **Maschera di affinità**, colonna avanzata generalmente nascosta.  In questa colonna viene visualizzata la maschera di affinità del processore per ogni thread.  In un sistema con più processori, la maschera di affinità determina in quali processori è possibile eseguire un thread.  
  
-   Colonna **Numero sospesi**, che contiene il conteggio sospeso.  Questo conteggio determina se un thread può essere eseguito.  Per una spiegazione del conteggio sospeso, vedere "Blocco e sblocco dei thread" più avanti in questo argomento.  
  
-   La colonna **Nome processo**, che contiene il processo al quale appartiene ogni thread.  Questa colonna può risultare utile quando si esegue il debug di più processi, ma in genere è nascosta.  
  
### Per visualizzare la finestra Thread in modalità di interruzione o di esecuzione  
  
-   Scegliere **Finestre** dal menu **Debug**, quindi **Thread**.  
  
### Per visualizzare o nascondere una colonna  
  
-   Nella barra degli strumenti nella parte superiore della finestra **Thread** fare clic su **Colonne**, quindi selezionare o deselezionare il nome della colonna che si desidera visualizzare o nascondere.  
  
### Per passare al thread attivo  
  
-   Effettuare uno dei passaggi seguenti:  
  
    -   Fare doppio clic su un thread.  
  
    -   Fare clic con il pulsante destro del mouse su un thread e scegliere **Passa al thread**.  
  
         La freccia gialla viene visualizzata accanto al nuovo thread attivo.  Il contorno grigio di una freccia identifica il thread nel quale l'esecuzione si è interrotta nel debugger.  
  
## Raggruppamento e ordinamento dei thread  
 Quando si raggruppano i thread, nella tabella viene visualizzata un'intestazione per ogni gruppo.  L'intestazione contiene una descrizione del gruppo, ad esempio "Thread di lavoro" o "Thread senza flag", e un controllo di struttura ad albero.  I thread membro di ciascuno gruppo appaiono sotto l'intestazione del gruppo.  Per nascondere i thread membro di un gruppo, è possibile utilizzare il controllo di struttura ad albero per comprimere il gruppo.  
  
 Poiché il raggruppamento ha la precedenza sull'ordinamento, è possibile ad esempio raggruppare i thread per categoria, per poi ordinarli in base all'ID all'interno di ogni categoria.  
  
#### Per ordinare i thread  
  
1.  Nella barra degli strumenti nella parte superiore della finestra **Thread** fare clic sul pulsante in cima a ogni colonna.  
  
     I thread verranno ordinati in base ai valori in quella colonna.  
  
2.  Per invertire l'ordine, fare nuovamente clic sullo stesso pulsante.  
  
     I thread che prima erano visualizzati all'inizio dell'elenco appariranno al fondo.  
  
#### Per raggruppare i thread  
  
-   Nella barra degli strumenti della finestra **Thread** fare clic sull'elenco **Raggruppa per**, quindi scegliere i criteri in base ai quali raggruppare i thread.  
  
#### Per ordinare i thread all'interno di gruppi  
  
1.  Nella barra degli strumenti nella parte superiore della finestra **Thread** fare clic sull'elenco **Raggruppa per**, quindi scegliere i criteri in base ai quali raggruppare i thread.  
  
2.  Nella finestra **Thread** fare clic sul pulsante all'inizio di una colonna.  
  
     I thread verranno ordinati in base ai valori in quella colonna.  
  
#### Per espandere o comprimere tutti i gruppi  
  
-   Nella barra degli strumenti nella parte superiore della finestra **Thread** fare clic su **Espandi gruppi** o **Comprimi gruppi**.  
  
## Ricerca di thread specifici  
 In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] è possibile cercare i thread che corrispondono a una stringa specificata.  Quando si cercano i thread nella finestra **Thread**, questa visualizza tutti i thread che corrispondono alla stringa di ricerca in qualsiasi colonna.  Le informazioni includono il percorso del thread visualizzato all'inizio dello stack di chiamate nella colonna **Percorso**.  Per impostazione predefinita, tuttavia, non vengono eseguite ricerche nello stack di chiamate completo.  
  
#### Per cercare thread specifici  
  
-   Nella barra degli strumenti nella parte superiore della finestra **Thread** andare alla casella **Cerca** e:  
  
    -   Digitare una stringa di ricerca, quindi premere INVIO.  
  
         \- oppure \-  
  
    -   Fare clic sull'elenco a discesa accanto alla casella **Cerca** e selezionare una stringa di ricerca da una ricerca precedente.  
  
-   \(Facoltativo\) Per includere lo stack di chiamate completo nella ricerca, selezionare **Cerca nello stack di chiamate**.  
  
## Blocco e sblocco dei thread  
 Quando si blocca un thread, l'esecuzione dello stesso da parte del sistema non viene avviata anche se le risorse sono disponibili.  
  
 Nel codice nativo, è possibile sospendere o riprendere i thread chiamando le funzioni Windows `SuspendThread` e `ResumeThread` o le funzioni MFC [CWinThread::SuspendThread](../Topic/CWinThread::SuspendThread.md) e [CWinThread::ResumeThread](../Topic/CWinThread::ResumeThread.md).  Se si chiama `SuspendThread` o `ResumeThread`, si modifica il *numero sospesi* visualizzato nella finestra **Thread**.  Tuttavia, se si blocca o sblocca un thread nativo, il numero sospesi non viene modificato.  Nel codice nativo, un thread non può essere eseguito a meno che non sia sbloccato e il numero sospesi non sia pari a zero.  
  
 Nel codice gestito, il blocco o lo sblocco di un thread comporta la modifica del numero sospesi.  Nel codice gestito, un thread bloccato presenta un numero sospesi pari a 1.  Nel codice nativo, un thread bloccato presenta un numero sospesi pari a 0 a meno che non sia stato sospeso tramite una chiamata a `SuspendThread`.  
  
> [!NOTE]
>  Quando si esegue il debug di una chiamata da codice nativo a codice gestito, il codice gestito viene eseguito nello stesso thread fisico del codice nativo che lo ha chiamato.  Sospendendo o bloccando l'esecuzione del thread di codice nativo si otterrà anche il blocco del codice gestito.  
  
#### Per bloccare o sbloccare l'esecuzione di un thread  
  
-   Nella barra degli strumenti nella parte superiore della finestra **Thread** fare clic su **Blocca thread** o **Sblocca thread**.  
  
     Questa azione influisce solo sui thread selezionati nella finestra **Thread**.  
  
## Visualizzazione di thread con flag  
 È possibile contrassegnare un thread al quale si desidera prestare particolare attenzione mediante un'icona nella finestra **Thread**.  Per ulteriori informazioni, vedere [Procedura: impostare e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md).  Nella finestra Thread è possibile scegliere di visualizzare tutti i thread o solo i thread con flag.  
  
#### Per visualizzare solo i thread con flag  
  
-   Scegliere il pulsante flag nell'angolo superiore sinistro della finestra **Thread**.  
  
## Visualizzazione degli stack di chiamate dei thread e passaggio da un frame all'altro  
 In un programma multithread ogni thread dispone di un proprio stack di chiamate.  La finestra **Thread** consente di visualizzare in modo pratico questi stack.  
  
#### Per visualizzare lo stack di chiamate di un thread  
  
-   Nella colonna **Percorso** fare clic sul triangolo invertito accanto al percorso del thread.  
  
     Il percorso si espanderà per visualizzare lo stack di chiamate del thread.  
  
#### Per visualizzare o comprimere gli stack di chiamate di tutti i thread  
  
-   Nella barra degli strumenti nella parte superiore della finestra **Thread** fare clic su **Espandi stack di chiamate** o **Comprimi stack di chiamate**.  
  
## Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura dettagliata: debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md)