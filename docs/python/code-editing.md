---
title: Modifica del codice Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03effe56-d6f6-461d-9005-e43c15bf537c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: d16b8fcae5b7d1a14c8f6068dfd7103115cba291
ms.contentlocale: it-it
ms.lasthandoff: 07/18/2017

---

# <a name="editing-python-code"></a>Modifica del codice Python

Gli sviluppatori passano la maggior parte del tempo nell'editor di codice, quindi il [supporto per Python in Visual Studio](installation.md) offre funzionalità che consentono di migliorare la produttività. Le funzionalità includono evidenziazione della sintassi di IntelliSense, completamento automatico, supporto per la firma digitale, override dei metodi, ricerca e navigazione. 

Contenuto dell'argomento:

- [IntelliSense](#intellisense) inclusi completamenti, informazioni della Guida per le firme, informazioni rapide e colorazione del codice.
- [Frammenti di codice](#code-snippets)
- [Navigazione nel codice](#navigating-your-code)

Per informazioni generali sulla modifica del codice in Visual Studio, vedere [Scrittura di codice nell'Editor di testo e del codice](../ide/writing-code-in-the-code-and-text-editor.md). Vedere anche [Struttura](../ide/outlining.md) per informazioni su questa funzionalità che consente di concentrarsi su sezioni specifiche del codice. Il supporto di Python include l'uso del Visualizzatore oggetti di Visual Studio (**Visualizza > Altre finestre > Visualizzatore oggetti** o CTRL+W,J) per esaminare le classi definite in ogni modulo e le funzioni definite in tali classi. 

L'editor è anche integrato con la finestra interattiva in Visual Studio, semplificando così lo scambio di codice tra i due prodotti. Per informazioni dettagliate, vedere [Introduzione - Uso della finestra interattiva REPL])(getting-started.md#using-the-interactive-repl-window) e [Uso della finestra interattiva - Comando per inviare codice alla finestra interattiva](interactive-repl.md#send-code-to-interactive-command).

Per un'introduzione alla modifica del codice Python, vedere [Getting Started with Python in Visual Studio, Part 3: Editing](https://youtu.be/uZGZNEyyeKs?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introduzione a Python in Visual Studio, parte 3: modifica) (youtube.com, 3m 48s):

> [!VIDEO https://www.youtube.com/embed/uZGZNEyyeKs]

## <a name="intellisense"></a>IntelliSense

IntelliSense offre [completamenti](#completions), [informazioni della Guida per le firme](#signature-help), [informazioni rapide](#quick-info) e [colorazione del codice](#code-coloring). Per migliorare le prestazioni, IntelliSense dipende dal database di completamento generato per ogni ambiente Python nel progetto. Può essere necessario aggiornare i database se si aggiungono, si rimuovono o si aggiornano i pacchetti. Lo stato dei database viene visualizzato nella finestra **Ambienti Python**, elemento di pari livello di Esplora soluzioni, o nella scheda **IntelliSense** (vedere [Ambienti Python](python-environments.md). 

### <a name="completions"></a>Completamenti

I completamenti vengono visualizzati come istruzioni, identificatori e altre parole che possono essere immessi in modo corretto nella posizione corrente nell'editor. Il contenuto dell'elenco dipende dal contesto e viene filtrato per omettere opzioni non corrette o fonte di distrazione. I completamenti vengono spesso attivati digitando istruzioni (ad esempio `import`) e operatori (incluso un punto) diversi, ma è possibile visualizzarli in qualsiasi momento digitando CTRL+J, BARRA SPAZIATRICE.

![Completamento dei membri](media/code-editing-completions-simple.png)

Quando viene aperto un elenco di completamento, è possibile cercare il completamento desiderato usando i tasti di direzione, il mouse oppure continuando a digitare. Digitando altre lettere l'elenco viene ulteriormente filtrato per mostrare i completamenti probabili. È anche possibile usare i tasti di scelta rapida, ad esempio:

- Digitare lettere che non si trovano all'inizio del nome, come 'parse' per trovare 'argparse'
- Digitare solo le lettere che si trovano all'inizio di parole, come 'abc' per trovare 'AbstractBaseClass' o 'air' per trovare 'as_integer_ratio'
- Omettere lettere, ad esempio 'b64' per trovare 'base64'

Ecco alcuni esempi:

![Completamento dei membri con filtro](media/code-editing-completion-filtering.png)

I completamenti dei membri appaiono automaticamente quando si digita un punto dopo una variabile o un valore, insieme ai metodi e agli attributi dei tipi potenziali. Se una variabile può avere più di un tipo, l'elenco include tutte le possibilità per tutti i tipi, con informazioni aggiuntive per indicare quali tipi supportano ogni completamento. Nel caso un completamento sia supportato da tutti i tipi possibili, viene visualizzato senza annotazione.

![Completamento dei membri per più tipi](media/code-editing-completion-types.png)

Per impostazione predefinita, non vengono visualizzati i cosiddetti membri "dunder", il cui nome inizia e termina con un doppio carattere di sottolineatura. In generale, non si deve accedere direttamente a tali membri. Se tuttavia è necessario un membro di questo tipo, digitando un doppio carattere di sottolineatura iniziale i seguenti completamenti vengono aggiunti all'elenco:

![Completamento dei membri privati](media/code-editing-completion-dunder.png)

Le istruzioni `import` e `from ... import` visualizzano un elenco dei moduli che possono essere importati. Con `from ... import`, l'elenco include i membri che possono essere importati dal modulo specificato.

![Completamento per le importazioni](media/code-editing-completion-import.png)

Per le istruzioni `raise` e `except` vengono visualizzati gli elenchi di classi che probabilmente sono tipi di errore. L'elenco può non includere tutte le eccezioni definite dall'utente, ma consente di trovare rapidamente le eccezioni predefinite appropriate:

![Completamento per le eccezioni](media/code-editing-completion-exception.png)

È possibile digitare @ per iniziare un elemento Decorator e visualizzare gli elementi Decorator potenziali. Molti di questi elementi non possono essere usati come elementi Decorator. Consultare la documentazione della libreria per determinare quali usare.

![Completamento per gli elementi Decorator](media/code-editing-completion-decorator.png)

> [!Tip]
> È possibile configurare il comportamento dei completamenti tramite **Strumenti > Opzioni > Editor di testo > Python > Avanzate**. Tra le opzioni disponibili, **Filter list based on search string** (Filtra elenco in base alla stringa di ricerca) consente di applicare il filtro ai suggerimenti per il completamento durante la digitazione. Questa opzione è selezionata per impostazione predefinita. L'opzione **Member completion displays intersection of members** (Visualizza intersezione dei membri per i completamenti), inoltre, consente di visualizzare solo i completamenti supportati da tutti i tipi possibili (deselezionata per impostazione predefinita). Vedere [Opzioni - Risultati del completamento](options.md#completion-results).

### <a name="signature-help"></a>Supporto per la firma

Se si scrive codice che chiama una funzione, la guida per la firma digitale appare quando si digita la parentesi di apertura (`(`) e visualizza le informazioni della documentazione e sui parametri disponibili. Per visualizzare queste informazioni, è anche possibile usare CTRL+MAIUSC+BARRA SPAZIATRICE all'interno di una chiamata di funzione. Le informazioni visualizzate dipendono dalle stringhe di documentazione nel codice sorgente della funzione, ma includono eventuali valori predefiniti.

![Supporto per la firma](media/code-editing-signature-help.png)

> [!Tip]
> Per disabilitare le informazioni della Guida per le firme, passare a **Strumenti > Opzioni > Editor di testo > Python > Generale** e deselezionare **Completamento istruzioni > Informazioni sui parametri**.

### <a name="quick-info"></a>Informazioni rapide

Al passaggio del mouse su un identificatore viene visualizzata una descrizione comando delle informazioni rapide. In base all'identificatore, le informazioni rapide possono visualizzare i valori o i tipi potenziali, eventuale documentazione disponibile, i tipi restituiti e i percorsi delle definizioni:

![Informazioni rapide](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Colorazione del codice

La funzionalità di colorazione del codice usa le informazioni dall'analisi del codice per colorare variabili, istruzioni e altre parti del codice. Ad esempio, le variabili che fanno riferimento a moduli o classi possono essere visualizzate in un colore diverso rispetto alle funzioni o altri valori e i nomi dei parametri vengono visualizzati in un colore diverso rispetto alle variabili locali o globali. Le funzioni non appaiono in grassetto per impostazione predefinita:

![Colorazione del codice](media/code-editing-code-coloring.png)

Per personalizzare i colori, accedere a **Strumenti > Opzioni > Ambiente > Tipi di carattere e colori** e modificare le voci per Python nell'elenco **Elementi visualizzati**:

![Opzioni Tipi di carattere e colori](media/code-editing-customize-colors.png)

> [!Tip]
> Per disabilitare la colorazione del codice, passare a **Strumenti > Opzioni > Editor di testo > Python > Avanzate** e deselezionare **Miscellaneous Options > Color names based on type** (Opzioni varie > Colora i nomi in base al tipo). Vedere [Opzioni - Opzioni varie](options.md#miscellaneous-options).


## <a name="code-snippets"></a>Frammenti di codice

I frammenti di codice sono parti di codice che possono essere inserite nei file digitando una scelta rapida e premendo TAB oppure tramite i comandi **Modifica > IntelliSense > Inserisci frammento di codice** **Racchiudi tra**. Ad esempio, è possibile digitare `class` seguito da TAB per generare il resto della classe. È possibile digitare sull'elenco dei nomi e delle basi, spostarsi tra i campi evidenziati tramite TAB e quindi premere INVIO per iniziare a digitare il corpo.

![Frammenti di codice](media/code-editing-code-snippets.png)

È possibile visualizzare i frammenti di codice disponibili in Gestione frammenti di codice (**Strumenti > Gestione frammenti di codice**), selezionando **Python** come linguaggio:

![Gestione frammenti di codice](media/code-editing-code-snippets-manager.png)

Per creare frammenti personalizzati, vedere [Procedura dettagliata: creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md).
Per personalizzare i frammenti di codice, è possibile [creare un frammento di codice](https://msdn.microsoft.com/library/ms165394.aspx) e poi importarlo. 

Se si scrive un frammento di codice particolarmente utile e si vuole condividerlo, pubblicarlo in un gist e [segnalarlo a Microsoft](https://github.com/Microsoft/PTVS/issues). È possibile che venga incluso in una versione futura di Visual Studio.


## <a name="navigating-your-code"></a>Navigazione nel codice

Il supporto di Python in Visual Studio offre diversi strumenti per spostarsi rapidamente all'interno del codice, incluse le librerie per cui è disponibile codice sorgente: la [barra di spostamento](#navigation-bar), [Vai a definizione](#go-to-definition), [Passa a](#navigate-to) e [Trova tutti i riferimenti](#find-all-references). È anche possibile usare il [Visualizzatore oggetti](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser) di Visual Studio.

### <a name="navigation-bar"></a>Barra di navigazione

La barra di spostamento viene visualizzata nella parte superiore di ogni finestra dell'editor e include un elenco di definizioni su due livelli. L'elenco a discesa a sinistra contiene le definizioni di classi e funzioni di primo livello nel file corrente. L'elenco a discesa a destra visualizza un elenco di definizioni all'interno dell'ambito indicato a sinistra. Spostandosi nell'editor, gli elenchi vengono aggiornati in modo da indicare il contesto corrente ed è anche possibile selezionare una voce dagli elenchi per passarvi direttamente.

![Barra di spostamento](media/code-editing-navigation-bar.png)

> [!Tip]
> Per nascondere la barra di spostamento, passare a **Strumenti > Opzioni > Editor di testo > Python > Generale** e deselezionare **Impostazioni > Barra di spostamento**.

### <a name="go-to-definition"></a>Vai a definizione

Il comando **Vai a definizione** consente di passare velocemente dall'uso di un identificatore (ad esempio, un nome di funzione, una classe o una variabile) al codice sorgente in cui è definito. Per richiamare questo comando, è possibile fare clic con il pulsante destro del mouse su un identificatore e selezionare **Vai a definizione** oppure posizionare il punto di inserimento nell'identificatore e premere F12. Il comando viene applicato a tutto il codice e alle librerie esterne, a condizione che sia disponibile il codice sorgente. Se il codice sorgente della libreria non è disponibile, il comando **Vai a definizione** passa all'istruzione `import` pertinente per un riferimento al modulo o visualizza un errore.

![Vai a definizione](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Passa a

Il comando **Modifica > Passa a** (CTRL+virgola) consente di visualizzare una casella di ricerca nell'editor in cui è possibile digitare qualsiasi stringa e vedere le possibili corrispondenze nel codice che definisce una funzione, una classe o una variabile contenente tale stringa. La funzionalità di questo comando è simile a **Vai a definizione**, ma non richiede l'individuazione di un uso di un identificatore.

Per passare alla definizione dell'identificatore, fare doppio clic su qualsiasi nome oppure selezionarlo con i tasti di direzione e premere INVIO.

![Passa a](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Trova tutti i riferimenti

**Trova tutti i riferimenti** è un modo utile per individuare le posizioni in cui un qualsiasi identificatore specificato viene sia definito che usato, incluse importazioni e assegnazioni. Per richiamare questo comando, è possibile fare clic con il pulsante destro del mouse su un identificatore e scegliere **Trova tutti i riferimenti** o posizionare il punto di inserimento nell'identificatore e premere MAIUSC+F12. È possibile fare doppio clic su un elemento nell'elenco per passare alla relativa posizione.

![Risultati di Trova tutti i riferimenti](media/code-editing-find-all-references.png)
