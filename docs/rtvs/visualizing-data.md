---
title: Visualizzazione dei dati con R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
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
ms.openlocfilehash: cd9e0afac5c9a0975197cb65001f8f2698242b85
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


# <a name="creating-visual-data-plots-with-r"></a>Creazione di tracciati visivi dei dati con R

Il tracciato è una parte fondamentale del flusso di lavoro di un data scientist. In R Tools per Visual Studio (RTVS), tutte le attività di tracciato coinvolgono una o più finestre dei tracciati, che sono progettate per migliorare la produttività con questa attività chiave.

![Immagine banner tracciato](~/docs/rtvs/media/plotting-hero-image.png)

Contenuto dell'argomento:

- [Finestra dei tracciati](#the-plot-window)
- [Più finestre dei tracciati](#multiple-plot-windows)
- [Cronologia dei tracciati](#plot-history)
- [Modifica a livello di programmazione delle finestre dei tracciati](#programmatically-manipulating-plot-windows)

Il video seguente (2m 02s) offre una breve presentazione dei tracciati in RTVS:

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZTbKmz5RSgY" frameborder="0" allowfullscreen></iframe>

## <a name="the-plot-window"></a>Finestra dei tracciati

Una finestra dei tracciati contiene una serie di tracciati, in cui ognuno viene generato da un comando `plot`. Ad esempio, con `plot(1:100)` si crea una nuova finestra dei tracciati se non è già disponibile:

![Tracciato lineare 1 a 100](~/docs/rtvs/media/plotting-1-to-100.png)

Tecnicamente, i comandi `plot` di R eseguono il rendering dell'output a un dispositivo di grafica R; una finestra dei tracciati esegue il rendering dei contenuti di un dispositivo di grafica R, motivo per cui a ogni finestra dei tracciati viene assegnato un numero di dispositivo.

Le finestre dei tracciati sono indipendenti dai progetti di Visual Studio e rimangono aperte quando si caricano e si chiudono i progetti.

La generazione di un tracciato userà la finestra dei tracciati "attiva", salvando gli eventuali tracciati precedenti nella cronologia dei tracciati (vedere [Cronologia dei tracciati](#plot-history)). Ad esempio, immettendo `plot(100:1)` si noterà che il tracciato precedente viene sostituito con una riga verso il basso.

Come tutte le altre finestre di Visual Studio, la finestra dei tracciati supporta i layout personalizzati (vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)). Le finestre dei tracciati possono essere ancorate in diverse posizioni all'interno della cornice di Visual Studio, ridimensionate all'interno di essa o interamente estratte per il ridimensionamento separato. 

In tutti i casi il ridimensionamento di una finestra dei tracciati esegue nuovamente il rendering del tracciato per offrire la migliore qualità di immagine. In genere è consigliabile eseguire questa operazione prima di esportare il tracciato in un file o negli Appunti con i comandi descritti nella sezione successiva.

## <a name="plot-window-commands"></a>Comandi della finestra dei tracciati

La barra degli strumenti della finestra dei tracciati contiene i comandi applicabili, la maggior parte dei quali sono disponibili anche tramite il menu **R Tools > Tracciati**.

| Pulsante | Comando | Descrizione | 
| --- | --- | --- |
| ![Pulsante Nuova finestra dei tracciati](~/docs/rtvs/media/plotting-toolbar-01-new-plot-window.png) | Nuova finestra dei tracciati | Crea una finestra dei tracciati separata con la propria cronologia. Vedere [Più finestre dei tracciati](#multiple-plot-windows). |
| ![Pulsante di attivazione della finestra dei tracciati](~/docs/rtvs/media/plotting-toolbar-02-activate-plot-window.png) | Attiva finestra dei tracciati | Imposta la finestra dei tracciati corrente come finestra attiva, in modo che i comandi `plot` successivi vengano sottoposti a rendering per quella finestra. Vedere [Più finestre dei tracciati](#multiple-plot-windows). Vedere [Più finestre dei tracciati](#multiple-plot-windows). |
| ![Pulsante della finestra cronologia dei tracciati](~/docs/rtvs/media/plotting-toolbar-03-plot-history.png) | Finestra cronologia dei tracciati | Apre una finestra con tutti i tracciati nella cronologia visualizzati come miniature. Vedere [Cronologia dei tracciati](#plot-history). |
| ![Pulsanti della cronologia dei tracciati](~/docs/rtvs/media/plotting-toolbar-04-plot-history-arrows.png) | Tracciato precedente/successivo |  Passa al tracciato precedente o successivo nella cronologia. È anche possibile passare alla cronologia con CTRL+ ALT+F11 (Precedente) e CTRL+ALT F12 (Successivo). Vedere [Cronologia dei tracciati](#plot-history). |
| ![Pulsante Salva come immagine](~/docs/rtvs/media/plotting-toolbar-05-save-as-image.png)| Salva come immagine | Richiede un nome di file e salva il tracciato corrente (il contenuto della finestra nelle dimensioni della finestra) in un file di immagine. I formati disponibili sono `.png`, `.jpg`, `.bmp` e `.tif`. |
| ![Pulsante Salva come PDF](~/docs/rtvs/media/plotting-toolbar-06-save-as-pdf.png)| Salva come PDF | Salva il tracciato corrente in un file PDF, usando le dimensioni della finestra corrente. Il tracciato verrà nuovamente sottoposto a rendering in caso di ridimensionamento del PDF. |
| ![Pulsante Copia come bitmap](~/docs/rtvs/media/plotting-toolbar-07-copy-as-bitmap.png)| Copia come bitmap | Copia il tracciato negli Appunti come bitmap raster, usando le dimensioni della finestra corrente. | 
| ![Pulsante Copia come metafile](~/docs/rtvs/media/plotting-toolbar-08-copy-as-metafile.png)| Copia come metafile | Copia il tracciato negli Appunti come un [metafile di Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). | 
| ![Pulsante Rimuovi tracciato](~/docs/rtvs/media/plotting-toolbar-09-remove-plot.png)| Rimuovi tracciato | Rimuove il tracciato corrente dalla cronologia. |
| ![Pulsante Cancella tutti i tracciati](~/docs/rtvs/media/plotting-toolbar-10-clear-all-plots.png) | Cancella tutti i tracciati | Rimuove tutti i tracciati dalla cronologia (richiede una conferma). |

## <a name="multiple-plot-windows"></a>Più finestre dei tracciati

Poiché spesso i data scientist lavorano con molti tracciati provenienti da set di dati diversi, RTVS consente di creare il numero desiderato di finestre dei tracciati che è possibile disporre a piacere all'interno o all'esterno della cornice di Visual Studio. (Vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) per informazioni generali su ancoraggio e ridimensionamento delle finestre.)

Creare una nuova finestra dei tracciati con il pulsante della barra degli strumenti o **R Tools > Tracciati > Nuova finestra dei tracciati**. La nuova finestra dei tracciati diventa la finestra *attiva*, nella quale viene eseguito il rendering dei nuovi tracciati. Per modificare la finestra attiva, accedere a essa e selezionare il pulsante della barra degli strumenti Attiva finestra dei tracciati o **R Tools > Tracciati > Attiva finestra dei tracciati**.

I tracciati sono anch'essi oggetti indipendenti, ovvero è possibile copiarli o spostarli tra finestre dei tracciati usando il trascinamento della selezione, il mouse o i comandi **Copia**, **Taglia** e **Incolla** presenti nel menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse e nel menu **Modifica**.

 Il comportamento predefinito per il trascinamento della selezione è copia; per spostare, trascinare tenendo premuto MAIUSC.

## <a name="plot-history"></a>Cronologia dei tracciati

I comandi dei tracciati vengono mantenuti nella cronologia dei tracciati per ogni finestra, assicurando il mantenimento di tutti i tracciati all'interno di una sessione. Per esplorare la cronologia, usare i pulsanti freccia sulla barra degli strumenti della finestra dei tracciati o CTRL+ALT+F11 e CTRL+ALT+F12. È anche possibile rimuovere singoli tracciati o cancellare tutti i tracciati dalla finestra usando i pulsanti della barra degli strumenti o i comandi del menu **R Tools > Tracciati**.

Per visualizzare l'intera raccolta di tracciati, aprire la finestra cronologia dei tracciati usando il pulsante della barra degli strumenti o **R Tools > Tracciati > Finestra cronologia dei tracciati**.
In questo modo si ottiene un elenco di miniature per i tracciati che sono stati visualizzati in tale finestra, raggruppati in base alle diverse finestre dei tracciati (o dispositivi). Con i pulsanti dello zoom presenti sulla barra degli strumenti è possibile modificare la dimensione delle miniature.

![Finestra cronologia dei tracciati](~/docs/rtvs/media/plotting-plot-history-window.png)

Per aprire un tracciato nella finestra associata, fare doppio clic sul tracciato, selezionarlo e quindi selezionare il pulsante della barra degli strumenti **Mostra tracciato** o fare clic e scegliere **Mostra tracciato**. È anche possibile selezionare un singolo tracciato e copiarlo, tagliarlo o eliminarlo usando il menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse o il menu **Modifica**.

La durata della cronologia dei tracciati in tutte le finestre è associata alla durata della sessione di R interattiva. Se si reimposta la sessione di R o si esce e si riavvia Visual Studio, la cronologia dei tracciati verrà reimpostata.

## <a name="programmatically-manipulating-plot-windows"></a>Modifica a livello di programmazione delle finestre dei tracciati

È possibile modificare a livello di programmazione le finestre dei tracciati dal codice R, usando i numeri dei dispositivi per identificare specifiche finestre dei tracciati. 

- `dev.list()`: elenca tutti i dispositivi di grafica all'interno della sessione di R corrente.
- `dev.new()`: crea un nuovo dispositivo di grafica (una nuova finestra dei tracciati).
- `dev.set(<device number>)`: imposta il dispositivo di grafica attivo.
- `dev.off()`: elimina il dispositivo attivo.

