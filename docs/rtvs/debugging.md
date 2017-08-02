---
title: Debug con R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
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
ms.openlocfilehash: 01bc916eb656cb8e24279498b7b0236fb8eb0e80
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


# <a name="debugging-r-in-visual-studio"></a>Debug di R in Visual Studio

R Tools per Visual Studio (RTVS) si integra con l'esperienza di debug completa di Visual Studio (vedere [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)), tra cui i punti di interruzione, il collegamento a processi in esecuzione, l'ispezione e il controllo di variabili, l'analisi dello stack di chiamate e così via. In questo argomento vengono quindi esaminati gli aspetti del debug che sono univoci per R e RTVS.

Avviare il debugger per un il file di avvio R in un progetto di R è un'operazione identica a quella per altri tipi di progetto: usare **Debug > Avvia debug**, F5, o il **Source startup file** (File di avvio di origine) sulla barra degli strumenti di debug illustrata di seguito. Per modificare il file di avvio, fare clic con il pulsante destro del mouse su un file in Esplora soluzioni e selezionare **Imposta come script R di avvio**.

![Pulsante di avvio del debugger per R](~/rtvs/media/debugger-start-button.png)

In tutti i casi, il debug "dà origine" al file nella finestra interattiva, ovvero lo carica e lo esegue da qui. Quando si avvia il debug, infatti, verrà visualizzato un output simile al seguente nella finestra interattiva:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Si noti che viene usata la funzione `rtvs::debug_source` per eseguire lo script di origine. Ciò è obbligatorio perché RTVS necessita di modificare il codice in preparazione al debug. Se si usa uno dei comandi RTVS, ad esempio facendo clic con il pulsante destro del mouse su un file in Esplora soluzioni ed eseguendo il comando **File di origine selezionati**, la chiamata verrà reindirizzata automaticamente a `rtvs::debug_source` se il debugger è allegato.

È anche possibile allegare manualmente il debugger dalla finestra interattiva direttamente usando il comando **R Tools > Sessione > Collega debugger**, il comando **Debug > Collega a R interattivo**, o il comando **Collega debugger** sulla barra degli strumenti della finestra interattiva. Dopo avere eseguito questa operazione, è necessario che l'utente recuperi i file di cui vuole eseguire il debug. Se si vuole chiamare i file manualmente, assicurarsi di usare `rtvs::debug_source` e non il normale comando `source` in R. Anche se è possibile che tale comando funzioni in _alcuni_ casi, non è possibile essere certi che funzioni in tutti i casi a meno che non si usi il comando `rtvs::debug_source`.

Questa connessione tra il debugger e la finestra interattiva semplifica alcune operazioni, come ad esempio la chiamata e il debugging di una funzione con valori di parametro diversi. Ad esempio, si supponga di avere una funzione simile alla seguente in un file che è stato caricato nella sessione:

```R
add <- function(x, y) {
    return(x + y)
}
```

Impostare quindi un punto di interruzione nell'istruzione `return`. A questo punto, nella finestra interattiva se si immette `add(4,5)`, si noterà che il debugger si arresta nel punto di interruzione.


## <a name="environment-browser-in-the-interactive-window"></a>Browser ambiente nella finestra interattiva

Quando il debugger si arresta, viene arrestato anche il prompt del browser di ambiente nella [finestra interattiva](interactive-repl.md). Il prompt viene visualizzata come `Browse[n]>` dove n è un numero.

Il browser ambiente supporta un numero di comandi speciali:

| Comando | Descrizione | 
| --- | --- |
| n | next: esegue l'istruzione successiva nel file di codice (uguale a step over). |
| s | step into: esegue l'istruzione successiva nel file di codice, passando all'ambito della funzione se l'istruzione successiva è una chiamata di funzione. | 
| f | finish: esegue il resto dell'ambito della funzione corrente e restituisce al chiamante (uguale a step out). |
| c, cont | continue: esegue il programma fino al punto di interruzione successivo. | 
| Q | quits: termina la sessione di debug. |
| dove | show stack: consente di visualizzare lo stack di chiamate nella finestra interattiva. |
| guida | show help: consente di visualizzare le chiamate disponibili nella finestra interattiva. |
| &lt;expr&gt; | valuta l'espressione in *expr*. |

![Browser ambiente nella finestra interattiva](~/rtvs/media/debugger-environment-browser.png)

