---
title: Progetti di esempio per R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa52ed0e-cdb5-4fb2-814c-c94cac2ffc6f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: d58ff34914af9185ce5282bdc8848db2b12f1aea
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---

# <a name="r-tools-for-visual-studio-sample-projects"></a>Progetti di esempio di R Tools per Visual Studio

Questa raccolta di esempi funge da introduzione a R, R Tools per Visual Studio (RTVS) e Microsoft R Server:

1. Scaricare il [file degli esempi con estensione zip](https://github.com/Microsoft/RTVS-docs/archive/master.zip) ed estrarne il contenuto in una cartella di propria scelta.
1. Aprire `examples/Examples.sln`; si noterà che vi sono due cartelle nel progetto:

    - *A First Look at R* (Panoramica di R) offre un'introduzione semplice per chi non ha dimestichezza con R.
    - *MRS and Machine Learning* (Microsoft R Server e apprendimento automatico) offre esempi di come usare R e Microsoft R Server per l'apprendimento automatico.

## <a name="a-first-look-at-r"></a>A First Look at R

In questo esempio viene offerta un'introduzione approfondita a R tramite la serie di commenti esaustivi nei file di origine. Il modo migliore per sperimentare questo approccio consiste nel posizionare il cursore all'inizio del file, quindi premere CTRL + INVIO per inviare ogni riga, una alla volta, alla finestra **R interattivo** in cui è possibile visualizzare i risultati. Si noti che alcune righe avvieranno l'installazione di pacchetti che potrebbe richiedere un minuto o due.

- `1-Getting Started with R.R` illustra molte nozioni fondamentali di R compresi l'uso di pacchetti, il caricamento e l'analisi dei dati e il tracciamento.

    ![Output dell'esempio 1-Getting Started with R.R](~/rtvs/media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` introduce il pacchetto di grafica ggplot2 noto per i tracciati visivamente gradevoli e la sintassi semplice. In questo esempio vengono visualizzati dati sui terremoti alle Figi.

    ![Output dell'esempio 2-Introduction to ggplot2.R](~/rtvs/media/samples-ggplot-output.png)


## <a name="microsoft-r-server-and-machine-learning"></a>Microsoft R Server e apprendimento automatico

Questa raccolta di esempi illustra come usare R e Microsoft R Server per creare modelli di apprendimento automatico e come sfruttare le funzionalità di [Microsoft R Server (MRS)](http://aka.ms/rtvs-msft-r). Si noti che è necessario installare MRS per eseguire gli script con `MRS` nel titolo e dove indicato.

Come con tutti gli esempi, il modo migliore per usarli è aprire il file, posizionare il cursore nella parte superiore e quindi eseguire il codice riga per riga con CTRL + INVIO. Vedere anche i file markdown in ogni cartella per altri dettagli.

- `Benchmarks` esegue diversi benchmark a elevato utilizzo di calcolo per visualizzare il miglioramento delle prestazioni che è possibile realizzare tramite l'uso di Microsoft R Open e delle librerie Intel Math Kernel Library (MKL) per calcoli algebrici rapidi, lineari e paralleli. Con dati simulati, confronta in particolare l'uso di due thread rispetto all'uso di uno solo per alcuni calcoli relativi alla matrice.   

    ![Tracciato di esempio Benchmark](~/rtvs/media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` crea un modello di previsione della domanda per noleggi di biciclette basato su un set di dati cronologico, usando Microsoft R Server. 

- `Data_Exploration` contiene tre script:  
    - `Import Data from URL.R` illustra come caricare in R un file di dati identificato da URL.
    - `Import Data from URL to xdf.R` illustra come caricare in Microsoft R Server un file di dati identificato da URL come xdf. (Richiede MRS).
    - `Using ggplot2.R` è un'estensione dell'esempio `A First Look at R/2-Introduction to ggplot2.R`, con una panoramica più estesa della funzionalità di ggplot2, tra cui il tracciamento 3D interattivo.

        ![Output dell'uso dell'esempio ggplot2.R](~/rtvs/media/samples-3d-interactive.png)

- `Datasets` include tre file `.csv` usati da altri esempi
- `Flight_Delays_Prediction_with_R` e `Flight_Delays_Prediction_with_MRS` illustrano come prevedere i ritardi dei voli con R, l'apprendimento automatico e lo storico delle prestazioni nei tempi stabiliti, nonché i dati meteorologici. 
- `Machine learning` include tre esempi per imparare a prevedere i ritardi dei voli, i prezzi delle abitazioni e i noleggi di biciclette, illustrando l'applicazione di R e MRS a problemi reali. Illustra anche come usare diversi modelli comuni di apprendimento automatico e distribuirli come un servizio Web di Azure tramite un'area di lavoro di [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/).

- `R_MRO_MRS_Comparison` è un confronto tra sei parti che illustra similitudini e differenze di R, Microsoft R Open e Microsoft R Server con comandi, sintassi, costrutti e prestazioni.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>I punti salienti di Microsoft R Open e Microsoft R Server.

[Microsoft R Open](http://aka.ms/rtvs-r-open), la distribuzione Microsoft di R, è diverso da [CRAN R](https://cran.r-project.org/) in due aspetti principali:

1. [Migliori prestazioni di calcolo](https://mran.revolutionanalytics.com/rro/#intelmkl1) quando usato con le librerie [Intel MKL](https://software.intel.com/intel-mkl), disponibili per il download gratuito da Microsoft per l'uso con Microsoft R Open.

1. [Toolkit di R riproducibile](https://mran.revolutionanalytics.com/rro/#reproducibility), che assicura che le librerie usate per compilare il programma di R siano sempre disponibili ad altri utenti che vogliano riprodurre il lavoro.

[Microsoft R Server](http://aka.ms/rtvs-msft-r) è un'estensione di R che consente di gestire più dati e più velocemente. Offre due funzionalità potenti per R:

1. Set di dati di grandi dimensioni. MRS può elaborare dati in caso di memoria insufficiente da un'ampia gamma di origini tra cui cluster di Hadoop, database e data warehouse. La RAM non costituirà più un limite.

1. Elaborazione parallela, multi-core. MRS può distribuire in modo efficiente i calcoli in tutte le risorse di calcolo disponibili. Nella workstation personale o in un cluster remoto MRS otterrà una risposta velocemente.

Il confronto seguente illustra come MRS e MRO con MKL abbiano prestazioni di calcolo decisamente migliori relativamente ad alcuni calcoli di matrice rispetto a R e MRO senza MKL. Per questo calcolo vengono usati dati simulati:

![Confronto tra MRS e MRO con MKL e R e MRO senza MKL](~/rtvs/media/samples-speed-comparison.png)

Per un confronto tecnico di R con MRO e MRS, vedere [la discussione dettagliata di Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) sull'argomento.

Nella figura seguente viene quindi confrontato il tempo trascorso in secondi usato per la creazione di modelli di regressione logistica per stimare se l'arrivo dei voli passeggeri programmato ritarderà di più di 15 minuti. Il tempo trascorso usato in CRAN R aumenta notevolmente all'aumento di un numero ridotto di righe, mentre MRS aumenta solo di circa due volte. Per informazioni dettagliate su questo benchmark, vedere l'esempio `Benchmarks/rxGlm_benchmark.R`.

![Benchmark rxGlm](~/rtvs/media/samples-rxGLM-benchmark.png)

