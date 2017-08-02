---
title: "Informazioni sui metodi di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.wizard.methodpage"
helpviewer_keywords: 
  - "strumenti per la profilatura, metodi di profilatura"
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Informazioni sui metodi di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli Strumenti di Profilatura di Visual Studio forniscono cinque metodi che è possibile utilizzare per raccogliere dati relativi alle prestazioni.  In questo argomento vengono descritti i diversi metodi e vengono suggeriti alcuni scenari nei quali può risultare appropriata la raccolta di dati con un particolare metodo.  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Campionamento](#sampling)|Raccoglie dati statistici sul lavoro eseguito da un'applicazione.|  
|[Strumentazione](#instrumentation)|Raccoglie informazioni di intervallo dettagliate su ogni chiamata di funzione.|  
|[Concorrenza](#concurrency)|Raccoglie informazioni dettagliate sulle applicazioni multi\-threading.|  
|[Memoria .NET](#net_memory)|Raccoglie informazioni dettagliate sull'allocazione di memoria .NET e sull'operazione di Garbage Collection.|  
|[Interazione tra livelli](#tier_interaction)|Raccoglie informazioni sulle chiamate di funzione ADO.NET sincrone a un database SqlServer.<br /><br /> La profilatura dell'interazione tra livelli può essere raccolta utilizzando [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], o [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)].  Tuttavia, i dati della profilatura dell'interazione tra livelli possono essere visualizzati solo in [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] o in [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].|  
  
 Mediante alcuni dei metodi di profilatura è inoltre possibile raccogliere dati aggiuntivi, ad esempio contatori di prestazioni di software e hardware.  Per ulteriori informazioni, vedere [Raccolta di dati aggiuntivi relativi alle prestazioni](../profiling/collecting-additional-performance-data.md).  
  
##  <a name="sampling"></a> Campionamento  
 Il metodo di profilatura del campionamento raccoglie dati statistici sul lavoro eseguito da un'applicazione durante l'esecuzione di una profilatura.  Il metodo di campionamento è leggero e ha un effetto limitato sull'esecuzione dei metodi dell'applicazione.  
  
 Il campionamento è il metodo predefinito degli Strumenti di Profilatura di Visual Studio.  È utile nei casi seguenti:  
  
-   Analisi iniziali delle prestazioni dell'applicazione.  
  
-   Individuazione dei problemi di prestazioni che comportano l'utilizzo del processore \(CPU\).  
  
 Il metodo di profilatura del campionamento interrompe il processore del computer a intervalli definiti e raccoglie lo stack delle chiamate di funzione.  l numeri dei campioni esclusivi vengono incrementati per la funzione in esecuzione, mentre i numeri di quelli inclusivi vengono incrementati per tutte le funzioni chiamanti nello stack di chiamate.  I rapporti di campionamento presentano i totali di questi numeri per modulo, funzione, riga di codice sorgente e istruzione profilati.  
  
 Per impostazione predefinita, il profiler imposta l'intervallo di campionamento sui cicli della CPU.  È possibile impostare il tipo di intervallo su un altro contatore di prestazioni della CPU e impostare il numero di eventi del contatore per l'intervallo.  È inoltre possibile raccogliere dati sulla profilatura dell'interazione tra livelli \(TIP\) che forniscono informazioni sulle query eseguite su un database SQL Server tramite ADO.NET.  
  
 [Raccolta di statistiche sulle prestazioni tramite il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)  
  
 [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)  
  
##  <a name="instrumentation"></a> Strumentazione  
 Il metodo di profilatura della strumentazione raccoglie dati di intervallo dettagliati per le chiamate di funzione in un'applicazione profilata.  La profilatura della strumentazione è utile per i casi seguenti:  
  
-   Individuazione di colli di bottiglia di input\/output, ad esempio l'I\/O del disco.  
  
-   Analisi dettagliata di un particolare modulo o set di funzioni.  
  
 Il metodo di strumentazione inserisce codice in un file binario che acquisisce informazioni di intervallo per ogni funzione nel file instrumentato e ogni chiamata di funzione effettuata da tali funzioni.  La strumentazione identifica inoltre quando una funzione effettua una chiamata al sistema operativo per richiedere operazioni quale la scrittura su un file.  Nei rapporti di strumentazione vengono utilizzati quattro valori per rappresentare il tempo totale impiegato in una funzione o una riga di codice sorgente:  
  
-   Inclusivo trascorso \- Il tempo totale impiegato per eseguire la funzione o la riga di codice sorgente.  
  
-   Inclusivo applicazione \- Il tempo impiegato per eseguire la funzione o la riga di codice sorgente, tranne il tempo trascorso in chiamate al sistema operativo.  
  
-   Esclusivo trascorso \- Il tempo impiegato per eseguire il codice nel corpo della funzione o nella riga di codice sorgente.  Il tempo impiegato per eseguire funzioni chiamate dalla funzione o dalla riga di codice sorgente è escluso.  
  
-   Esclusivo applicazione \- Il tempo impiegato per eseguire il codice nel corpo della funzione o nella riga di codice sorgente.  Il tempo impiegato per eseguire chiamate al sistema operativo e il tempo impiegato per eseguire funzioni chiamate dalla funzione o dalla riga di codice sorgente sono esclusi.  
  
 È inoltre possibile raccogliere contatori delle prestazioni della CPU e del software tramite il metodo di strumentazione.  
  
 [Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md)  
  
 [Raccolta di dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
 [Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)  
  
##  <a name="concurrency"></a> Concorrenza  
 La profilatura della concorrenza consente di raccogliere informazioni sulle applicazioni multithread.  La profilatura dei conflitti di risorse consente di raccogliere informazioni dettagliate sullo stack di chiamate ogni volta che ai thread concorrenti viene imposto di attenere per l'accesso a una risorsa condivisa.  La visualizzazione di concorrenza raccoglie inoltre informazioni più generali sul modo in cui l'applicazione multithread interagisce con se stessa, con l'hardware, con il sistema operativo e con altri processi nel computer host.  
  
-   Nei rapporti sui conflitti di risorse viene visualizzato il numero complessivo di conflitti e il tempo totale di attesa di una risorsa per i moduli, le funzioni, le righe di codice sorgente e le istruzioni in cui si è verificata l'attesa.  I grafici cronologia mostrano inoltre il momento in cui si sono verificati i conflitti.  
  
-   La visualizzazione di concorrenza presenta informazioni grafiche che è possibile utilizzare per individuare colli di bottiglia delle prestazioni, un sottoutilizzo della CPU, un conflitto di thread, una migrazione di thread, ritardi di sincronizzazione, aree di I\/O sovrapposte e altre informazioni.  Quando possibile, l'output grafico viene collegato ai dati dello stack di chiamate e del codice sorgente.  È possibile raccogliere i dati della visualizzazione di concorrenza solo per applicazioni da riga di comando e di Windows.  
  
 [Informazioni sui valori dei dati su conflitti di risorse](../profiling/understanding-resource-contention-data-values.md)  
  
 [Raccolta di dati di concorrenza di thread e processi](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
 [Visualizzazioni dei dati su conflitti tra risorse](../profiling/resource-contention-data-views.md)  
  
 [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)  
  
##  <a name="net_memory"></a> Memoria .NET  
 Il metodo di profilatura dell'allocazione di memoria .NET interrompe il processore del computer a ogni allocazione di un oggetto .NET Framework in un'applicazione profilata.  Quando vengono raccolti dati sulla durata degli oggetti, il profiler interrompe il processore dopo ogni Garbage Collection di .NET Framework.  
  
 Il profiler raccoglie informazioni sul tipo, sulle dimensioni e sul numero di oggetti creati in un'allocazione o eliminati in modo permanente in un'operazione di Garbage Collection.  
  
-   Quando si verifica un evento di allocazione, il profiler raccoglie informazioni aggiuntive sullo stack delle chiamate di funzione.  l numeri di allocazione esclusiva vengono incrementati per la funzione attualmente in esecuzione, mentre i numeri di quelli inclusivi vengono incrementati per tutte le funzioni chiamanti nello stack di chiamate. I rapporti di .NET presentano i totali di questi numeri per tipi, moduli, funzioni, righe di codice sorgente e istruzioni profilati.  
  
-   Quando si verifica un'operazione di Garbage Collection, il profiler raccoglie dati sugli oggetti eliminati e informazioni sugli oggetti in ogni generazione di Garbage Collection.  Alla fine dell'esecuzione dell'analisi, il profiler registra dati sugli oggetti che non sono stati eliminati in modo esplicito.  Nel rapporto Durata oggetti vengono visualizzati i totali per ogni tipo allocato nell'esecuzione della profilatura.  
  
 La profilatura di memoria .NET può essere utilizzata in modalità campionamento o strumentazione.  La modalità selezionata non influisce sui rapporti Allocazione e Durata oggetti che sono specifici della profilatura della memoria .NET:  
  
-   Quando si esegue la profilatura di memoria .NET in modalità di campionamento, il profiler.NET utilizza eventi di allocazione della memoria come intervallo e visualizza il numero di oggetti allocati e i byte totali allocati come valori inclusivi ed esclusivi nei rapporti.  
  
-   Quando si esegue la profilatura della memoria .NET in modalità strumentazione, vengono raccolte informazioni di intervallo dettagliate insieme a tutti i valori di allocazione inclusivi ed esclusivi.  
  
 [Informazioni sull'allocazione di memoria e i valori dei dati di durata di un oggetto](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
 [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)  
  
##  <a name="tier_interaction"></a> Interazione tra livelli  
 La profilatura dell'interazione tra livelli inserisce informazioni in un file dei dati di profilatura relativo alle chiamate sincrone di [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] tra una pagina di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o un'altra applicazione e un database [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  Nei dati sono inclusi il numero e l'ora delle chiamate e i tempi massimo e minimo.  È possibile aggiungere dati di interazione tra livelli ai dati di profilatura raccolti con il metodo di campionamento, strumentazione, memoria .NET o concorrenza.  
  
 ![Dati di profilo di interazione tra livelli](~/docs/profiling/media/tierinteraction_profilingtools.png "TierInteraction\_ProfilingTools")  
Dati di interazione tra livelli raccolti dagli strumenti di profilatura  
  
 [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)  
  
 [Visualizzazioni Interazioni tra livelli](../profiling/tier-interaction-views.md)  
  
## Vedere anche  
 [Procedura: Raccogliere dati sulle prestazioni per un sito Web](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)