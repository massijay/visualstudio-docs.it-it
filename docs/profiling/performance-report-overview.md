---
title: "Panoramica dei report degli strumenti per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, informazioni sui report di prestazioni"
  - "prestazioni, report"
  - "report di prestazioni, informazioni"
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
caps.latest.revision: 45
caps.handback.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Panoramica dei report degli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile visualizzare i dati di profilatura di una sessione di prestazioni nella finestra **Rapporto di prestazioni** dell'ambiente di sviluppo integrato \(IDE\) di sviluppo di Visual Studio Team System.  I dati di profilatura vengono salvati in file vsp e vsps.  Le finestre delle visualizzazioni dei rapporti consentono di esaminare e analizzare i problemi relativi alle prestazioni dell'applicazione.  
  
> [!CAUTION]
>  Un file di dati di profilatura contiene informazioni riservate quali il nome del computer, la versione del sistema operativo, i percorsi dei file, le informazioni sulla memoria e altri dati relativi alle impostazioni del computer.  È necessario un controllo rigoroso della distribuzione dei dati sia nel formato nativo vsp, che nel formato di esportazione csv o xml.  
>   
>  Se vengono raccolti dati della traccia eventi durante la sessione di prestazioni, è possibile che nel file di log relativo all'analisi eventi \(etl\) vengano visualizzate informazioni aggiuntive,  come il nome utente e il dominio. Sarà pertanto necessario controllare rigorosamente anche la distribuzione del file di log.  
  
## Finestra Rapporto di prestazioni  
 La finestra Rapporto di prestazioni fornisce gli strumenti per visualizzare, gestire e filtrare i dati di prestazioni e un controllo query personalizzabile.  
  
 Nella barra degli strumenti principale della finestra Rapporto di prestazioni è possibile accedere ad ognuna delle visualizzazioni.  Fare clic sulla freccia accanto all'elenco **Visualizzazione corrente** per visualizzare e selezionare le singole visualizzazioni disponibili.  
  
 La finestra Rapporto di prestazioni offre le visualizzazioni di dati seguenti:  
  
### Visualizzazione Riepilogo  
 Per impostazione predefinita, i dati di profilatura vengono visualizzati nella visualizzazione Riepilogo  che rappresenta il punto di partenza per la profilatura finalizzata all'identificazione dei problemi di prestazioni.  Da ogni riga della visualizzazione Riepilogo è possibile spostarsi a visualizzazioni più dettagliate facendo clic con il pulsante destro del mouse sul nome del modulo o della funzione.  Per ulteriori informazioni, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
### Visualizzazione Chiamante\/Chiamato  
 La visualizzazione Chiamante\/chiamato contiene la struttura ad albero delle chiamate per una singola funzione.  Questa visualizzazione è suddivisa in tre parti:  
  
-   La funzione di destinazione viene riportata nella parte centrale della visualizzazione.  
  
-   Le funzioni che hanno chiamato la funzione \(chiamanti\) sono visualizzate sopra la funzione di destinazione.  
  
-   Le funzioni che sono chiamate dalla funzione di destinazione \(chiamate\) sono visualizzate sotto la destinazione.  
  
 È possibile selezionare una funzione diversa facendo doppio clic su qualsiasi funzione nell'elenco delle funzioni chiamanti o chiamate.  Per ulteriori informazioni, vedere [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view.md).  
  
### Visualizzazione Struttura ad albero delle chiamate  
 La visualizzazione Albero delle chiamate contiene i percorsi di esecuzione della funzione utilizzati nell'applicazione profilata.  La radice della struttura ad albero è il punto di ingresso nell'applicazione o nel componente.  Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati delle prestazioni delle relative chiamate di funzione.  
  
 Nella visualizzazione Albero delle chiamate è possibile anche espandere ed evidenziare il percorso di esecuzione di una funzione che ha impiegato più tempo o che è stata campionata con più frequenza.  Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sulla funzione, quindi fare clic su **Espandi percorso ricorrente**.  Per ulteriori informazioni, vedere [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view.md).  
  
### Visualizzazione Processo  
 La visualizzazione Processo contiene i dati relativi alle prestazioni per ogni processo e thread profilato.  Per ulteriori informazioni, vedere la classe [Visualizzazione Processo](../profiling/process-view.md).  
  
### Visualizzazione Moduli  
 La visualizzazione Moduli contiene l'elenco dei moduli nel progetto e i dati di profilatura per ogni modulo.  Espandere o comprimere il nome del modulo per visualizzare i dati di profilatura della funzione.  Quando i dati vengono raccolti tramite campionamento, sono disponibili anche i dati di profilatura delle righe del codice sorgente e dei puntatori alle istruzioni.  Per ulteriori informazioni, vedere [Visualizzazione Moduli](../profiling/modules-view.md).  
  
### Visualizzazione Funzioni  
 Nella visualizzazione Funzioni sono elencate le funzioni chiamate durante la profilatura.  Per ulteriori informazioni, vedere [Visualizzazione Funzioni](../profiling/functions-view.md).  
  
### Visualizzazione Riga  
 La visualizzazione Righe consente di visualizzare le righe del codice sorgente specifiche che sono state eseguite durante la profilatura mediante campionamento.  Per ulteriori informazioni, vedere [Visualizzazione Righe](../profiling/lines-view.md).  
  
### Visualizzazione Puntatore all'istruzione  
 La visualizzazione Puntatore all'istruzione consente di visualizzare le istruzioni specifiche che sono state eseguite durante la profilatura mediante campionamento.  Per ulteriori informazioni, vedere la classe [Visualizzazione Puntatori all'istruzione](../profiling/instruction-pointers-ips-view.md).  
  
### Visualizzazione Allocazione  
 La visualizzazione Allocazione è disponibile se è stato selezionato **Raccogliere le informazioni sull'allocazione dell'oggetto .NET** nella pagina **Generale** della finestra di dialogo delle proprietà **Sessione prestazioni**.  Per informazioni, vedere [Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md).  La visualizzazione Allocazione contiene l'elenco degli oggetti .NET allocati dall'applicazione o dal componente.  Quando si espande una riga dell'oggetto, viene visualizzato la struttura ad albero delle chiamate  che indica i percorsi di esecuzione utilizzati per la creazione dell'oggetto.  Nella struttura ad albero delle chiamate vengono anche visualizzate le informazioni sul numero delle allocazioni inclusive ed esclusive per ogni funzione.  Nella visualizzazione Allocazione è possibile anche espandere ed evidenziare il percorso di esecuzione di una funzione che ha allocato il maggior numero di oggetti.  Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sulla funzione, quindi fare clic su **Espandi percorso ricorrente**.  Per ulteriori informazioni, vedere [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) e [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md).  
  
### Visualizzazione Durata oggetti  
 La visualizzazione Durata oggetti è disponibile se è stato selezionato **Raccogliere le informazioni sull'allocazione dell'oggetto .NET** e **Raccogliere anche le informazioni sulla durata dell'oggetto .NET** nella pagina **Generale** della finestra di dialogo delle proprietà **Sessione prestazioni** .  
  
 Nella visualizzazione Durata oggetti viene visualizzato il numero totale di istanze di ogni tipo e il numero di oggetti raccolti in ogni generazione Garbage Collection.  Per ulteriori informazioni, vedere [Visualizzazione Durata oggetti](../profiling/object-lifetime-view.md).  
  
## Controllo filtro personalizzabile  
 Il controllo filtro personalizzabile presenta le seguenti opzioni:  
  
-   **Importa filtro** \- recupera una query personalizzata precedentemente salvata.  
  
-   **Esporta filtro** \- salva la query personalizzata nel percorso specificato.  
  
-   **Esegui query** \- esegue la query come visualizzata nel controllo query personalizzata.  
  
-   **Interrompi query** \- arresta una query in esecuzione.  Questo pulsante non è disponibile se nessuna query è in esecuzione.  
  
-   **Mostra query** \- mostra\/nasconde il controllo query personalizzata.  
  
-   **Salva rapporto analizzato** \- salva il rapporto con l'analisi corrente come file vsps.  
  
-   **Esporta** \- salva il rapporto corrente come file in formato CVS o XML, con opzioni per salvare le diverse visualizzazioni.  
  
## Vedere anche  
 [Analisi dei dati degli strumenti per la profilatura](../profiling/analyzing-performance-tools-data.md)   
 [Visualizzazioni dei report degli strumenti per la profilatura](../profiling/performance-report-views.md)