---
title: Introduzione a R per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39228cf0-8d21-43bb-a2ce-5e5fdc81ec41
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
ms.openlocfilehash: 27c16d7315acaa0efd4aa8b866b44784ffe056a4
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---

# <a name="getting-started-with-r-tools-for-visual-studio"></a>Introduzione a R Tools per Visual Studio

Dopo aver installato R Tools per Visual Studio (RTVS), da [How to install R Tools for Visual Studio](installation.md) (Procedura: Installare R Tools per Visual Studio), è possibile farsi rapidamente un'idea dell'esperienza offerta da tali strumenti. Nelle sezioni seguenti viene presentata una breve panoramica:

- [Creare un progetto R](#create-an-r-project)
- [Esplorare la finestra interattiva e IntelliSense](#explore-the-interactive-window-and-intellisense)
- [Scoprire le funzionalità di modifica del codice](#experience-code-editing-features)
- [Debug del codice](#debugging-your-code)
- [Passaggi successivi](#next-steps)

## <a name="create-an-r-project"></a>Creare un progetto R

1. Avviare Visual Studio.
1. Scegliere **File > Nuovo > Progetto** (CTRL+MAIUSC+N)
1. Selezionare "Progetto R" in **Modelli > R**, assegnare un nome e un percorso al progetto e selezionare **OK**:

   ![Finestra di dialogo Nuovo progetto per R in Visual Studio (RTVS in VS2017)](media/getting-started-01-new-project.png)

1. Una volta creato il progetto, si noterà quanto segue:

    - Nella parte destra in Esplora soluzioni di Visual Studio viene visualizzato il progetto all'interno di un oggetto contenitori *soluzione*. Le soluzioni possono contenere un numero qualsiasi di progetti di tipi diversi. Per altri dettagli, vedere [Creating R projects in Visual Studio](projects.md) (Creazione di progetti R in Visual Studio).
    - In alto a sinistra viene visualizzato un nuovo file di R (`script.R`) in cui è possibile modificare il codice sorgente con tutte le funzionalità di modifica di Visual Studio.
    - In basso a sinistra viene visualizzata la finestra **R interattivo** in cui è possibile sviluppare e testare il codice in modo interattivo.

> [!Note]
> È possibile usare la finestra **R interattivo** senza che vi siano progetti aperti e anche quando è stato caricato un tipo di progetto diverso. È sufficiente selezionare in qualsiasi momento **R Tools > Windows > R interattivo**.

## <a name="explore-the-interactive-window-and-intellisense"></a>Esplorare la finestra interattiva e IntelliSense

1. Accertarsi che la finestra interattiva funzioni digitando `3 + 4` e quindi scegliendo INVIO per visualizzare il risultato:

    ![Finestra R interattivo in Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Immettere un codice un po' più complicato, `ds <- c(1.5, 6.7, 8.9) * 1:12`, e immettere `ds` per visualizzare il risultato:

    ![Altro esempio interattivo per R in Visual Studio](media/getting-started-03-interactive2.png)

1. Digitare `mean(ds)` ma si noti che non appena si digita `m` o `me`, Visual Studio IntelliSense avvia le opzioni di completamento automatico, come illustrato di seguito. Quando viene selezionato il completamento che si vuole scegliere nell'elenco, premere TAB per inserirlo. È possibile modificare la selezione con il mouse o i tasti di direzione.

    ![Visualizzazione di IntelliSense quando si immette codice](media/getting-started-04-intellisense1.png)

1. Dopo aver completato `mean`, digitare la parentesi aperta `(`. Si noterà che IntelliSense visualizza la Guida in linea per la funzione:

    ![IntelliSense visualizza la Guida in linea per una funzione](media/getting-started-05-intellisense2.png)

1. Completare la riga `mean(ds)` e premere INVIO per visualizzare il risultato (`[1] 39.51667`).

1. La finestra interattiva è integrata con la Guida, quindi immettere `?mean`, ad esempio, per visualizzare la Guida per tale funzione nella finestra **Guida di R** in Visual Studio. Per altre informazioni su questa funzionalità, vedere [Help in R Tools for Visual Studio](getting-started-help.md) (Guida di R Tools per Visual Studio).

    ![Finestra Guida di R in Visual Studio](media/getting-started-06-help.png)

1. Alcuni comandi, come ad esempio `plot(1:100)`, aprono una nuova finestra in Visual Studio quando non è possibile visualizzare l'output direttamente nella finestra interattiva:

    ![Visualizzazione di un tracciato in Visual Studio](media/getting-started-07-plot-window.png)

La finestra interattiva consente anche di rivedere la cronologia, caricare e salvare le aree di lavoro, collegarsi a un debugger e interagire con i file di codice sorgente per le operazioni di scelta rapida copia e incolla. Per altri dettagli, vedere [Uso della finestra R interattivo](interactive-repl.md).

## <a name="experience-code-editing-features"></a>Scoprire le funzionalità di modifica del codice

L'uso semplice che è stato fatto della finestra interattiva nella sezione precedente ha consentito di illustrare le funzionalità di modifica di base come IntelliSense, che possono essere usate anche nell'editor di codice. Se si immette lo stesso codice, si noteranno gli stessi prompt di completamento automatico e di IntelliSense, ma non l'output, ovviamente.

Se si scrive il codice in un file `.R`, è possibile visualizzare tutto il codice in una sola volta ed è quindi più facile apportare piccole modifiche a diverse parti del codice e visualizzarne il risultato eseguendolo rapidamente nella finestra interattiva. È anche possibile avere quanti file si voglia in un solo progetto. Quando il codice si trova in un file è anche possibile eseguirlo un'istruzione per volta nel debugger, come vedremo più avanti. Tutto ciò è molto utile quando si sviluppano algoritmi di calcolo e si scrive codice per modificare uno o più set di dati, soprattutto quando si vogliono esaminare tutti i risultati intermedi.

Ad esempio, la procedura seguente crea un breve codice per esplorare i [teoremi centrali del limite](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). Questo esempio è stato adattato da *R Cookbook* di Paul Teetor.

1. Nell'editor `script.R` immettere il codice seguente:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Per visualizzare rapidamente i risultati, selezionare tutto il codice, premendo CTRL + A, e premere CTRL + INVIO o fare clic con il pulsante destro del mouse e scegliere **Esegui in finestra interattiva**. In questo modo tutto il codice selezionato viene immesso nella finestra interattiva come se fosse stato digitato direttamente. Il risultato viene poi visualizzato nella finestra del tracciato:

    ![Visualizzazione di un tracciato in Visual Studio](media/getting-started-08-plot1.png)

1. Per una singola riga è sufficiente premere CTRL + INVIO in qualsiasi momento per eseguire la riga nella finestra interattiva.

> [!Tip]
> È consigliabile imparare a eseguire le modifiche e premere CTRL + INVIO, oppure selezionare tutto con CTRL + A e quindi premere CRTRL + INVIO per eseguire il codice rapidamente. Questa procedura è molto più efficiente rispetto all'uso del mouse per le stesse operazioni.
> 
> È anche possibile trascinare e rilasciare la finestra del tracciato fuori dalla cornice di Visual Studio e posizionarlo in qualsiasi punto dello schermo. In questo modo è possibile ridimensionare la finestra del tracciato alle dimensioni che si preferiscono e quindi salvarlo in un'immagine o un file con estensione pdf.

1. Aggiungere altre righe di codice da includere in un secondo tracciato:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))    
    lines(density(samp.means))
    ```

1. Premere nuovamente CTRL + A e CTRL + INVIO per rieseguire il codice e produrre quanto segue:

    ![Doppio tracciato aggiornato in Visual Studio](media/getting-started-09-plot2.png)

1. Il problema è che la scala verticale viene determinata dal primo tracciato, quindi il secondo (con `lines`) non vi rientra. Per risolvere il problema, impostare il parametro `ylim` della chiamata `plot`, ma per eseguire questa operazione correttamente è necessario aggiungere codice per calcolare il valore verticale massimo. Eseguire questa operazione riga per riga nella finestra interattiva non è pratico, in quanto sarebbe necessario modificare il codice per usare `samp.means` prima di chiamare `plot`. In un file di codice tuttavia, è possibile apportare facilmente le modifiche appropriate:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. Selezionare ancora CTRL + A e CTRL + INVIO per visualizzare il risultato:

    ![Doppio tracciato aggiornato in Visual Studio, ridimensionato correttamente](media/getting-started-10-plot3.png)

Nell'editor è possibile eseguire altre operazioni. Per informazioni dettagliate, vedere [Editing R code in Visual Studio](code-editing.md) (Modifica di codice R in Visual Studio), [IntelliSense](code-intellisense.md), e [Code snippets](code-snippets.md) (Frammenti di codice).

## <a name="debugging-your-code"></a>Debug del codice

Uno dei principali vantaggi di Visual Studio è l'interfaccia utente di debug. RTVS si basa su queste fondamenta solide e aggiunge un'interfaccia utente innovativa, come ad esempio [Esplora variabili e il visualizzatore di tabelle di dati](variable-explorer.md). In questo caso, vedremo solo brevemente il debug.

1. Per iniziare, reimpostare l'area di lavoro corrente per cancellare tutto quanto fatto finora tramite il comando di menu **R Tools > Sessione > Reimposta**. Per impostazione predefinita, tutte le operazioni eseguite nella finestra interattiva vengono aggiunte alla sessione corrente, che viene usata anche dal debugger. Reimpostare la sessione consente di essere certi che la sessione di debug verrà avviata senza dati pre-esistenti, se è questo ciò che si vuole. Si noti che ciò non ha alcun effetto sul file di origine `script.R`, poiché questo viene gestito e salvato fuori dell'area di lavoro.

1. Con il file `script.R` creato nella sezione precedente, impostare un punto di interruzione sulla riga che inizia con `pop <-` posizionando il cursore sulla riga e premendo F9 o selezionando il comando di menu **Debug > Imposta/Rimuovi punto di interruzione**. È possibile eseguire questa operazione in un unico passaggio facendo clic sul margine sinistro, o sul margine rilegatura, della riga, laddove viene visualizzato il punto di interruzione rosso:

    ![Impostazione di un punto di interruzione nell'editor](media/getting-started-11-debug1.png)

1. Avviare il debugger con il codice in `script.R` selezionando il pulsante **Source startup file** (File di avvio di origine) sulla barra degli strumenti, selezionando le voci di menu **Debug > Source startup file** (File di avvio di origine), o premendo F5. In questo modo si avvia la modalità di debug di Visual Studio e viene eseguito il codice. L'esecuzione del codice si interrompe, tuttavia, nel punto in cui è stato impostato il punto di interruzione:

    ![Arresto in corrispondenza del punto di interruzione nel debugger di Visual Studio](media/getting-started-12-debug2.png)

1. Durante il debug, Visual Studio consente di esaminare il codice riga per riga, nonché di eseguire funzioni o di uscire dalle funzioni, nel contesto di chiamata. Queste funzionalità, insieme ad altre, sono disponibili nel menu **Debug**, nel menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse, e nella barra degli strumenti Debug:

    ![Barra degli strumenti Debug in Visual Studio](media/getting-started-13-debug3.png)

1. Quando l'esecuzione si arresta in corrispondenza del punto di interruzione, è possibile esaminare i valori delle variabili. Individuare la finestra **Auto** in Visual Studio e selezionare la scheda nella parte inferiore denominata **Variabili locali**. La finestra **Variabili locali** visualizza le variabili locali nel punto corrente all'interno del programma. Se il programma è stato arrestato in corrispondenza del punto di interruzione impostato in precedenza, si noterà che la variabile `pop` non è ancora definita. A questo punto usare il comando **Debug > Esegui istruzione/routine** (F10). Verrà visualizzato il valore per pop:

    ![Finestra Variabili locali in Visual Studio](media/getting-started-14-debug4.png)

1. Per esaminare le variabili in ambiti diversi, tra cui l'ambito globale e gli ambiti package, usare [Esplora variabili](variable-explorer.md) illustrato di seguito. Esplora variabili offre anche la possibilità di passare a una visualizzazione tabulare con colonne ordinabili e di esportare i dati in un file con estensione csv.

    ![Visualizzazione estesa di Esplora variabili](media/variable-explorer-expanded-results.png)

1. È possibile continuare l'esecuzione del programma riga per riga oppure selezionare **Continua** (F5) per completare l'esecuzione fino alla fine, o fino al punto di interruzione successivo.

Per informazioni più approfondite, vedere [Debugging in R Visual Studio](debugging.md) (Debug in R Visual Studio) e [Variable Explorer](variable-explorer.md) (Esplora variabili).

## <a name="next-steps"></a>Passaggi successivi

In questa procedura dettagliata sono state illustrate le nozioni di base dei progetti di R, usando la finestra interattiva, la modifica del codice e il debug in Visual Studio. Per continuare a esplorare altre funzionalità, vedere gli argomenti seguenti, nonché quelli illustrati nella tabella dei contenuti:

- [Progetti di esempio per R Tools per Visual Studio](getting-started-samples.md)
- [Editing R code in Visual Studio](code-editing.md) (Modifica di codice R in Visual Studio)
- [Debug](debugging.md)
- [Workspaces](workspaces.md) (Aree di lavoro)
- [Visualizing data](visualizing-data.md) (Visualizzazione di dati)

