---
title: Opzioni di R Tools in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
ms.assetid: 554dc602-ecad-4cd0-8e6f-a60bb8a2328f
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
ms.openlocfilehash: 9b680c73d54c9809e3f4c46dc2841f1f320e4af9
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


# <a name="r-tools-for-visual-studio-options"></a>Opzioni di R Tools per Visual Studio
 
Le impostazioni sono accessibili tramite il menu **R Tools > Opzioni** o tramite **Strumenti > Opzioni** e quindi scorrendo fino a **R Tools**:
 
  ![Finestra di dialogo Opzioni per R Tools](~/docs/rtvs/media/options-dialog.png)

Le sezioni seguenti descrivono le diverse opzioni disponibili in questa pagina.

> [!Note]
> Quando si accede alle opzioni tramite il menu **Strumenti > Opzioni** generale, per visualizzare la pagina **R Tools** potrebbe essere necessario selezionare la casella **Mostra tutte le impostazioni** nella parte inferiore.

<a name="data-scientist-layout"</a>

È anche disponibile la voce di menu speciale **R Tools > Impostazioni di Data Science** che configura l'IDE di Visual Studio con un layout ottimizzato per le esigenze dei data scientist. In particolare, questa opzione consente di aprire le finestre [R interattivo](interactive-repl.md), [Esplora variabili](variable-explorer.md) e [Aree di lavoro](workspaces.md):

![Layout delle finestre per data scientist in Visual Studio](~/docs/rtvs/media/installation-data-scientist-layout-result.png)

> [!Important]      
> Per ripristinare le altre impostazioni di Visual Studio in un secondo momento, prima usare il comando **Strumenti > Importa/Esporta impostazioni** selezionando **Esporta le impostazioni di ambiente selezionate** e specificando un nome file. Per ripristinare tali impostazioni, usare lo stesso comando e selezionare **Importa le impostazioni di ambiente selezionate**. È possibile usare gli stessi comandi anche se si modifica il layout per i data scientist e si vuole tornarvi in un secondo momento, anziché usare direttamente il comando **Impostazioni di Data Science**.

## <a name="debugging"></a>Debug

Queste opzioni controllano la gestione dei valori in [Esplora variabili](variable-explorer.md) e all'interno di finestre del debugger quali Espressione di controllo e Variabili locali. Vedere [Debugging](debugging.md) (Debug).

| Opzione | Valore predefinito | Descrizione | 
| --- | --- | --- |
| Valuta associazioni attive | `True` | Se `True`, è sempre possibile visualizzare il valore più aggiornato durante il controllo di variabili e proprietà. Il rischio è che la valutazione delle espressioni possa causare effetti collaterali, a seconda della modalità di implementazione delle espressioni stesse. |
| Mostra variabili che includono un punto come prefisso | `False` | Specifica se devono essere visualizzate le variabili con prefisso `.`. |

## <a name="general"></a>Generale

| Opzione | Valore predefinito | Descrizione | 
| --- | --- | --- |
| Controllo sondaggio/notizie | `Once a week` | Specifica la frequenza con cui R Tools deve controllare la presenza di aggiornamenti di sondaggi e notizie nel server. | 

## <a name="help"></a>?

| Opzione | Valore predefinito | Descrizione | 
| --- | --- | --- |
| Web browser F1 | `Internal` | Controlla la modalità di visualizzazione della Guida quando si sta cercando un termine tramite CTRL + F1. Se l'opzione è impostata su `Internal`, il rendering della Guida viene eseguito all'interno di una finestra degli strumenti in Visual Studio. Se l'opzione è impostata su `External`, la Guida viene visualizzata nel Web browser predefinito. | 
| Stringa di ricerca sul Web F1 | `R site:stackoverflow.com` | Controlla il modo in cui i termini di ricerca vengono passati al motore di ricerca quando si preme CTRL + F1 per un termine nell'editor. Per impostazione predefinita la stringa è `R site:stackoverflow.com`, che aggiunge `R` al termine di ricerca. `site:stackoverflow.com` è una direttiva che indica al motore di ricerca di definire come ambito della ricerca le pagine all'interno del dominio `stackoverflow.com`. | 
| Browser della Guida di R | `Automatic` | Controlla la modalità di visualizzazione della Guida quando si sta effettuando una ricerca all'interno della documentazione di R tramite F1, `?` o `??`. Se l'opzione è impostata su `Automatic`, il rendering della Guida viene eseguito nella finestra appropriata. Ad esempio, la Guida di HTML viene visualizzata all'interno di una finestra degli strumenti di Visual Studio, mentre i PDF vengono visualizzati nel programma per PDF predefinito. Se l'opzione è impostata su `External`, il rendering della Guida viene effettuato nel Web browser predefinito. |

## <a name="history"></a>Cronologia

| Opzione | Valore predefinito | Descrizione | 
| --- | --- | --- |
| Salva sempre cronologia | `True` | Controlla se RTVS deve scrivere la cronologia dei comandi in un file `.RHistory` nella directory di lavoro ogni volta che il progetto viene chiuso. Si noti che questo si verifica anche se non si salva il progetto prima di uscire. |
| Ripristina filtro di ricerca | `True` | Determina se la finestra Cronologia può filtrare la cronologia dei comandi per visualizzare solo i comandi con sottostringhe corrispondenti al termine di filtro nella finestra di dialogo Cronologia di R. Questa impostazione determina se il filtro di ricerca della cronologia deve essere reimpostato ogni volta che si esegue un nuovo comando o se si deve passare a un nuovo progetto, che attiverà il caricamento di un file `.RHistory` diverso. L'impostazione predefinita, `True`, riduce al minimo i casi in cui si esegue un comando con un set di filtri e questo non compare nella cronologia. |
| Usa selezione multilinea | `True` | Specifica se nella cronologia è possibile selezionare un'istruzione multilinea con un solo clic. Consente anche di spostarsi con le frecce su/giù nella finestra interattiva da un'istruzione all'altra anziché da una riga all'altra. |

## <a name="html"></a>HTML

| Opzione | Valore predefinito | Descrizione | 
| --- | --- | --- |
| Browser di pagine HTML | `External` | Determina dove eseguire il rendering di contenuto quale un tracciato `ggvis` o un'applicazione `shiny`. `Internal` visualizza l'output HTML all'interno di una finestra degli strumenti in Visual Studio. `External` visualizza l'output HTML nel browser predefinito. | 

## <a name="logging"></a>Registrazione

| Opzione | Valore predefinito | Descrizione | 
| --- | --- | --- |
| Registra eventi | `Normal` | Controlla il livello di dettaglio della registrazione usata per la diagnostica di RTVS. L'impostazione predefinita, `Normal`, crea un file di log nella directory `TEMP`. Se l'opzione è impostata su `Traffic`, RTVS registra tutti i comandi e tutte le risposte della sessione corrente. Questi file di log non escono mai dal computer ma potrebbero risultare utili per la diagnosi di problemi in RTVS. |

## <a name="markdown"></a>Markdown

| Opzione | Valore predefinito | Descrizione | 
| --- | --- | --- |
| Browser di anteprima Markdown | `External` | Determina dove visualizzare l'output HTML R Markdown. `Internal` visualizza il documento HTML R Markdown all'interno di una finestra degli strumenti in Visual Studio. `External` visualizza il documento HTML R Markdown tramite il browser predefinito. | 

## <a name="r-engine"></a>Motore R

| Opzione | Valore predefinito | Descrizione | 
| --- | --- | --- |
| Tabella codici | `(OS Default)` | Imposta la tabella codici (impostazioni locali) per R. Per impostazione predefinita vengono usate le impostazioni locali sottostanti del sistema operativo. | 
| Mirror CRAN | `(Use .Rprofile)` | Imposta il mirror CRAN predefinito per l'installazione di pacchetti. L'impostazione predefinita, `Use .Rprofile`, rispetta le impostazioni mirror CRAN del file `.RProfile`. È possibile eseguire l'override di questa opzione selezionando uno dei mirror CRAN elencati nell'elenco a discesa. |
| Directory di lavoro | Cartella specifica dell'utente | Imposta la directory di lavoro corrente, che in genere viene impostata ogni volta che viene aperto un progetto. |

## <a name="workspace"></a>Area di lavoro

| Opzione | Valore predefinito | Descrizione | 
| --- | --- | --- |
| Carica area di lavoro all'apertura di un progetto | `No` | L'impostazione `Yes` consente il caricamento dei dati della sessione dal file `.RData` nell'ambiente globale quando il progetto è aperto. |
| Richiedi salvataggio area di lavoro al ripristino | `Yes` | L'impostazione `No` disabilita la richiesta di salvataggio dell'area di lavoro quando si fa clic sul pulsante Reimposta nella finestra interattiva. |
| Salva area di lavoro alla chiusura di un progetto | `No` | L'impostazione `Yes` consente il salvataggio dell'ambiente globale nel file `.RData` quando il progetto viene chiuso. |
| Mostra finestra di conferma prima di passare da un'area di lavoro all'altra | `Yes` | L'impostazione `No` disabilita la richiesta di conferma all'utente prima del passaggio da un'area di lavoro all'altra. Vedere [Passaggio da un'area di lavoro all'altra](workspaces.md#switching-between-workspaces) |
 
