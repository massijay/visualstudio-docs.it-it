---
title: "Procedura dettagliata: Profilatura di applicazioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, procedure dettagliate"
  - "strumenti per le prestazioni, procedure dettagliate"
  - "prestazioni, analisi"
  - "applicazioni di profilatura, procedure dettagliate"
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 53
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura dettagliata: Profilatura di applicazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come profilare un'applicazione per l'identificazione dei problemi di prestazioni.  
  
 In questa procedura dettagliata verranno illustrati tutti i passaggi del processo di profilatura di un'applicazione gestita, nonché l'utilizzo del campionamento e della strumentazione per isolare e identificare i problemi presenti nell'applicazione.  
  
 Nel corso di questa procedura dettagliata verranno effettuate le seguenti operazioni:  
  
-   Profilare un'applicazione utilizzando il metodo di campionamento.  
  
-   Esaminare i risultati dell'analisi mediante campionamento per individuare e risolvere un problema di prestazioni.  
  
-   Profilare un'applicazione utilizzando il metodo di strumentazione.  
  
-   Esaminare i risultati dell'analisi mediante strumentazione per individuare e risolvere un problema di prestazioni.  
  
## Prerequisiti  
  
-   Conoscenza di livello medio di C\#.  
  
-   Una copia di [Esempio PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md).  
  
 Per utilizzare le informazioni fornite dalla profilatura, è preferibile che siano disponibili le informazioni sui simboli di debug.  
  
## Profilatura mediante il metodo di campionamento  
 Il campionamento è il metodo di analisi con cui il processo in questione viene sottoposto regolarmente a polling al fine di stabilire quale sia la funzione attiva.  Nei dati risultanti è presente un conteggio della frequenza con cui la funzione in oggetto si è trovata in cima allo stack di chiamate quando è stato effettuato il campionamento del processo.  
  
#### Per profilare un'applicazione utilizzando il metodo di campionamento  
  
1.  Aprire [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] con i privilegi di amministratore.  L'esecuzione come un amministratore è obbligatoria per la profilatura.  
  
2.  Aprire la soluzione PeopleTrax.  
  
     La soluzione PeopleTrax verrà inserita in Esplora soluzioni.  
  
3.  Impostare l'opzione di configurazione del progetto su **Release**.  
  
     Si consiglia di utilizzare una compilazione di rilascio per rilevare problemi di prestazioni nell'applicazione.  Una compilazione di rilascio è consigliata per la profilatura perché una compilazione di debug contiene informazioni aggiuntive che potrebbero incidere negativamente sulle prestazioni e non riuscire a illustrare accuratamente i problemi di prestazioni.  
  
4.  Scegliere **Avvia Creazione guidata sessione di prestazioni** dal menu **Analizza**.  
  
     Verrà visualizzata la Creazione guidata sessione di prestazioni.  
  
5.  Assicurarsi che **Campionamento CPU \(consigliato\)** sia selezionata, quindi scegliere **Avanti**.  
  
6.  In **Specificare l'applicazione di destinazione per il profilo** selezionare PeopleTrax, quindi scegliere **Avanti**.  
  
     In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] viene compilato il progetto e viene avviata la profilatura dell'applicazione.  Verrà visualizzata la finestra dell'applicazione **PeopleTrax**.  
  
7.  Fare clic su **Get People**.  
  
8.  Scegliere **Esporta Dati**.  
  
     Viene aperto Blocco note in cui è visualizzato un nuovo file contenente i dati esportati da **PeopleTrax**.  
  
9. Chiudere Blocco note e successivamente l'applicazione **PeopleTrax**.  
  
     Il profiler genera un file dei dati di profilatura \(\*.vsp\), elenca il nome file nella sezione Rapporti della finestra Esplora prestazioni e carica automaticamente la visualizzazione **Riepilogo** del file di dati nella finestra principale di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
#### Per esaminare i risultati dell'analisi mediante campionamento  
  
1.  Nella visualizzazione Riepilogo sono riportati una sequenza temporale dell'utilizzo della CPU nel corso dell'esecuzione della profilatura, l'elenco **Percorso critico** che rappresenta il ramo dell'albero delle chiamate dell'applicazione più attiva e un elenco di **Funzioni che svolgono più lavoro individuale** con le funzioni sottoposte a un campionamento più frequente durante l'esecuzione di codice nel corpo stesso della funzione.  
  
     Esaminare l'elenco **Percorso critico** e notare che il metodo PeopleNS.People.GetNames è la funzione PeopleTrax più vicina alla fine dell'elenco.  La posizione la rende un buon candidato per l'analisi.  Fare clic sul nome della funzione per visualizzare dettagli di GetNames nella visualizzazione **Dettagli funzione**.  
  
2.  Nella visualizzazione **Dettagli funzione** sono presenti due finestre.  La finestra di distribuzione dei costi fornisce una visualizzazione grafica delle operazioni eseguite dalla funzione e dalle funzioni chiamate, nonché il contributo delle funzioni che hanno chiamato la funzione sul numero di istanze campionate.  È possibile modificare la funzione con lo stato attivo della visualizzazione facendo clic sul nome di una funzione.  Ad esempio, è possibile fare clic su PeopleNS.People.GetPeople per impostare GetPeople come funzione selezionata.  
  
     Nella finestra **Visualizzazione codice funzione** viene mostrato il codice sorgente della funzione, se disponibile, e vengono evidenziate le righe con il costo più elevato della funzione selezionata.  Quando è selezionata GetNames, è possibile verificare che questa funzione legge una stringa dalle risorse dell'applicazione, quindi utilizza un oggetto <xref:System.IO.StringReader> per aggiungere ogni riga nella stringa a un oggetto <xref:System.Collections.ArrayList>.  Non esiste una modalità ovvia per ottimizzare questa funzione.  
  
3.  Poiché PeopleNS.People.GetPeople è il solo chiamante di GetNames, fare clic su GetPeople nella finestra di distribuzione dei costi per esaminare il codice.  Questo metodo restituisce un oggetto <xref:System.Collections.ArrayList> di oggetti PersonInformationNS.PersonInformation dai nomi di persone e società prodotti da GetNames.  GetNames viene tuttavia chiamato due volte ogni volta che viene creato un oggetto PersonInformation.  È possibile osservare che il metodo può essere facilmente ottimizzato creando gli elenchi una sola volta all'inizio del metodo e indicizzando tali elenchi durante il ciclo di creazione di PersonInformation.  
  
4.  Una versione alternativa di GetPeople viene fornita con il codice dell'applicazione di esempio ed è possibile chiamare la funzione ottimizzata aggiungendo un simbolo di compilazione condizionale alle proprietà di compilazione.  Nella finestra Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto People, quindi scegliere **Proprietà**.  Scegliere **Compila** dal menu della pagina delle proprietà, quindi digitare **OPTIMIZED\_GETPEOPLE** nella casella di testo Simboli di compilazione condizionale.  La versione ottimizzata di GetPeople sostituisce il metodo originale nella compilazione successiva.  
  
5.  Eseguire di nuovo la sessione di prestazioni.  Sulla barra degli strumenti di Esplora prestazioni fare clic su **Avvio con profilatura** .  Fare clic su **Get People**, quindi su **Esporta dati**.  Chiudere la finestra Blocco note che viene visualizzata, quindi chiudere l'applicazione PeopleTrax.  
  
     Viene generato un nuovo file dei dati di profilatura e nella finestra principale di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] viene mostrata una visualizzazione **Riepilogo** per i nuovi dati.  
  
6.  Per confrontare le due esecuzioni della profilatura, selezionare i due file di dati in Esplora prestazioni, fare clic con il pulsante destro del mouse sui file, quindi scegliere **Confronta rapporti di prestazioni**.  Nella finestra principale di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] viene visualizzata la finestra Rapporto di confronto.  Nella colonna **Delta** è visualizzata la modifica del valore di prestazioni delle funzioni dal precedente valore di **Alla linea di base** al successivo valore di **Confronto**.  È possibile selezionare i valori da confrontare dall'elenco a discesa **Colonna**.  Selezionare **% campioni inclusivi**.  
  
     Si noti che i metodi GetPeople e GetNames mostrano notevoli miglioramenti delle prestazioni.  
  
## Profilatura mediante il metodo di strumentazione  
 La strumentazione è un metodo di profilatura in cui il profiler inserisce funzioni probe in versioni compilate in modo speciale dei binari profilati.  I probe raccolgono informazioni sugli intervalli all'ingresso e all'uscita di funzioni nei moduli instrumentati e in tutti i siti di chiamata in tali funzioni.  Il processo di strumentazione è utile per analizzare problemi relativi alle operazioni di input\/output, quali la scrittura su disco e la comunicazione in rete.  La strumentazione fornisce informazioni più dettagliate del campionamento, ma è più intrusiva nell'esecuzione del processo e implica un maggior sovraccarico.  I binari instrumentati sono inoltre di dimensioni maggiori rispetto a quelli di debug e di rilascio e non sono destinati alla distribuzione.  
  
 In questa sezione della procedura dettagliata si utilizzerà il metodo di strumentazione per individuare ulteriore codice ottimizzabile nell'applicazione PeopleTrax precedentemente profilata.  Tramite il filtro della cronologia della visualizzazione Riepilogo, si concentrerà l'analisi sullo scenario di esportazione dei dati nell'applicazione profilata, in cui l'elenco di persone viene scritto in un file del Blocco note.  
  
#### Per profilare un'applicazione esistente utilizzando il metodo di strumentazione  
  
1.  Se necessario, aprire l'applicazione PeopleTrax in Visual Studio.  
  
     Verificare che il programma venga eseguito come Amministratore e che la configurazione della compilazione per la soluzione viene impostata su **Release**.  
  
2.  In Esplora prestazioni fare clic su **Strumentazione**.  
  
3.  Sulla barra degli strumenti di Esplora prestazioni fare clic su **Avvio con analisi** .  
  
     Il profiler compila il progetto e avvia la profilatura dell'applicazione.  Verrà visualizzata la finestra dell'applicazione PeopleTrax.  
  
4.  Fare clic su **Get People**.  
  
     La griglia di dati di PeopleTrax viene compilata.  
  
5.  Attendere per circa 10 secondi, quindi fare clic su **Esporta dati**.  
  
     Viene avviato **Blocco note** in cui viene visualizzato un nuovo file contenente un elenco di persone ottenuto dall'applicazione PeopleTrax.  L'attesa consente di identificare più facilmente la procedura di esportazione dei dati per il filtraggio.  
  
6.  Chiudere **Blocco note** e successivamente l'applicazione **PeopleTrax**.  
  
     In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] viene generato un report delle sessioni di prestazioni \(\*.vsp\).  
  
#### Per esaminare i risultati dell'analisi mediante strumentazione  
  
1.  Il grafico cronologia della visualizzazione **Riepilogo** del rapporto mostra l'utilizzo della CPU del programma per la durata dell'esecuzione della profilatura.  L'operazione di esportazione dei dati dovrebbe essere il punto massimo o costante sul lato destro del grafico.  È possibile filtrare la sessione di prestazioni per visualizzare e analizzare solo i dati raccolti nell'operazione di esportazione.  Fare clic a sinistra dell punto sul grafico dove inizia l'operazione sui dati dell'esportazione.  Fare di nuovo clic sul lato destro dell'operazione.  Fare quindi clic su **Filtra in base a selezione** nell'elenco di collegamenti a destra della cronologia.  
  
     Nella struttura ad albero **Percorso critico** viene mostrato che il metodo <xref:System.String.Concat%2A> chiamato dal metodo PeopleTrax.Form1.ExportData utilizza un'ampia percentuale del tempo.  Poiché **System.String.Concat** si trova anche all'inizio dell'elenco **Funzioni con più lavoro individuale**, la riduzione del tempo trascorso nella funzione è un possibile punto di ottimizzazione.  
  
2.  Fare doppio clic su **System.String.Concat** in una delle tabelle di riepilogo per ottenere ulteriori informazioni nella visualizzazione Dettagli funzione.  
  
3.  È possibile osservare che PeopleTrax.Form1.ExportData è il solo metodo che chiama Concat.  Fare clic su **PeopleTrax.Form1.ExportData** nell'elenco **Funzioni chiamanti** per selezionare il metodo come destinazione della visualizzazione Dettagli funzione.  
  
4.  Esaminare il metodo nella finestra Visualizzazione codice funzione.  Notare che non sono presenti chiamate letterali a **System.String.Concat**.  Sono invece presenti diversi utilizzi dell'operando \+\=, che il compilatore sostituisce con chiamate a **System.String.Concat**.  Qualsiasi modifica apportata a una stringa in .NET Framework determina l'allocazione di una nuova stringa.  In .NET Framework è disponibile una classe <xref:System.Text.StringBuilder> ottimizzata per la concatenazione di stringhe.  
  
5.  Per sostituire l'area problematica con il codice ottimizzato, aggiungere OPTIMIZED\_EXPORTDATA come simbolo di compilazione condizionata al progetto PeopleTrax.  
  
6.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto PeopleTrax e scegliere **Proprietà**.  
  
     Verrà visualizzato il form delle proprietà del progetto PeopleTrax.  
  
7.  Fare clic sulla scheda **Compila**.  
  
8.  Nella casella di testo **Simboli di compilazione condizionale** digitare OPTIMIZED\_EXPORTDATA.  
  
9. Chiudere il form delle proprietà del progetto e scegliere **Salva tutto** quando richiesto.  
  
 Alla successiva esecuzione dell'applicazione sarà possibile riscontrare notevoli miglioramenti nelle prestazioni.  Eseguire nuovamente la sessione di analisi, anche se le prestazioni presentano miglioramenti visibili all'utente.  La verifica dei dati dopo la risoluzione di un problema costituisce un passaggio importante, poiché il primo problema potrebbe nasconderne altri.  
  
## Vedere anche  
 [Cenni preliminari](../profiling/overviews-performance-tools.md)   
 [Introduzione](../profiling/getting-started-with-performance-tools.md)   
 [\/Z7, \/Zi, \/ZI \(Formato informazioni di debug\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)