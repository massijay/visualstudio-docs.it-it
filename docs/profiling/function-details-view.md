---
title: "Visualizzazione Dettagli funzione | Microsoft Docs"
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
  - "vs.performance.view.functiondetails"
helpviewer_keywords: 
  - "visualizzazione Dettagli funzione"
  - "strumenti di profilatura, visualizzazione Dettagli funzione"
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Dettagli funzione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra **Visualizzazione Dettagli funzione** vengono visualizzate le informazioni seguenti:  
  
-   Grafico a barre **Distribuzione costi** che rappresenta le relazioni tra una funzione selezionata e le funzioni chiamanti che hanno eseguito la funzione selezionata e tra la funzione selezionata e le funzioni che ha chiamato.  
  
-   Nella tabella **Dettagli prestazioni funzione** sono riportati i dati di profilo di riepilogo per la funzione specificata.  
  
-   Nella finestra **Visualizzazione Codice funzione** viene visualizzato il codice della funzione quando è disponibile.  
  
 La finestra **Visualizzazione Codice funzione** è un riquadro separato.  Per impostazione predefinita, i due riquadri sono suddivisi orizzontalmente e la finestra **Visualizzazione Codice funzione** è posizionata nella parte inferiore del frame.  
  
-   Per suddividere i due riquadri verticalmente, fare clic su **Dividi schermo verticalmente** sulla barra degli strumenti.  
  
-   Per modificare le dimensioni relative dei riquadri, fare clic sul bordo ombreggiato tra le cornici e trascinare il bordo in un'altra posizione.  
  
## Grafico a barre Distribuzione costi  
  
### Metriche prestazioni  
 Nell'elenco a discesa **Metrica prestazioni** è possibile specificare i valori da visualizzare.  I valori disponibili dipendono dal metodo di profilo utilizzato nel file dei dati di profilo.  I nomi tra parentesi sono i nomi delle righe nella tabella **Dettagli prestazioni funzione**.  
  
### Grafico a barre  
 **Chiamata delle funzioni**  
  
 Sulla barra **Funzioni chiamanti** vengono visualizzate le funzioni che hanno chiamato la funzione selezionata.  Le dimensioni del blocco che contiene la funzione chiamante sono proporzionali al contributo della funzione chiamante rispetto al valore totale della metrica prestazioni per la funzione selezionata.  
  
 È possibile fare clic sul nome di una funzione chiamante per selezionarla nella visualizzazione.  
  
-   Se le funzioni chiamanti da elencare sono troppe, le funzioni con i contributi meno importanti vengono raccolte in un blocco **Altro**.  Scegliere **Altro** per visualizzare tutte le funzioni chiamanti e chiamate della funzione selezionata nella finestra **Visualizzazione Chiamante\/chiamato**.  Per ulteriori informazioni, vedere [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view.md).  
  
-   Se non sono presenti funzioni chiamanti o se la funzione è la funzione di ingresso di un thread o di un processo, viene visualizzato un blocco **Inizio dello stack**.  
  
 **Funzione selezionata**  
  
 La barra della funzione selezionata mostra i contributi delle funzioni chiamate e del codice nella funzione selezionata rispetto alla metrica prestazioni totale della funzione selezionata.  Le dimensioni del blocco che contiene una funzione chiamata o il corpo della funzione sono proporzionali al relativo contributo rispetto al valore totale della metrica prestazioni per la funzione selezionata.  
  
 È possibile fare clic sul nome di una funzione chiamata per selezionarla nella visualizzazione.  
  
-   Il valore **Totale** rappresenta la metrica prestazioni per la funzione selezionata.  
  
-   Il blocco **Corpo funzione** rappresenta la quantità del valore totale della metrica prestazioni relativo all'esecuzione diretta del codice nel corpo della funzione.  
  
-   Le funzioni chiamate dalla funzione selezionata sono elencate in blocchi.  Le dimensioni del blocco delle funzioni selezionate, rappresentano l'importo delle prestazioni metriche totali per la funzione selezionata che si verificano nella funzione chiamata.  
  
-   Se le funzioni chiamanti da elencare sono troppe, le funzioni con i contributi meno importanti vengono raccolte in un blocco **Altro**.  Scegliere **Altro** per visualizzare tutte le funzioni chiamanti e chiamate della funzione selezionata nella finestra **Visualizzazione Chiamante\/chiamato**.  Per ulteriori informazioni, vedere [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view.md).  
  
-   Se non sono presenti funzioni chiamate, viene visualizzato un blocco **Fine dello stack**.  
  
## Dettagli prestazioni funzione  
 Nella tabella Dettagli prestazioni funzione sono contenuti dati di riepilogo per le metriche prestazioni della funzione selezionata.  Vengono visualizzati il valore e la percentuale.  Specificare i dati di profilo visualizzati nel grafico e nella tabella dei dettagli nell'elenco **Metrica prestazioni**.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Exclusive**|-   Valore della metrica prestazioni relativo all'esecuzione del corpo della funzione.|  
|**In chiamate**|-   Valore della metrica prestazioni relativo a funzioni chiamate dalla funzione selezionata.|  
|**Totale inclusivo**|-   Totale dei valori **Esclusivo** e **In chiamate**.|  
  
## Visualizzazione codice funzione  
 Nella finestra **Visualizzazione codice funzione** viene visualizzato un elenco del codice sorgente quando è disponibile.  Accanto alle righe di codice sorgente che chiamano altre funzioni è presente una colonna ombreggiata contenente i valori della metrica prestazioni per la funzione chiamata.  Per modificare il codice sorgente, fare clic sul collegamento al file del codice sorgente.  
  
## Valori del grafico a barre Distribuzione costi  
  
### Campionamento  
 Nella tabella seguente vengono descritti i valori nell'elenco Metrica prestazioni per i dati di profilo raccolti tramite il metodo di campionamento.  
  
|||  
|-|-|  
|**Campioni inclusivi \(campioni raccolti\)**|-   Per una funzione chiamante, numero di campioni raccolti quando la funzione selezionata è stata chiamata da questa funzione chiamante.<br />-   Per il corpo della funzione, numero di campioni raccolti durante l'esecuzione del codice della funzione selezionata.<br />-   Per una funzione chiamata, numero di campioni raccolti durante l'esecuzione della funzione chiamata in seguito a una chiamata dalla funzione selezionata.|  
  
### Strumentazione  
 Nella tabella seguente vengono descritti i valori nell'elenco Metrica prestazioni per i dati di profilo raccolti tramite il metodo di strumentazione.  
  
|||  
|-|-|  
|**Tempo inclusivo trascorso \(tempo trascorso\)**|Sono inclusi il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br /><br /> -   Per una **Funzione chiamante**, quantità di tempo trascorso durante l'esecuzione delle istanze della funzione selezionata chiamate dalla funzione.  È incluso il tempo trascorso nelle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo funzione**, quantità totale di tempo trascorso durante l'esecuzione del codice della funzione selezionata.  Non è incluso il tempo trascorso nelle funzioni chiamate.<br />-   Per una funzione chiamata, quantità di tempo trascorso durante l'esecuzione delle istanze della funzione chiamate dalla funzione selezionata.  È incluso il tempo trascorso nelle funzioni chiamate dalla funzione.  È incluso il tempo trascorso nelle funzioni chiamate dalla funzione selezionata.|  
|**Tempo inclusivo applicazione \(tempo applicazione\)**|Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br /><br /> -   Per una **Funzione chiamante**, quantità di tempo applicazione trascorso durante l'esecuzione delle istanze della funzione selezionata chiamate dalla funzione.  È incluso il tempo trascorso nelle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo funzione**, quantità totale di tempo applicazione trascorso durante l'esecuzione del codice della funzione selezionata.  Non è incluso il tempo trascorso nelle funzioni chiamate.<br />-   Per una funzione chiamata, quantità di tempo applicazione trascorso durante l'esecuzione delle istanze della funzione chiamate dalla funzione selezionata.  È incluso il tempo trascorso nelle funzioni chiamate dalla funzione.|  
  
### Memoria .NET  
 Nella tabella seguente vengono descritti i valori nell'elenco Metrica prestazioni per i dati di profilo raccolti tramite il metodo di profilo di memoria .NET.  
  
|||  
|-|-|  
|**Allocazioni inclusive \(Allocazioni\)**|-   Per una **Funzione chiamante**, numero di oggetti allocati dalle istanze della funzione selezionata chiamate dalla funzione.  Sono inclusi gli oggetti allocati dalle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo funzione**, numero di oggetti allocati dalla funzione selezionata durante l'esecuzione del codice relativo.  Non sono inclusi gli oggetti allocati nelle funzioni chiamate dalla funzione selezionata.<br />-   Per una funzione chiamata, numero di oggetti allocati dalle istanze della funzione chiamate dalla funzione selezionata.  Sono inclusi gli oggetti allocati da funzioni chiamate dalla funzione.|  
|**Byte inclusivi \(Byte\)**|-   Per una **Funzione chiamante**, il numero di byte allocati dalle istanze della funzione selezionata chiamate dalla funzione.  Sono inclusi i byte allocati dalle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo funzione**, numero totale di byte allocati dalla funzione selezionata durante l'esecuzione del codice relativo.  Non sono inclusi i byte allocati nelle funzioni chiamate dalla funzione selezionata.<br />-   Per una funzione chiamata, il numero di byte allocati dalle istanze della funzione chiamate dalla funzione selezionata.  Sono inclusi i byte allocati dalle funzioni chiamate dalla funzione.|  
  
### Concorrenza  
 Nella tabella seguente vengono descritti i valori nell'elenco Metrica prestazioni per i dati di profilo raccolti tramite il metodo di concorrenza.  
  
|||  
|-|-|  
|**Conflitti inclusivi \(conflitti\)**|-   Per una **Funzione chiamante**, numero di eventi di conflitto di risorse che si sono verificati nelle istanze della funzione selezionata chiamata dalla funzione.  Sono inclusi gli eventi di conflitto nelle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo funzione**, numero totale di eventi di conflitto che si sono verificati durante l'esecuzione del codice della funzione.  Non sono inclusi i conflitti nelle funzioni chiamate dalla funzione selezionata.<br />-   Per una funzione chiamata, numero di eventi di conflitto che si sono verificati nelle istanze della funzione chiamate dalla funzione selezionata.  Sono inclusi gli eventi di conflitto che si sono verificati nelle funzioni chiamate dalla funzione.|  
|**Tempo blocco inclusivo \(tempo blocco\)**|-   Per una funzione chiamante, tempo trascorso in eventi di conflitto di risorse per le istanze della funzione selezionata chiamate dalla funzione.  È incluso il tempo blocco trascorso nelle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo funzione**, tempo totale trascorso in eventi di conflitto che si sono verificati durante l'esecuzione del codice della funzione.  Non sono inclusi i conflitti che si verificano nelle funzioni chiamate dalla funzione selezionata.<br />-   Per una funzione chiamata, tempo trascorso in eventi di conflitto di risorse per le istanze della funzione selezionata chiamate dalla funzione selezionata.  È incluso il tempo blocco trascorso nelle funzioni chiamate dalla funzione.|