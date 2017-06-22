---
title: Progetti in R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 732b73cf-2014-4f98-838e-4141ef9dedac
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
ms.openlocfilehash: b2e331fe3a538150845ede2534b2164393d6c5e6
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


# <a name="creating-r-projects-in-visual-studio"></a>Creazione di progetti R in Visual Studio

Un progetto R (un file `.rxproj`) identifica tutti i file di origine e di contenuto associati al progetto, contiene le informazioni di compilazione relative a ogni file, gestisce le informazioni per l'integrazione con sistemi di controllo del codice sorgente e consente di organizzare l'applicazione in componenti logici. Si noti che le informazioni relative all'area di lavoro, ad esempio l'elenco dei pacchetti installati, vengono gestite separatamente nell'area di lavoro stessa.

I progetti vengono sempre gestiti all'interno di una *soluzione* di Visual Studio, che può contenere un numero qualsiasi di progetti che possono fare riferimento l'uno all'altro. Vedere [Usare più tipi di progetto in Visual Studio](#use-multiple-project-types-in-visual-studio) più avanti.

## <a name="creating-a-new-r-project"></a>Creazione di un nuovo progetto R

1. Avviare Visual Studio.
1. Scegliere **File > Nuovo > progetto...** (CTRL+MAIUSC+N)
1. Selezionare "Progetto R" in **Modelli > R**, assegnare un nome e un percorso al progetto e selezionare **OK**:

    ![Finestra di dialogo Nuovo progetto per R in Visual Studio (RTVS in VS2017)](media/getting-started-01-new-project.png)

Verrà creato un progetto con un file `script.R` aperto nell'editor. Si noti anche che in **Esplora soluzioni** sono presenti altri due file per il progetto:

![Contenuto di un progetto R creato dal modello](media/projects-template-results.png)

Il file `.Rhistory` registra tutti i comandi immessi dall'utente nella finestra [R interattivo](interactive-repl.md). È possibile aprire una finestra dedicata per la cronologia con il comando **R Tools > Windows > Cronologia**. Tale finestra ha un pulsante della barra degli strumenti e voci di menu contestuale per cancellare il contenuto della cronologia.

Il file `rproject.rproj` consente di gestire alcune impostazioni di progetto specifiche di R non altrimenti gestite da Visual Studio:

| Proprietà | Impostazione predefinita | Descrizione |
| --- | --- | --- |
| Versione | 1.0 | La versione di R Tools per Visual Studio usata per creare il progetto. |
| RestoreWorkspace | Default | Carica automaticamente le variabili precedenti dell'area di lavoro dal file `.RData` nella directory del progetto. |
| SaveWorkspace | Default | Salva le variabili correnti dell'area di lavoro per il file `.RData` nella directory del progetto quando quest'ultimo viene chiuso. |
| AlwaysSaveHistory | Default | Salva la cronologia corrente della finestra interattiva per il file `.RHistory` nella directory del progetto quando quest'ultimo viene chiuso. |
| EnableCodeIndexing | Sì | Determina se eseguire un'attività di indicizzazione in background per velocizzare le ricerche di codice. |
| UseSpacesForTab | Sì | Determina se inserire spazi (Sì) o un carattere di tabulazione (No) quando viene premuto Tab nell'editor. |
| NumSpacesForTab | 2 | Il numero di spazi da inserire se UseSpacesForTab è impostato su Sì. |
| Codifica | UTF-8 | La codifica predefinita per i file `.R`. |
| RnwWeave | Sweave | Pacchetto da usare per la composizione di un file Rnw. |
| LaTeX | pdfLaTeX | Libreria da usare per la conversione da RMarkdwon a PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Conversione di una cartella di file in un progetto R

Se si vuole gestire all'interno di un progetto una cartella di file `.R` esistente, eseguire le operazioni seguenti:

1. Creare un nuovo progetto in Visual Studio come descritto nella sezione precedente.
1. Copiare i file nella cartella del progetto.
1. In Esplora soluzioni di Visual Studio fare clic con il pulsante destro del mouse sul progetto, selezionare **Aggiungi > Elemento esistente** e selezionare i file che si vogliono aggiungere. Quando si seleziona **OK**, questi compaiono nell'albero del progetto.
1. Per organizzare il codice in sottocartelle, fare clic con il pulsante destro del mouse sul progetto, selezionare **Aggiungi > Nuova cartella** e quindi copiare i file e tutti gli elementi esistenti sopra citati nella cartella appena creata.

## <a name="project-properties"></a>Proprietà di progetti

Per aprire le pagine delle proprietà del progetto, fare clic con il pulsante destro del mouse su **Esplora soluzioni** e selezionare **Proprietà** oppure scegliere la voce di menu **Progetto > Proprietà (nome progetto)...*. Verrà aperta una finestra con le proprietà seguenti:

| Tab | Proprietà | Descrizione |
| --- | --- | --- |
| Esegui | File di avvio | Il nome del file che viene eseguito con il comando **Source startup file** (File di avvio di origine), F5, **Debug > Avvio del debug** o **Debug > Avvia senza eseguire debug**. È possibile impostare questa proprietà anche facendo clic sul file nel progetto e selezionando **Imposta come script R di avvio**. |
| | Ripristina R interattivo durante l'esecuzione | Cancella tutte le variabili dall'area di lavoro della finestra interattiva quando si esegue il progetto. Questa operazione garantisce che non ci sia contenuto residuo dell'area di lavoro dall'esecuzione precedente. |
| | Percorso progetto remoto | Percorso di un'area di lavoro remota. |
| | Trasferisci file durante l'esecuzione | Indica se i file di progetto, soggetti al filtro in **File da trasferire**, devono essere copiati in un'area di lavoro remota a ogni esecuzione. |
| | File da trasferire | Nomi di file e caratteri jolly che indicano i file specifici da copiare un'area di lavoro remota se l'opzione **Trasferisci file durante l'esecuzione** è selezionata. |
| Impostazioni | (File Settings.R) | Le impostazioni dei progetti R derivano dai file `Settings.R` o `*.Settings.R` che si trovano all'interno del progetto. Se non è presente alcun file di impostazioni, è possibile aggiungere variabili e salvare la pagina. Un file `Settings.R` predefinito verrà creato automaticamente. È possibile aggiungere un file di impostazioni al progetto anche tramite il comando di menu **File > Aggiungi nuovo elemento...*. <br/> Le impostazioni vengono memorizzate come codice R e il file può essere originato prima di eseguire altri moduli, prepopolando in questo modo l'ambiente con le impostazioni predefinite. |

## <a name="r-specific-project-commands"></a>Comandi di progetto specifici di R

I progetti di Visual Studio supportano diversi comandi generali sia tramite il menu di scelta rapida che tramite il menu **Progetto**. Per i dettagli su queste funzionalità generali, vedere [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Tenere presente, tuttavia, che 

Per i progetti R, R Tools per Visual Studio aggiunge diversi comandi specifici al menu di scelta rapida e un certo numero di file e cartelle all'interno del progetto.

| Comando | Descrizione |
| --- | --- |
| Imposta directory di lavoro qui | Imposta la directory di lavoro della finestra R interattivo R sulla cartella del progetto. Questo comando può essere usato anche su qualsiasi sottocartella all'interno di un progetto. |
| Apri cartella superiore | Apre Esplora risorse in corrispondenza del percorso del file selezionato. | 
| Aggiungi script R | Crea e apre un nuovo file `.R` con nome predefinito. È anche possibile usare il comando **Aggiungi > Nuovo elemento...** per creare file `.R`, nonché diversi altri tipi di file. Vedere [Modelli di elemento specifici di R](#r-specific-item-templates) più avanti. |
| Aggiungi R Markdown | Crea e apre un nuovo documento `.rmd` con nome predefinito. È anche possibile usare il comando **Aggiungi > Nuovo elemento...** per creare file `.rmd`, nonché diversi altri tipi di file. Vedere [Modelli di elemento specifici di R](#r-specific-item-templates) più avanti.  | 
| Pubblica stored procedure | Avvia il processo di pubblicazione di eventuali stored procedure presenti all'interno di script R. Vedere [Uso di stored procedure di SQL Server](sql-server.md#working-with-sql-server-stored-procedures). | 

## <a name="r-specific-item-templates"></a>Modelli di elemento specifici di R

R Tools per Visual Studio include diversi modelli per tipi di file specifici. È possibile accedervi facendo clic con il pulsante destro del mouse sul progetto R e selezionando **Aggiungi > Nuovo elemento...**, tramite **Progetto > Aggiungi nuovo elemento...** o tramite **File > Nuovo > File...** e selezionando la scheda **R**. Il modo migliore per esplorare i modelli è semplicemente creare un nuovo progetto e inserirvi file di ogni tipo.

> [!Note]
> I comandi **Aggiungi > Nuovo elemento...** visualizzano anche tipi di file generici non elencati di seguito, mentre con **File > Nuovo > File...** tali tipi si trovano nella scheda **Generale**.

| Tipo di file | Descrizione |
| --- | --- |
| Script R | Un file di testo che contiene gli stessi comandi che è possibile immettere nella riga di comando R. |
| R Markdown | File contenente un documento [R Markdown](rmarkdown.md). |
| Impostazioni R | File che contiene le impostazioni applicazione R. | 
| Documentazione di R | File di documentazione di R generico che contiene solo i campi nome, alias e titolo. |
| Documentazione di R (funzione) | File di documentazione di R contenente molti campi con commenti di descrizione di una funzione. |
| Documentazione di R (set di dati) | File di documentazione di R contenente molti campi con commenti di descrizione di un set di dati. |
| Query SQL | File `.sql` vuoto. Vedere [SQL Server integration](sql-server.md) (Integrazione con SQL Server). |
| Stored procedure con R | File R con una query SQL figlio e un file modello di stored procedure figlio. Vedere [SQL Server integration](sql-server.md) (Integrazione con SQL Server). |


## <a name="use-multiple-project-types-in-visual-studio"></a>Usare più tipi di progetto in Visual Studio

Le soluzioni di Visual Studio rappresentano un modo pratico per raccogliere e gestire progetti correlati in un'unica posizione logica, consentendo un'organizzazione efficiente del codice e semplificando la collaborazione all'interno del team.

Nell'esempio seguente la soluzione contiene un progetto R con un modello compilato tramite R e Azure Machine Learning, un progetto Python/scikit-learn, un progetto C++ contenente moduli per un processo di calcolo intensivo, un progetto SQL per la gestione dei dati e un progetto Python/Bottle per il sito Web in cui viene pubblicato il risultato:

![Esplora soluzioni di Visual Studio con più progetti correlati in una soluzione](media/projects-polyglot.png)

Il progetto evidenziato in grassetto è il progetto di "avvio" per la soluzione. Per cambiarlo, fare clic con il pulsante destro del mouse su un altro progetto e selezionare **Imposta come progetto di avvio**.

> [!Note]
> Al momento, a differenza di quanto avviene con Python (vedere [Creazione di un'estensione C++ per Python](../python/cpp-and-python.md)) non esiste alcuna integrazione esplicita tra R e i linguaggi C#/C++.  Sono tuttavia disponibili librerie che consentono di creare punti di comunicazione tra R e i linguaggi C# e C++.

Per altri dettagli sulla gestione di progetti e soluzioni in generale, vedere [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).

