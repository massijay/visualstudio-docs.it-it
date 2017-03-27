---
title: Finestra REPL interattiva di Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
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
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: f31d92f193af3fb32f61030ca52e444ae2baa60b
ms.lasthandoff: 03/10/2017

---

# <a name="working-with-the-python-interactive-window"></a>Uso della finestra interattiva di Python

In Visual Studio è disponibile una finestra REPL (Read-Evaluate-Print Loop) per ognuno degli ambienti Python, che costituisce un miglioramento rispetto alla funzionalità REPL disponibile con `python.exe` dalla riga di comando. La finestra interattiva, cui è possibile accedere con i comandi di menu **Visualizza > Altre finestre > &lt;Ambiente&gt; interattivo**, consente di immettere codice Python arbitrario e di visualizzare risultati immediati per imparare a usare le API e sperimentarle e sviluppare in modo interattivo codice funzionante da includere nei progetti.

![Finestra interattiva di Python](media/interactive-window.png)

In Visual Studio sono disponibili numerose modalità REPL tra cui scegliere:

| REPL | Descrizione | Modifica | Debug | Immagini |
| --- | --- | --- | --- | --- |
| Standard | REPL predefinito, comunica direttamente con Python | Modifica standard (su più righe e così via) | Sì, tramite `$attach` | No |
| Debug | REPL predefinito, comunica con il processo Python di cui è in corso il debug | Modifica standard | Solo debug | No |
| IPython | REPL comunica con il back-end di IPython | Comandi IPython, vantaggi di Pylab | No | Sì, inline in REPL |
| IPython senza Pylab | REPL comunica con il back-end di IPython | IPython standard | No | Sì, finestra separata | 

Questo argomento illustra le modalità REPL **Standard** e **Debug**. Per informazioni dettagliate sulle modalità IPython, vedere [Uso di IPython nella finestra interattiva](interactive-repl-ipython.md).

Per un'introduzione alla finestra interattiva di Python, vedere il video [Getting Started with Python in Visual Studio, Part 5: Interactive REPL](https://youtu.be/yc2CROtTsC0?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introduzione a PTVS, parte 5 REPL interattivo) su youtube.com (durata: 2 minuti e 51 secondi).

> [!VIDEO https://www.youtube.com/embed/yc2CROtTsC0]

## <a name="opening-an-interactive-window"></a>Apertura di una finestra interattiva

È possibile aprire la finestra interattiva per un ambiente in diversi modi.

Passare innanzitutto alla finestra Ambienti Python (**Visualizza > Altre finestre > Ambienti Python** oppure premere CTRL+K,CTRL+`) e selezionare il comando o il pulsante **Apri finestra interattiva** per un ambiente scelto.

![Collegamento Finestra interattiva nella finestra Ambienti Python](media/interactive-window-opening.png)

A questo punto, esaminare i comandi relativi alla finestra **interattiva**, disponibili per ognuno degli ambienti in **Visualizza > Altre finestre** e visualizzati in genere nella parte inferiore del menu:

![Voci di menu relative alla finestra interattiva in Visualizza > Altre finestre](media/interactive-window-menu.png)

È quindi possibile aprire una finestra interattiva nel file di avvio del progetto oppure per un file autonomo selezionando il comando di menu **Debug > Esegui progetto in Python interattivo oppure Esegui file in Python interattivo** (MAIUSC+ALT+F5):

![Menu Esegui progetto in Python interattivo](media/interactive-execute-project.png)

È infine possibile selezionare il codice nel file e usare il [comando per inviare codice alla finestra interattiva](#send-code-to-interactive) descritto più avanti.

## <a name="interactive-window-options"></a>Opzioni della finestra interattiva

È possibile controllare vari aspetti della finestra interattiva tramite l'opzione di **configurazione della finestra interattiva** nella finestra Ambienti Python oppure tramite **Strumenti > Opzioni > Strumenti Python > Finestre interattive**:

![Opzioni della finestra interattiva di Python](media/interactive-window-options.png)

Si noti che è disponibile anche un set di opzioni specifico per **Finestra debug interattivo**, che consente di controlla il comportamento durante una sessione di debug:

![Opzioni di debug della finestra interattiva di Python](media/interactive-window-debug-options.png)

## <a name="using-the-interactive-window"></a>Uso della finestra interattiva

Dopo aver aperto la finestra interattiva, è possibile iniziare a immettere codice riga per riga al prompt dei comandi di `>>>`. La finestra interattiva esegue ogni riga non appena viene immessa, tra cui l'importazione di moduli, la definizione di variabili e così via. È possibile osservare questo comportamento nelle prime due righe illustrate nell'immagine seguente:

![Finestra interattiva di Python](media/interactive-window.png)

L'unica eccezione è costituita dalle istruzioni che terminano con due punti, come nell'istruzione `for` illustrata in precedenza, perché la finestra interattiva riconosce che sono necessarie altre righe per poter eseguire correttamente il blocco di codice. In questo caso, il prompt della riga diventa `...`, per indicare che è necessario immettere altre righe per il blocco, come illustrato nella quarta e nella quinta riga della figura precedente. Quando si preme INVIO in una riga vuota, la finestra interattiva chiude il blocco e lo esegue nell'interprete.

> [!Tip]
> La finestra interattiva costituisce un miglioramento rispetto all'esperienza REPL di Python dalla riga di comando in quanto imposta automaticamente un rientro per le istruzioni che appartengono a un ambito circostante. La relativa cronologia (richiamata con la freccia su) visualizza inoltre elementi su più righe, mentre la riga di comando REPL visualizza solo singole righe.

La finestra interattiva costituisce la soluzione ideale per provare una nuova libreria. È possibile importare la libreria, esaminare i sottopacchetti, le classi e le funzioni.  Python offre tutte queste informazioni tramite la relativa funzione `help()`.  Inoltre, il supporto per Python in Visual Studio include suggerimenti e documentazione basati sui modelli di codice usati nell'editor, senza dover eseguire la libreria.  Quando si esegue il codice, Visual Studio usa le informazioni del runtime di Python per migliorare tali suggerimenti.  

<a name="meta-commands"></a> La finestra interattiva supporta anche diversi metacomandi. Tutti i metacomandi iniziano con `$` ed è possibile digitare `$help` per ottenere un elenco dei metacomandi oppure `$help <command>` per ottenere i dettagli relativi all'utilizzo di un comando specifico.

| Metacomando | Descrizione |
| --- | --- |
| `$$` | Inserisce un commento ed è quindi utile per aggiungere commenti al codice durante la sessione. |
| `$attach` | Collega il debugger di Visual Studio al processo della finestra REPL per abilitare il debug. |
| `$cls`, `$clear` | Cancella il contenuto della finestra dell'editor, lasciando intatti la cronologia e il contesto di esecuzione. |
| `$help` | Visualizza un elenco di comandi o la Guida su un comando specifico. |
| `$load` | Carica i comandi dal file e viene eseguito fino al completamento. |
| `$mod` | Consente di passare dall'ambito corrente al nome di modulo specificato. |
| `$reset` | Ripristina lo stato iniziale dell'ambiente di esecuzione, mantenendo però la cronologia. |
| `$wait` | Attende almeno il numero di millisecondi specificato. |

È anche possibile estendere i comandi tramite MEF (Managed Extensibility Framework per .NET).

## <a name="switching-scopes"></a>Passaggio a un altro ambito

Per impostazione predefinita, l'ambito della finestra interattiva di un progetto è impostato sul file di avvio del progetto, come se la finestra venisse eseguita dal prompt dei comandi. Per un file autonomo l'ambito corrisponde al file stesso. È però possibile cambiare in qualsiasi momento l'ambito durante la sessione REPL tramite il menu a discesa disponibile nella parte superiore della finestra interattiva:

![Ambiti della finestra interattiva](media/interactive-scopes.png)

Dopo aver importato un modulo, ad esempio digitando `import os`, nel menu a discesa verranno visualizzate le opzioni per passare a un qualsiasi ambito presente in tale modulo. Nella finestra interattiva verrà anche visualizzato un messaggio che indica il nuovo ambito, in modo che sia possibile tenere traccia di come si è arrivati a un determinato stato nel corso della sessione.

Se si immette `dir()` in un ambito, vengono visualizzati gli identificatori validi presenti in tale ambito, inclusi nomi di funzione, classi e variabili. Se ad esempio si usa `$mod importlib` seguito da `dir()`, viene visualizzato quanto segue:

![Finestra interattiva nell'ambito importlib](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>
## <a name="send-code-to-interactive-command"></a>Comando per inviare codice alla finestra interattiva

Oltre a lavorare direttamente nella finestra interattiva, è possibile selezionare codice nell'editor, fare clic con il pulsante destro del mouse e scegliere **Invia a finestra interattiva**:

![Comando di menu Invia a finestra interattiva](media/interactive-send-to.png)

Questo comando è utile per lo sviluppo di codice iterativo o evolutivo, tra cui il test del codice durante lo sviluppo. Dopo aver inviato una parte di codice alla finestra interattiva e averne visualizzato l'output, è ad esempio possibile premere la freccia su per visualizzare di nuovo il codice, modificarlo e testarlo rapidamente premendo CTRL+INVIO. Se si preme INVIO alla fine dell'input, si esegue il codice, mentre se lo si preme durante la digitazione viene inserito un carattere di nuova riga. Dopo aver creato il codice desiderato, è possibile copiarlo nuovamente nel file di progetto.

È anche possibile selezionare il codice, fare clic con il pulsante destro del mouse e scegliere **Invia a modulo di definizione** per cercare nel processo interattivo il modulo corrispondente al file corrente di cui è in corso la modifica. Se viene trovato il modulo corretto, il comando usa il metacomando `$mod` per passare a tale modulo (che viene incluso nella cronologia della sessione della finestra interattiva) e incolla la selezione nella finestra interattiva per eseguirne la valutazione. Questo costituisce un metodo rapido rispetto alla procedura per copiare il codice nell'editor, cambiare ambito nella finestra interattiva e incollare il codice manualmente.

## <a name="intellisense-behavior"></a>Comportamento di IntelliSense

La finestra interattiva include la funzionalità IntelliSense basata su oggetti attivi, a differenza dell'editor del codice in cui IntelliSense è basato solo sull'analisi del codice sorgente. I suggerimenti risultano quindi più corretti nella finestra interattiva, in particolare con codice generato dinamicamente. Può però capitare che funzioni con effetti collaterali, ad esempio la registrazione di messaggi, possano influire negativamente sull'esperienza di sviluppo.

Se questo costituisce un problema, modificare le impostazioni in **Strumenti > Opzioni > Strumenti di Python > Finestre interattive** nel gruppo **Modalità di completamento**:

- **Non valutare mai le espressioni**: usa il normale motore di IntelliSense per i suggerimenti.
- **Valuta solo le espressioni senza chiamate di funzione** (impostazione predefinita): vengono valutate solo espressioni semplici quali `a.b`, mentre per le espressioni che implicano chiamate, come `a().b`, viene usato il motore normale.
- **Valuta tutte le espressioni**: esegue l'espressione completa per ottenere i suggerimenti, anche se potrebbe avere effetti collaterali.
