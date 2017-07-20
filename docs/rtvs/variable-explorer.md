---
title: Esplora variabili in R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c669434-40d8-4970-92cc-502a98c8b5ab
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
ms.openlocfilehash: 7a72afdf01a9c1efb389efc893beedfc1eed87c1
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


# <a name="variable-explorer"></a>Esplora variabili

La finestra **Esplora variabili**, che è possibile aprire tramite **R Tools > Finestre > Esplora variabili** (o CTRL+8 se si usa **R Tools > Impostazioni di Data Science**), mostra tutte le variabili di un ambito specifico nella sessione di R corrente. Se, ad esempio, dopo aver aperto Esplora variabili si immettono le righe seguenti nella [finestra interattiva](interactive-repl.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```
 
La finestra Esplora variabili viene visualizzata come segue:

![Finestra Esplora variabili in Visual Studio](media/variable-explorer-window.png)

Se nella sessione è stato definito un dataframe R più complesso, è possibile spostarsi all'interno dei dati. Dopo aver eseguito `cars <- mtcars` è possibile spostarsi all'interno del set di dati espandendo i diversi nodi in Esplora variabili:
 
![Visualizzazione espansa di Esplora variabili](media/variable-explorer-expanded-results.png)
 
Per eliminare variabili, fare clic con il pulsante destro del mouse e selezionare **Elimina** oppure selezionare la variabile da eliminare e premere Canc.

È anche possibile cercare un'osservazione in un dataframe tramite la ricerca incrementale. Prima espandere i nodi del dataframe in cui si vuole eseguire la ricerca e quindi immettere i termini di ricerca nella relativa casella.

## <a name="details-table-view"></a>Vista (tabella) dei dettagli

Poiché i dati sono spesso tabulari, è possibile visualizzare qualsiasi tipo di dati complesso come tabella separata selezionando l'icona della lente di ingrandimento oppure facendo clic con il pulsante destro del mouse e selezionando **Mostra dettagli**. 

![Vista tabella di Esplora variabili](media/variable-explorer-table-view.png)

Se si fa clic sull'intestazione di una colonna, i dati vengono ordinati in base a tale colonna, alternatamente in ordine crescente e decrescente. Se si fa clic su altre colonne tenendo premuto MAIUSC, anche queste vengono prese in considerazione per l'ordinamento. Se si fa clic su una colonna senza tenere premuto MAIUSC si torna all'ordinamento in base a una sola colonna.

La sequenza in cui si fa clic sulle intestazioni di colonna determina l'ordine in cui viene eseguito l'ordinamento. Se ad esempio tenendo premuto MAIUSC si fa clic sulla colonna **cyl** e quindi due volte su **mpg**, l'elenco viene ordinato per cilindri in ordine crescente e per miglia per gallone in ordine decrescente:

![Vista tabulare dell'ordinamento dei dati in base a due colonne.](media/variable-explorer-table-view-sorting.png)

Dato che Esplora variabili e le viste delle tabelle si trovano in finestre di Visual Studio separate, è possibile disporle nel modo voluto per usarle affiancate. Vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) per istruzioni generali.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Visualizzare le variabili in Excel o in un'altra applicazione in grado di supportare file CSV

Per altre operazioni di manipolazione e analisi è spesso utile esportare le variabili di sessione in formato CSV. È possibile eseguire questa operazione con l'icona di Excel di piccole dimensioni (![icona di esportazione in Excel](media/variable-explorer-excel-icon.png)) accanto a ogni nodo in Esplora variabili o facendo clic con il pulsante destro del mouse su un elemento e selezionando **Apri in app CSV**. Se si seleziona l'icona i dati vengono scritti in un nuovo file CSV nella cartella `%userprofile%\Documents\RTVS_CSV_Exports` e il file verrà aperto nell'applicazione associata all'estensione `.csv`.

## <a name="scopes"></a>Ambiti

Per impostazione predefinita, all'apertura l'ambito di Esplora variabili è l'ambito globale. È possibile passare all'ambito di un pacchetto selezionando il pacchetto dall'elenco a discesa nella parte superiore della finestra.

![Esplora variabile con l'ambito di un pacchetto](media/variable-explorer-package-scopes.png)

È anche possibile passare all'ambito di una funzione in caso di arresto in corrispondenza di un punto di interruzione nel debugger. Si noti che Esplora variabili non passa automaticamente all'ambito della funzione del codice in fase di debug:

![Esplora variabili con un dataframe durante il debug](media/variable-explorer-as-locals-window.png)

Esplora variabili modifica automaticamente l'ambito di funzione man mano che scorre il codice nel debugger, ad esempio mostrando le variabili locali di una funzione.


## <a name="importing-data-into-variable-explorer"></a>Importazione di dati in Esplora variabili

Due comandi sulla barra degli strumenti di Esplora variabili, disponibili anche nel menu **R Tools > Dati**, consentono di importare set di dati CSV esterni nella sessione di R: **Importa set di dati in una sessione di R da un URL Web** e **Importa set di dati in una sessione di R da un file di testo**. 

Dopo avere identificato il file CSV da importare, R Tools per Visual Studio visualizza la finestra di dialogo **Importa set di dati**, in cui sono disponibili opzioni per controllare la modalità di analisi del file di dati (ovvero per definire il separatore di campo e la modalità di gestione delle virgolette) ed è possibile visualizzare un'anteprima del dataframe importato e del file di dati originale:

![Finestra di dialogo Importa set di dati](media/variable-explorer-import-dataset-dialog.png)
