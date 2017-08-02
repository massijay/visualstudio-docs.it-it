---
title: Scrivere codice nell&quot;editor del codice | Microsoft Docs
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, go to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- go to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 44
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 7b3cc733a1a808f60a27332024bcfff1dd9e670b
ms.contentlocale: it-it
ms.lasthandoff: 05/13/2017

---
# <a name="write-code-in-the-code-editor"></a>Scrivere codice nell'editor del codice
L'editor di Visual Studio include diverse funzionalità che semplificano la scrittura e la gestione di codice e testo. È possibile espandere e comprimere diversi blocchi di codice usando la struttura. Per altre informazioni sul codice in uso, vedere IntelliSense, **Visualizzatore oggetti** e Gerarchia di chiamata. Per trovare il codice, è possibile usare funzionalità quali **Vai a**, **Vai a definizione** e **Trova tutti i riferimenti**. È possibile inserire i blocchi di codice con i frammenti di codice e generare il codice usando funzionalità come **Generazione dall'utilizzo**. Se non si è mai usato l'editor di Visual Studio, vedere [Modifica del codice](https://www.visualstudio.com/features/ide-vs) per una rapida panoramica.  

 Il codice può essere visualizzato in diversi modi. Per accedere a una visualizzazione delle classi della soluzione, è possibile aprire la finestra **Visualizzazione classi** o espandere i nodi in **Esplora soluzioni** nei file di classe.

 È possibile cercare e sostituire il testo per file singoli o per più file. Per altre informazioni, vedere [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md). È possibile usare espressioni regolari per la ricerca e la sostituzione di testo. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 I diversi linguaggi di Visual Studio offrono set di funzionalità diversi e, in alcuni casi, le funzionalità si comportano in modo diverso a seconda del linguaggio. Molte di queste differenze sono specificate nelle descrizioni delle funzionalità, ma per altre informazioni è possibile vedere le sezioni su linguaggi specifici di Visual Studio.  

> [!IMPORTANT]
>  L'edizione di Visual Studio e le impostazioni in uso possono influire sulle funzionalità nell'IDE, che potrebbero essere diverse da quelle descritte in questo argomento.  

## <a name="editor-features"></a>Funzionalità dell'editor  

|||  
|-|-|  
|Colorazione della sintassi|Alcuni elementi della sintassi del codice e dei file di markup sono colorati in modo diverso per distinguerli. Ad esempio, le parole chiave (ad esempio `using` in C# e `Imports` in Visual Basic) sono di un colore, mentre i tipi (ad esempio `Console` e `Uri`) sono di un altro colore. Anche altri elementi della sintassi sono colorati, ad esempio i valori letterali stringa e i commenti. C++ usa i colori per distinguere i tipi, le enumerazioni e le macro dagli altri token.<br /><br /> È possibile visualizzare il colore predefinito per ogni tipo e modificare il colore per ogni specifico elemento della sintassi nella finestra di dialogo [Opzioni, Ambiente, Tipi di carattere](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), che può essere aperta dal menu **Strumenti**.|  
|Contrassegni di errore e di avviso|Quando si aggiunge codice e si compila la soluzione, vengono visualizzate (a) sottolineature ondulate con diversi colori (note come sottolineature a zigzag) o (b) lampadine nel codice. Le sottolineature rosse denotano errori di sintassi, quelle blu errori del compilatore, quelle verdi gli avvisi e quelle viola altri tipi di errore. Le [lampadine](../ide/perform-quick-actions-with-light-bulbs.md) suggeriscono correzioni dei problemi e ne semplificano l'applicazione.<br /><br /> I colori predefiniti per ogni sottolineatura di errore e di avviso possono essere visualizzati nella finestra di dialogo **Strumenti/Opzioni/Ambiente/Tipi di carattere e colori**. Cercare **Errore di sintassi**, **Errore del compilatore**, **Avviso**e **Altro errore**.|  
|Corrispondenza parentesi graffe|Quando il punto di inserimento viene inserito in una parentesi graffa di apertura in un file di codice, il punto e la parentesi graffa di chiusura vengono evidenziati. Questa funzionalità consente di ottenere un feedback immediato sulle parentesi graffe inserite non correttamente o mancanti. È possibile attivare o disattivare la corrispondenza tra parentesi graffe con l'impostazione **Evidenzia delimitatore automatico** (**Strumenti/Opzioni/Editor di testo**). È possibile modificare il colore di evidenziazione nell'impostazione **Tipi di carattere e colori** (**Strumenti/Opzioni/Ambiente**). Cercare **Corrispondenza parentesi (evidenziate)** o **Corrispondenza parentesi (rettangolo)**.|  
|Visualizzatore di struttura|Per facilitare l'individuazione delle coppie di parentesi graffe di apertura e chiusura corrispondenti nel file di codice, vengono visualizzate linee tratteggiate che connettono le parentesi corrispondenti. In questo modo è possibile individuare più rapidamente il codice nella codebase. È possibile attivare o disattivare queste linee nell'opzione **Mostra guide per strutture** nella sezione **Visualizza** della pagina **Strumenti/Opzioni/Editor di testo/Generale**.|
|Numeri di riga|I numeri di riga possono essere visualizzati nel margine sinistro della finestra del codice. Non vengono visualizzati per impostazione predefinita. È possibile attivare questa opzione nelle impostazioni **Tutti i linguaggi dell'Editor di testo** (**Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**). È possibile visualizzare i numeri di riga per i singoli linguaggi di programmazione cambiando le impostazioni per i linguaggi (**Strumenti/Opzioni/Editor di testo/\<linguaggio>**). Per stampare i numeri di riga, è necessario selezionare Includi numeri di riga nella finestra di dialogo **Stampa**.|  
|Rilevamento modifiche|Il colore del margine sinistro consente di tenere traccia delle modifiche apportate al file. Le modifiche apportate dall'apertura del file ma non ancora salvate vengono contrassegnate con una barra gialla nel margine sinistro (noto come margine di selezione). Dopo aver salvato le modifiche, ma prima di chiudere il file, la barra diventa verde. Se si annulla una modifica dopo aver salvato il file, la barra diventa arancione. Per attivare e disattivare questa funzionalità, modificare l'opzione **Revisioni** nelle impostazioni **Editor di testo** (**Strumenti/Opzioni/Editor di testo**).|  
|Selezione di codice e testo|È possibile selezionare il testo con la modalità standard a flusso continuo oppure con la modalità riquadro, in cui non viene selezionato un set di righe, ma una porzione rettangolare di testo. Per effettuare una selezione in modalità riquadro, premere ALT mentre si trascina il mouse sulla selezione oppure premere ALT+MAIUSC+\<tasto di direzione>. La selezione include tutti i caratteri nel rettangolo definiti dal primo e dall'ultimo carattere nella selezione. Tutto ciò che viene digitato o incollato nell'area selezionata viene inserito nello stesso punto di ogni riga.|  
|Zoom|È possibile ingrandire o ridurre qualsiasi finestra del codice tenendo premuto CTRL e spostando la rotellina del mouse (oppure CTRL+MAIUSC+. per ingrandire e CTRL+MAIUSC+, per ridurre). Per impostare una specifica percentuale di zoom, è anche possibile usare la casella Zoom nell'angolo in basso a sinistra della finestra del codice. La funzionalità di zoom non funziona nelle finestre degli strumenti.|  
|Spazio virtuale|Per impostazione predefinita, le righe nell'editor di Visual Studio terminano dopo l'ultimo carattere, quindi il tasto freccia DESTRA alla fine della riga sposta il cursore all'inizio della riga successiva. In altri editor, una riga non termina dopo l'ultimo carattere ed è possibile posizionare il cursore in qualsiasi punto della riga. È possibile abilitare lo spazio virtuale nell'editor nelle impostazioni **Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**. È possibile abilitare **Spazio virtuale** o **A capo automatico**, ma non entrambi.|  
|Stampa|È possibile usare le opzioni nella finestra di dialogo **Stampa** per includere i numeri di riga o nascondere le aree di codice compresse quando si stampa un file. Nella finestra di dialogo **Imposta pagina** è possibile scegliere di stampare il percorso completo e il nome del file scegliendo **Intestazione pagina**.<br /><br /> È possibile impostare le opzioni di stampa a colori nella finestra di dialogo **Strumenti/Opzioni/Ambiente/Tipi di carattere e colori**. Scegliere **Stampante** nell'elenco **Mostra impostazioni per** per personalizzare la stampa a colori. Per la stampa di un file è possibile specificare colori diversi rispetto alla modifica di un file.|  
|Fasi di rollforward e rollback globali|I comandi **Annulla ultima azione globale** e **Ripeti ultima azione globale** nel menu **Modifica** annullano o ripetono le azioni globali che interessano più file. Le azioni globali includono la ridenominazione di una classe o di uno spazio dei nomi, l'esecuzione di un'operazione di ricerca e sostituzione in una soluzione, il refactoring di un database o altre azioni che modificano più file. È possibile applicare questi comandi globali alle azioni nella sessione corrente di Visual Studio anche dopo aver chiuso la soluzione alla quale è stata applicata un'azione.|  

## <a name="advanced-editing-features"></a>Funzionalità di modifica avanzate  
 Diverse funzionalità avanzate sono disponibili nel sottomenu **Modifica/Avanzate**. Non tutte le funzionalità sono disponibili per tutti i tipi di file di codice.  

|||  
|-|-|  
|Formatta documento|Imposta il rientro corretto per le righe di codice e sposta le parentesi graffe in righe separate nel documento.|  
|Formatta selezione|Imposta il rientro corretto per le righe di codice e sposta le parentesi graffe in righe separate nella selezione.|  
|Inserisci tabulazione in righe selezionate|Cambia gli spazi iniziali in tabulazioni dove appropriato.|  
|Rimuovi tabulazione da righe selezionate|Cambia le tabulazioni iniziali in spazi. Per convertire tutti gli spazi nel file in tabulazioni (o tutte le tabulazioni in spazi), è possibile usare i comandi `Edit.ConvertSpacesToTabs` e `Edit.ConvertTabsToSpaces`. Questi comandi non vengono visualizzati nei menu di Visual Studio, ma possono essere richiamati dalla finestra di accesso rapido o dalla finestra di comando.|  
|Maiuscole|Converte in maiuscolo tutti i caratteri nella selezione oppure, se non sono state effettuate selezioni, converte in maiuscolo il carattere nel punto di inserimento.|  
|Minuscole|Converte in minuscolo tutti i caratteri nella selezione oppure, se non sono state effettuate selezioni, converte in minuscolo il carattere nel punto di inserimento.|  
|Sposta in alto righe selezionate|Sposta la riga selezionata di una riga verso l'alto. Scelta rapida: ALT+freccia SU.|
|Sposta in basso righe selezionate|Sposta la riga selezionata di una riga verso il basso. Scelta rapida: ALT+freccia GIÙ.|
|Convalida documento|Convalida i file di codice JScript.|  
|Elimina spazio vuoto superfluo|Elimina le tabulazioni o gli spazi alla fine della riga corrente.|  
|Mostra/Nascondi spazi|Visualizza gli spazi sotto forma di punti mediani e le tabulazioni sotto forma di frecce. La fine di un file viene visualizzata come un glifo rettangolare. Se è selezionato **Strumenti/Opzioni/Editor di testo/Tutti i linguaggi/A capo automatico/Mostra icone per ritorno a capo automatico**, viene visualizzato anche il glifo.|  
|A capo automatico|Rende visibili tutte le righe di un documento nella finestra del codice. È possibile attivare e disattivare il ritorno a capo nelle impostazioni Tutti i linguaggi dell'editor di testo (**Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**).|  
|Rimuovi commento selezione|Aggiunge caratteri di commento alla selezione o alla riga corrente.|  
|Commenta selezione|Rimuove tutti i caratteri di commento dalla selezione o dalla riga corrente.|  
|Aumenta rientro riga|Aggiunge una tabulazione (o gli spazi equivalenti) alle righe selezionate o alla riga corrente.|  
|Riduci rientro riga|Rimuove una tabulazione (o gli spazi equivalenti) dalle righe selezionate o dalla riga corrente.|  
|Seleziona tag|In un documento che contiene tag, ad esempio XML o HTML, seleziona il tag.|  
|Seleziona contenuto tag|In un documento che contiene tag, ad esempio XML o HTML, seleziona il contenuto.|  

## <a name="navigate-and-find-code"></a>Eseguire ricerche e spostarsi nel codice  
È possibile spostarsi in un documento in diversi modi. Oltre alle operazioni standard, è possibile usare i pulsanti **Posizione precedente** (CTRL+MENO) e **Posizione successiva** (CTRL+MAIUSC+MENO) nella barra degli strumenti per spostare il punto di inserimento nelle posizioni precedenti o tornare alle posizioni più recenti nel documento attivo. Questi pulsanti conservano le ultime 20 posizioni del punto di inserimento.

![Pulsanti di spostamento per spostarsi avanti e indietro](~/docs/ide/media/vs2017_nav_buttons.png)

Nella funzionalità Visualizzatore di struttura dell'editor del codice sono visualizzate le *guide per strutture*, ovvero linee verticali tratteggiate che indicano la presenza di parentesi graffe corrispondenti nella codebase. In questo modo risulta più agevole visualizzare l'inizio e la fine dei blocchi logici.

![Visualizzatore di struttura](~/docs/ide/media/vside_structure_visualizer.png)

Per disabilitare le guide per strutture, passare a **Strumenti**, **Opzioni**, **Editor di testo**, **Generale** e deselezionare la casella **Mostra guide per strutture**.

Per una panoramica del codice, è anche possibile usare la barra di scorrimento avanzata in una finestra del codice. In modalità di mapping è possibile visualizzare l'anteprima del codice quando si sposta il cursore verso l'alto e verso il basso nella barra di scorrimento. Per altre informazioni, vedere [Procedura: Tenere traccia del codice personalizzando la barra di scorrimento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

I comandi seguenti sono metodi di spostamento specifici per il codice:  

|||  
|-|-|  
|Trova tutti i riferimenti|(Menu di scelta rapida o MAIUSC+F12): trova tutti i riferimenti all'elemento selezionato nella soluzione.|  
|Vai a|Include i comandi seguenti: **Vai alla riga** (CTRL+G): consente di passare al numero di riga specificato nel documento attivo. **Vai a tutti** (CTRL+T): consente di passare alla riga, al tipo, al file, al membro o al tipo specificato. **Vai al file** (CTRL+1, CTRL+F): consente di passare al file specificato nella soluzione. **Vai al tipo** (CTRL+1, CTRL+T): consente di passare al tipo specificato nella soluzione. **Vai al membro** (CTRL+1, CTRL+M): consente di passare al membro specificato nella soluzione. **Vai al simbolo** (CTRL+1, CTRL+S): consente di passare al simbolo specificato nella soluzione. Per altre informazioni su questi comandi, vedere la sezione "Trovare codice con i comandi Vai a" più avanti in questo argomento.|  
|Vai a definizione|(Menu di scelta rapida o F12): trova la definizione dell'elemento selezionato.|  
|Vai all'implementazione|(Menu di scelta rapida o CTRL+F12): trova la posizione nel codice in cui è implementato l'elemento selezionato.|
|Visualizza definizione|(Menu di scelta rapida o ALT+F12): trova la definizione dell'elemento selezionato e la visualizza in una finestra nell'editor del codice. Per altre informazioni, vedere [How to: View and Edit Code by Using Peek Definition (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) (Procedura: Visualizzare e modificare il codice usando la finestra Visualizza definizione (Alt+F12).|  
|Metodo successivo, Metodo precedente|(**Modifica/Metodo successivo, Metodo precedente**) Nei file di codice di Visual Basic, usare questi comandi per spostare il punto di inserimento in metodi diversi.|  
|Evidenziazione di riferimenti|Quando si fa clic su un simbolo nel codice sorgente, tutte le istanze del simbolo vengono evidenziate nel documento. I simboli evidenziati possono includere dichiarazioni e riferimenti e molti altri simboli restituiti da **Trova tutti i riferimenti**. Sono inclusi i nomi di classi, oggetti, variabili, metodi e proprietà. Nel codice Visual Basic vengono evidenziate anche le parole chiave per molte strutture di controlli. Per spostarsi al simbolo evidenziato successivo o precedente, premere CTRL+MAIUSC+ freccia GIÙ o CTRL+MAIUSC+freccia SU. È possibile modificare il colore di evidenziazione in **Strumenti/Opzioni/Ambiente/Tipi di carattere e colori/Riferimento evidenziato.**|  
|Trova informazioni relative al codice|È possibile trovare informazioni relative a codice specifico, ad esempio modifiche, autori delle modifiche, riferimenti, bug, elementi di lavoro, revisioni del codice e stato dello unit test quando si usa CodeLens nell'editor del codice. CodeLens funziona come una visualizzazione preliminare quando si usa Visual Studio Enterprise con Team Foundation Server. Vedere [Trovare le modifiche apportate al codice e altri elementi della cronologia](../ide/find-code-changes-and-other-history-with-codelens.md).|
|Visualizza gerarchia delle chiamate|(Menu di scelta rapida o CTRL+K, CTRL+T).|  

 Per trovare codice in una codebase, è anche possibile usare la **barra di spostamento** (caselle a discesa nella parte superiore della finestra del codice) e scegliere un tipo o un membro per accedervi direttamente. La barra di spostamento viene visualizzata quando si modifica il codice in una codebase Visual Basic, C# o C++.

 ![Barra di spostamento per il codice](~/docs/ide/media/vside_navigation_bar.png)

 Per nascondere la barra di spostamento, modificare l'opzione **Barra di navigazione** nelle impostazioni Tutti i linguaggi dell'editor di testo (**Strumenti**, **Opzioni**, **Editor di testo**, **Tutti i linguaggi** oppure modificare le impostazioni per i singoli linguaggi). È possibile spostarsi tra le caselle a discesa come segue:  

-   Per spostare lo stato attivo dalla finestra del codice alla barra di spostamento, premere la combinazione di tasti di scelta rapida CTRL+F2.  

-   Per ripristinare lo stato attivo dalla barra di spostamento alla finestra del codice, premere ESC.  

-   Per spostare lo stato attivo da un elemento a un elemento nella barra di spostamento, premere TAB.  

-   Per selezionare l'elemento della barra di spostamento con stato attivo e tornare all'IDE, premere INVIO.  

-   Per spostarsi in una classe o in un tipo, fare clic sul relativo nome nell'elenco a discesa a sinistra.  

-   Per passare direttamente a una routine in una classe, fare clic su una routine nell'elenco a discesa a destra.  

 In una classe parziale i membri definiti all'esterno del file di codice corrente potrebbero essere disabilitati (visualizzati in grigio).  

## <a name="find-code-using-go-to-commands"></a>Trovare codice con i comandi Vai a
Il comando **Vai a** di Visual Studio consente di eseguire una ricerca mirata del codice allo scopo di individuare rapidamente gli elementi specificati in file di codice, percorsi di file e simboli del codice. A differenza di altri strumenti di ricerca nel testo, ad esempio Trova o Cerca nei file, con il comando Vai la ricerca è limitata alle aree in cui si trova il codice effettivo, ad esempio file, moduli e moduli di codice. Se ad esempio si cerca una stringa in un'applicazione Web ASP.NET usando Trova o Cerca nei file nell'intera soluzione, i risultati ottenuti potrebbero includere istanze della stringa nei commenti del codice. Con il comando Vai a, però, la ricerca consente di individuare la funzione cercata, ignorando le istanze della stringa nei commenti del codice.

### <a name="find-code-using-go-to"></a>Trovare codice con Vai a

1. Aprire una soluzione o una cartella in Visual Studio.
1. Nel menu principale scegliere **Modifica**, **Vai a**. Viene visualizzata una piccola casella di testo nell'angolo superiore dell'editor del codice.
1. Immettere il nome dell'elemento di codice da cercare nella casella di testo.

    ![Finestra Passa a](~/docs/ide/media/vside_navigatetowindow.png "Finestra Passa a")

    Durante la digitazione i risultati vengono visualizzati in un elenco a discesa sotto la casella di testo.
1. Per passare a un elemento, selezionarlo nell'elenco.


### <a name="filter-your-search"></a>Filtrare la ricerca

Per impostazione predefinita, l'elemento specificato viene cercato in tutti gli elementi della soluzione. È però possibile limitare la ricerca nel codice a tipi di elementi specifici anteponendo determinati caratteri di prefisso ai termini di ricerca. Per eseguire facilmente questa operazione, premere CTRL+T per aprire la finestra di dialogo Vai a e quindi modificare il carattere di prefisso in uno di quelli elencati di seguito. In alternativa, è possibile usare i tasti di scelta rapida seguenti per aggiungere automaticamente il carattere di prefisso.

|Simbolo|Descrizione|  
|-|-|
|Nessuno|Nessun carattere di prefisso. Consente di trovare il termine specificato in tutte le righe, i file, i tipi, i membri e i simboli. Scelta rapida: CTRL+T|
|:|Consente di passare al numero di riga specificato. Scelta rapida: CTRL+G|
|f|Consente di passare al nome file specificato. Scelta rapida: CTRL+1, CTRL+F|
|u|Consente di passare al tipo specificato. Scelta rapida: CTRL+1, CTRL+T|
|m|Consente di passare al membro specificato. Scelta rapida: CTRL+1, CTRL+M|
|#|Consente di passare al simbolo specificato. Scelta rapida: CTRL+1, CTRL+S|

Ad esempio, per limitare la ricerca ai soli simboli di codice, premere CTRL+T (o CTRL+,) per aprire la finestra di dialogo Vai a e quindi anteporre alla query di Vai a il carattere "#" oppure scegliere **Modifica**, **Vai a**, **Vai al simbolo** nel menu. Se, ad esempio, si cerca `# application`, vengono visualizzati solo i simboli di codice che contengono la parola "application".

È anche possibile modificare rapidamente il filtro di ricerca scegliendo i pulsanti sulla barra degli strumenti della finestra di dialogo Vai a. I pulsanti per la modifica dei filtri si trovano sul lato sinistro, mentre quelli per la modifica dell'ambito della ricerca sono sul lato destro.

![](~/docs/ide/media/vside_navigation_toolbar.png)

Se si usa la [notazione camel](https://en.wikipedia.org/wiki/Camel_case) per maiuscole e minuscole nel codice, è possibile trovare gli elementi di codice più rapidamente immettendo solo le lettere maiuscole dei nomi degli elementi di codice. Ad esempio, se nel codice è presente un tipo denominato `CredentialViewModel`, è possibile restringere la ricerca scegliendo il filtro Tipo ("t") e quindi immettendo solo le lettere maiuscole del nome (`CVM`) nella finestra di dialogo Vai a.

![Finestra Passa a - ricerca con lettere maiuscole](~/docs/ide/media/vside_capitalsearch.png)

Questa funzionalità può essere utile se il codice contiene nomi lunghi.

## <a name="finding-references-in-your-codebase"></a>Ricerca di riferimenti nella codebase
Per trovare i riferimenti a particolari elementi del codice presenti nella codebase, è possibile usare il comando **Trova tutti i riferimenti**. Per usare **Trova tutti i riferimenti**, scegliere tale comando nel menu di scelta rapida dell'elemento per il quale si vogliono trovare i riferimenti oppure premere MAIUSC+F12.

I risultati vengono visualizzati in una finestra degli strumenti denominata **'*{elemento}*' references**, in cui *{elemento}* è il nome dell'elemento cercato. Una barra degli strumenti in questa finestra Riferimenti consente di:
- Modificare l'ambito della ricerca in una casella di riepilogo a discesa. È possibile scegliere di eseguire la ricerca solo nei documenti modificati o nell'intera soluzione.
- Copiare l'elemento di riferimento selezionato scegliendo il pulsante **Copia**.
- Scegliere i pulsanti per passare alla posizione precedente o successiva nell'elenco oppure premere F8 e MAIUSC+F8 per eseguire questa operazione.
- Rimuovere tutti i filtri applicati ai risultati restituiti scegliendo il pulsante **Cancella tutti i filtri**.
- Modificare il raggruppamento degli elementi restituiti scegliendo un'impostazione nella casella di riepilogo a discesa **Raggruppa per**.
- Mantenere la finestra dei risultati della ricerca corrente scegliendo il pulsante **Mantieni risultati**.
- Cercare stringhe nei risultati della ricerca immettendo testo nella casella di testo **Cerca in Trova tutti i riferimenti**.

È anche possibile passare con il puntatore del mouse su un risultato della ricerca qualsiasi per visualizzare un'anteprima dell'elemento restituito.

![Finestra degli strumenti Trova tutti i riferimenti](~/docs/ide/media/vside_findallreferences.png)

Per mantenere i risultati della ricerca, scegliere il pulsante **Mantieni risultati**. Quando si sceglie questo pulsante, i risultati della ricerca corrente rimangono in questa finestra e i nuovi risultati vengono visualizzati in una nuova finestra degli strumenti.

### <a name="navigate-to-references"></a>Passare ai riferimenti
Nella finestra di dialogo Trova tutti i riferimenti è possibile usare i metodi seguenti per passare ai riferimenti.

- Premere F8 per passare al riferimento successivo oppure MAIUSC+F8 per passare al riferimento precedente.
- Premere INVIO su un riferimento o farvi sopra doppio clic per visualizzarlo nel codice.
- Nel menu di scelta rapida di un riferimento scegliere i comandi **Vai alla posizione precedente** / **Vai alla posizione successiva**.
- Premere i tasti freccia SU e freccia GIÙ, se sono abilitati nella finestra di dialogo Opzioni. Per abilitare questa funzionalità, nel menu scegliere **Strumenti**, **Opzioni**, **Ambiente**, **Schede e finestre**, **Scheda anteprima** e quindi selezionare le caselle **Consenti apertura nuovi file nella scheda anteprima** e **Anteprima file selezionati in Risultati ricerca**.

### <a name="change-reference-groupings"></a>Modificare i raggruppamenti di riferimenti
Per impostazione predefinita, i riferimenti sono raggruppati prima in base al progetto e quindi in base alla definizione. È però possibile modificare questo ordine di raggruppamento modificando l'impostazione nella casella di riepilogo a discesa**Raggruppa per** sulla barra degli strumenti. Ad esempio, è possibile modificare l'impostazione predefinita **Definizione, quindi progetto** in **Progetto, quindi definizione**, oltre ad altre impostazioni.

I due raggruppamenti predefiniti usati sono **Definizione** e **Progetto**, ma è possibile aggiungerne altri scegliendo il comando **Raggruppamento** nel menu di scelta rapida dell'elemento selezionato. L'aggiunta di più raggruppamenti può essere utile se la soluzione contiene molti file e percorsi.

## <a name="customize-the-editor"></a>Personalizzare l'editor  
È possibile condividere le impostazioni di Visual Studio con un altro sviluppatore, renderle conformi a uno standard o ripristinare le impostazioni predefinite con il comando **Importazione/Esportazione guidata delle impostazioni** nel menu **Strumenti**. Nell'**Importazione/Esportazione guidata delle impostazioni** è possibile modificare impostazioni generali selezionate oppure impostazioni specifiche di un linguaggio e di un progetto.

Per definire i nuovi tasti di scelta o ridefinire quelli esistenti, passare a **Strumenti**, **Opzioni**, **Ambiente**, **Tastiera**. Per altre informazioni sui tasti di scelta rapida, vedere [Tasti di scelta rapida predefiniti](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

Per altre informazioni sulla personalizzazione dell'editor, vedere [Personalizzazione dell'editor](../ide/customizing-the-editor.md). Per informazioni sulle opzioni dell'editor specifiche di un linguaggio, vedere [Using the Visual Studio Development Environment for C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) (Uso dell'ambiente di sviluppo di Visual Studio per C#) e [Opzioni, Editor di testo, JavaScript, Formattazione](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Vedere anche  
 [IDE di Visual Studio](../ide/visual-studio-ide.md)

