---
title: "Menu e comandi di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Menu e comandi di Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Utilizzo dei comandi  
  
### Panoramica  
 A differenza di Microsoft Office, ovvero un gruppo che include molti prodotti distinti, Visual Studio include molti prodotti che ogni contribuiscono i set di comandi all'IDE di Visual Studio globale. L'IDE consente di gestire la complessità di migliaia di comandi filtrando le funzionalità disponibili per l'utente in base al contesto.  
  
 Quando viene modificato un contesto utente: ad esempio il passaggio da una finestra di progettazione a una finestra di modifica del codice, funzionalità non correlate a viene rimosso il nuovo contesto. Allo stesso tempo, nuove superfici di funzionalità insieme a informazioni dinamiche correlate, ad esempio le opzioni della casella degli strumenti e proprietà. L'utente non noteranno lo scambio del set di comandi disponibili. Se l'utente è distratti o confusi dai comandi visualizzati o scomparire, la progettazione dell'interfaccia utente deve quindi regolazione. Il contesto dell'utente corrente è sempre indicato in uno o più modi, ad esempio nella barra del titolo IDE, la finestra proprietà o la finestra di dialogo Pagine delle proprietà.  
  
 Barre dei comandi consentono flessibilità nell'interfaccia utente. L'unico comando strutture inerenti a Visual Studio ambiente sono menu principale e la barra dei comandi principale, che può essere personalizzata e anche nascosta. Altre barre dei comandi apparire e scompaiano in base allo stato dell'applicazione. Editor di documento e finestre degli strumenti può anche contenere barre degli strumenti incorporati all'interno i bordi della finestra.  
  
#### Linee guida di base  
  
##### Utilizzare comandi condivisi esistenti, gruppi di comandi e menu laddove possibile.  
 Poiché i comandi vengono in genere riportati in base al contesto, l'utilizzo di menu condivisi esistenti e i gruppi di comando assicura che la struttura di comando rimane relativamente stabile tra le modifiche nel contesto. Riutilizzo di comandi condivisi e l'inserimento di nuovi comandi vicino comandi correlati condivisi anche riduce la complessità IDE e crea un'esperienza più semplice. Se è necessario definire un nuovo comando, provare a posizionarlo in un gruppo di comando condiviso esistente. Se è necessario definire un nuovo gruppo, è necessario inserirlo in un menu condiviso esistente vicino a un gruppo di comandi correlati prima di creare un nuovo menu di primo livello.  
  
##### Non creare le icone per ogni comando.  
 Prestare attenzione prima di creare un'icona del comando. Le icone devono essere create solo per i comandi che:  
  
-   vengono visualizzati in una barra degli strumenti predefinita.  
  
-   possono essere aggiunti dagli utenti per una barra degli strumenti tramite il **Personalizza …** finestra di dialogo.  
  
-   è associata un'icona con la stessa azione in un altro prodotto Microsoft.  
  
##### Limitare l'aggiunta di tasti di scelta rapida  
 La maggior parte degli utenti utilizzano una piccola frazione di tutti i collegamenti disponibili. In caso di dubbi, non si associano le funzionalità di un tasto di scelta rapida. Lavorare con l'utente esperienza team prima di aggiungere nuovi collegamenti.  
  
##### Impartire comandi una posizione di menu predefinita.  
 Tenere presente che i comandi saranno personalizzati da altri utenti e progettare di conseguenza. Non esiste alcun equivalente di un comando nascosto. Vengono visualizzati tutti i comandi di Visual Studio nel **Strumenti \> Personalizza** finestra di dialogo, finestra di comando, il completamento automatico, il **Strumenti \> Opzioni \> tastiera** finestra di dialogo e l'ambiente DTE \(Development Tools\). Assicurarsi di assegnare i comandi di un nome e una descrizione comando nel file .ctc in modo che gli utenti possano individuarli facilmente.  
  
##### Non duplicano comandi condivisi in una barra degli strumenti incorporata.  
 È utile posizionare i comandi in stretta vicinanza all'area di interesse dell'utente. Un modo per eseguire questa operazione consiste nel creare una barra degli strumenti incorporato nella parte superiore del documento o finestra degli strumenti editor. I comandi posizionati sulla barra degli strumenti devono essere specifici per l'area di contenuto all'interno della finestra. Non duplicano comandi condivisi su queste barre degli strumenti. Ad esempio, non posizionare un'icona "Salva" all'interno di una barra degli strumenti incorporata.  
  
### Visibilità del contenuto e dei comandi  
 Comandi sono presenti negli ambiti seguenti: **ambiente**, **gerarchia**, e **documento**. Conoscere ogni ambito per avere la certezza che nel posizionamento del comando.  
  
 I comandi di **ambiente** ambito stabilire il contesto primario e vengono condivise tra più contesti. Queste alterano la visibilità o la disposizione dei documenti e finestre degli strumenti. Tra i comandi nell'ambiente di ambito sono **Nuovo progetto**, **Connetti al Server**, **il processo di collegamento**, **Taglia**, **Copia**, **Incolla**, **trovare**, **Opzioni**, **Personalizza**, **nuova finestra**, e **Visualizza Guida**.  
  
 I comandi di **gerarchia** ambito gestire gerarchie tra cui Visual Studio **progetto**, **Team**, e **dati**. Ad esempio, si riferiscono al sottocontesto del progetto: **Debug**, **compilare**, **Test**, **architettura**, o **Analizza**. Tra i comandi nella gerarchia di ambito sono **Aggiungi nuovo elemento**, **Nuova Query**, **le impostazioni di progetto**, **Aggiungi nuova origine dati**, **avviare Creazione guidata sessione di prestazioni**, e **nuovo diagramma**.  
  
 I comandi di **documento** act ambito sul contenuto di un documento, ad esempio di codice, struttura o una query elemento di lavoro \(WIQ\). Sono inoltre agire sulla visualizzazione di una finestra degli strumenti o in caso contrario sono specifici di tale finestra degli strumenti. I comandi di ambito documento può essere utilizzato anche per gli oggetti file che sono specifiche di gerarchia, ad esempio **rimuovere dal progetto**. Tra i comandi nel documento di ambito sono **il refactoring \> rinominare**, **Crea copia di elemento di lavoro**, **Espandi tutto**, **Comprimi tutto**, e **Crea attività definita dall'utente**.  
  
### Decisioni di posizionamento di comando  
 Una volta che si è deciso di creare un comando, è necessario determinare la posizione appropriata e se si desidera creare un tasto di scelta rapida. Seguire questo percorso decisionale per stabilire dove posizionare il comando:  
  
 ![Command placement decision chart](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501\-a\_CommandPlacement")  
  
 **Percorso di decisione per la selezione di comando in Visual Studio**  
  
### Posizionamento di comando di menu  
  
#### Barra dei menu principale  
 Barra dei menu principale deve essere il percorso standard per i comandi di tutti i pacchetti menu contestuali che contribuiscono all'interfaccia utente. Barra dei menu principale si differenzia da altre strutture di comando nell'ambiente viene utilizzato per controllare quali comandi sono visibili. Tutte le altre barre dei comandi disattivare semplicemente i comandi che sono fuori contesto, se vengono inseriti in un menu o in una barra degli strumenti.  
  
 L'ambiente definisce un set di comandi creati nella barra dei menu principale che sono comuni a più domini di attività e l'intero IDE. Questi comandi sono sempre visibili indipendentemente dal fatto che di cui VSPackage vengono caricati nell'ambiente. Sebbene i package VS possibile estendere questo set di comandi, il set di comandi in ogni prodotto e la posizione dei relativi comandi sono la responsabilità di ogni team.  
  
 La struttura di menu principale di Visual Studio può essere suddiviso nelle seguenti categorie di menu:  
  
##### Menu principali  
  
-   File  
  
-   Modifica  
  
-   Visualizza  
  
-   Strumenti  
  
-   Finestra  
  
-   ?  
  
##### Menu specifici del progetto  
  
-   Progetto  
  
-   Compilazione  
  
-   Debug  
  
##### Menu specifici del contesto  
  
-   Team  
  
-   Dati  
  
-   Test  
  
-   Architettura  
  
-   Analyze  
  
##### Menu specifici del documento  
  
-   Formato  
  
-   Tabella  
  
##### Quando si progettano i menu principali, è necessario attenersi a queste regole:  
  
-   Non superino 25 elementi di livello superiori in un determinato contesto  
  
-   I menu non devono mai superare 600 pixel di altezza.  
  
-   Valutare un menu principale in più contesti, ad esempio la SKU Ultimate e il profilo generale.  
  
-   Menu a comparsa sono accettabili.  
  
-   Menu a comparsa devono contenere almeno tre elementi e non più di sette.  
  
-   Menu a comparsa devono passare solo un livello di profondità: alcune voci di menu di Visual Studio dispongano sottomenu CSS, ma questo modello non è consigliabile.  
  
-   Utilizzare i separatori non più di sei. Raggruppamenti devono rispettare la figura seguente:  
  
     ![Guidelines for main menu grouping](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501\-b\_MainMenus")  
  
-   Mentre non è necessario che ogni raggruppamento nella figura, l'aggiunta di ulteriori raggruppamenti è limitato.  
  
-   Ogni raggruppamento deve avere da due a sette voci di menu.  
  
#### Menu principale di ordinamento  
 Prima di aggiungere un nuovo elemento di primo livello, è consigliabile inserire il comando in un menu di primo livello esistente. Quando si aggiunge un nuovo menu di primo livello, assicurarsi di inserirlo nella posizione corretta. Decidere se il menu è specifico di progetto, di contesto o documento. Mantenere il nome del menu di primo livello conciso e utilizzare solo una parola.  
  
 I menu principali devono delimitatore il resto dei comandi. File, modifica e visualizzazione deve essere sempre a sinistra, quindi Strumenti, finestra e Guida in linea deve essere sempre a destra.  
  
#### Menu di scelta rapida  
 Inserimento di una quantità eccessiva funzionalità all'interno di menu di scelta rapida risultati in un'interfaccia difficili da apprendere. Tutte le funzionalità principali devono essere disponibili tramite la barra dei menu principale. Posizione dei comandi deve essere riconciliato con comandi esistenti per evitare i comandi duplicati. Per i menu di scelta rapida, la shell definisce i gruppi di menu standard che devono essere inclusi, a seconda che il menu di scelta rapida sia per la soluzione, un nodo di progetto o un elemento di progetto.  
  
 Durante la progettazione di menu di scelta rapida, rispettare le stesse regole per il menu principale e inoltre:  
  
-   Non superare 25 voci di menu di primo livello.  
  
-   Menu a comparsa sono accettabili, ma deve superare un livello di profondità – mai utilizzare riquadri a comparsa CSS.  
  
-   Utilizzare i separatori non più di sei.  
  
### Posizionamento del comando nelle barre degli strumenti  
  
#### Barre degli strumenti generali  
 Durante la progettazione e la disposizione delle barre degli strumenti, seguire questi standard:  
  
-   Non utilizzare più di un verbo al pulsante. Un pulsante \= un'azione.  
  
-   Utilizzare testo con l'icona solo se è necessario rafforzare con l'etichetta.  
  
-   Utilizzare una casella combinata esclusivamente per le proprietà che verranno passate più volte in una sessione. In caso contrario, espongono la proprietà in un' posizione.  
  
-   La larghezza di una casella combinata deve essere uguale la larghezza dell'elemento più lungo di finestra \+ 30%. Ad esempio, se l'elemento più lungo è 200 pixel, della casella combinata deve essere 260 pixel.  
  
-   Limitare l'utilizzo di separatori. L'utilizzo di un separatore accanto a un elenco a discesa è un anti\-pattern, poiché la forma di elenco a discesa stesso agisce come un separatore visivo.  
  
-   Gruppi di icona devono contenere da tre a sei icone.  
  
-   Se i qualificatori di più comandi utili, utilizzare un controllo split button che archivia l'ultima impostazione:  
  
     ![Split buttons in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501\-c\_SplitButtons")  
  
     **Esempio di un pulsante di divisione. I sei comandi a sinistra possono invece essere contenuta in un singolo pulsante.**  
  
#### Barre degli strumenti specifici del prodotto  
 Ogni prodotto può fornire una barra degli strumenti predefinita che contiene utilizzati di frequente e comandi importanti e barra degli strumenti predefinita di ogni prodotto vengono visualizzati la prima volta Visual Studio viene avviato dopo l'installazione del prodotto.  
  
 Prodotti devono utilizzare anche gruppi di comandi condiviso e i menu forniti dall'IDE. Ogni gruppo di comandi condiviso viene inserito in un menu condiviso lo scopo di organizzare i comandi correlati in modo significativo per l'utente. È importante sfruttare questa struttura comando condiviso per ridurre la complessità.  
  
#### Barre degli strumenti globale  
 Barre degli strumenti globale sono necessari in base a destra di una riga predefinita. Quando si crea una nuova barra degli strumenti globale, seguire le linee guida per il tipo di barra degli strumenti.  
  
 **Linee guida generali sulla barra degli strumenti:**  
  
-   Ogni barra degli strumenti è 24 pixel nei controlli comuni \(gripper, overflow\).  
  
-   Ogni pulsante della barra degli strumenti è 22 pixel incluse la spaziatura. Effettua l'icona di un controllo split button aggiunge un altro 11 pixel di larghezza.  
  
-   È consentita la duplicazione dei comandi in barre degli strumenti.  
  
 **Barre degli strumenti specifici di documenti** quando un determinato tipo di file è attivo e quando un tipo di file diversi diventa attivo.  
  
-   Barre degli strumenti specifici di documenti potrebbe non disporre più di 12 pulsanti.  
  
-   La larghezza totale della barra degli strumenti non può superare i 300 pixel.  
  
-   Ogni tipo di file può avere uno degli strumenti incorporata o una barra degli strumenti globale specifiche per i documenti, ma non entrambi.  
  
 **Barre degli strumenti specifici del contesto** vengono visualizzati quando un determinato contesto viene impostato e tendono a rimanere attive per lunghi periodi di tempo.  
  
-   Il limite di pulsante per tutte le barre degli strumenti specifici del contesto è 18.  
  
-   Se la maggior parte degli utenti in modo coerente non utilizzano i comandi della barra degli strumenti quando è attivo il contesto, con un contesto non associare quindi questa barra degli strumenti.  
  
-   Assicurarsi che la barra degli strumenti scomparirà all'uscita dal contesto. Nessuna di queste barre degli strumenti visualizzata all'avvio.  
  
 **Barre degli strumenti senza alcun contesto** mai visualizzata automaticamente. Vengono visualizzati solo quando l'utente li attiva. Mantenere la larghezza massima di sotto di 200 pixel.  
  
### Organizzazione generale e i gruppi definiti shell  
 Utilizzare i comandi condivisi esistenti, gruppi di comandi e menu. Se è necessario definire un nuovo comando, provare a posizionarlo in un gruppo di comando condiviso esistente. Se è necessario definire un nuovo gruppo, provare a posizionarlo in un menu condiviso esistente vicino a un gruppo di comandi correlati prima di creare un nuovo menu di primo livello. Questo riduce la complessità comando assicurando posizionamento del comando coerenti nell'IDE.  
  
 Condivisa **formato** menu, in genere mostrato nel contesto delle finestre di documento in stile di finestra di progettazione, come illustrato nell'immagine seguente:  
  
 ![Visual Studio Format menu with callouts](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501\-d\_FormatMenu")  
  
 **Gruppi di menu in Visual Studio**  
  
### La riduzione e il riutilizzo dei comandi  
 I comandi vengono in genere riportati in base al contesto, per ridurre il numero di comandi che utente in qualsiasi momento. Tuttavia, è anche necessario riutilizzare menu condivisi esistenti e gruppi di comando per verificare che la struttura di comando rimane relativamente stabile tra le modifiche nel contesto.  
  
 Riutilizzo di comandi condivisi e l'inserimento di nuovi comandi vicino comandi condivisi correlati riduce la complessità IDE e crea un'esperienza più semplice.  
  
## Denominazione dei comandi  
  
### Convenzioni di denominazione  
 Comando coerenza di denominazione è fondamentale in modo che gli utenti possono trovare ed eseguire comandi, tramite riga di comando o un'associazione a tasti di scelta rapida. I nomi dei comandi inoltre comprendere l'utente scopo un comando viene utilizzato quando viene visualizzata una barra degli strumenti o in un menu di contesto o CSS.  
  
#### Denominazione dei comandi quando:  
  
-   Creare testo in modo da facilitarne la localizzazione. Per ulteriori informazioni sulla localizzazione del testo, vedere [internazionalizzazione di Visual Studio](http://msdn.microsoft.com/it-it/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Essere concisi. I comandi devono utilizzare non più di tre parole.  
  
-   Utilizzare le iniziali maiuscole lettere maiuscole\/minuscole: la prima lettera di ogni parola deve essere in maiuscolo. Per ulteriori informazioni sulla formattazione del testo in Visual Studio, vedere [Text style](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Prendere in considerazione in cui verrà inserito il comando. Si tratta di un menu di primo livello o un riquadro a comparsa? Ad esempio, quando i comandi di allineamento raggruppamento nel riquadro a comparsa, i comandi di primo livello devono essere "Allineamento" e i comandi del riquadro a comparsa deve essere "Left" "Right", "Center", "giustifica" e così via. Sarebbe inutile denominare i comandi del riquadro a comparsa "Allinea a sinistra" o "Allinea a destra".  
  
     ![Visual Studio Format menu](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502\-a\_FormatMenu")  
  
### Uso di icone con comandi  
 Essere riserva nell'uso dell'icona di associazione con i comandi. Anche se l'associazione di un'immagine univoca con un comando di accelerare la capacità dell'utente per identificare il comando, si verificano sempre in modo efficiente e rappresentazione visiva con utilizzo eccessivo di immagini. Le regole seguenti della Guida quando si decide se creare un'icona del comando.  
  
#### Usare un'icona con un comando solo se:  
  
-   Lo stesso comando con l'icona associata in un altro prodotto Microsoft principali, ad esempio una delle applicazioni Microsoft Office.  
  
-   Il comando verrà inserito in una barra degli strumenti predefinita.  
  
-   Il comando è una specializzazione che gli utenti possono aggiungere a una barra degli strumenti mediante il **"Personalizza..."** finestra di dialogo.  
  
## Chiavi di accesso e di scelta rapida  
  
### Panoramica  
 Esistono due tipi di chiave da tastiera:  
  
-   **Le chiavi di accesso** \(noto anche come tasti di scelta rapida\) consentono l'accesso della tastiera tramite i menu per l'esecuzione di comandi e a ogni etichetta nella finestra di dialogo dell'interfaccia utente. Chiavi di accesso sono principalmente a scopo di accessibilità, vengono assegnate a tutti i menu e la maggior parte dei controlli finestra di dialogo, non devono essere memorizzate, influenza solo la finestra corrente e sono localizzate.  
  
-   **Tasti di scelta rapida** principalmente utilizzare controllo \(Ctrl\) e le sequenze di tasti funzione \(Fn\). Sono più progettati per gli utenti esperti e aiuto della produttività. Essi vengono assegnati solo per i comandi utilizzati più frequentemente e consentire l'accesso rapido mentre viene ignorata dal menu principale. Tasti di scelta rapida sono destinati a essere memorizzate e per tale motivo deve essere assegnato coerente con lo schema di profilo. Schemi di tasti di scelta rapida possono variare da un profilo a profilo. Un utente può personalizzare i tasti di scelta rapida tramite **Strumenti \> Opzioni \> tastiera**.  
  
### Assegnazione di tasti  
 Chiavi di accesso sono costituiti da chiavi Alt più caratteri alfanumerici. Assegnare una chiave di accesso per ogni voce di menu senza eccezione. Seguire le convenzioni comuni per l'assegnazione di tasti e Windows. ad esempio, la chiave di accesso per **File \> Nuovo** deve essere sempre **Alt, F, N**.  
  
 Non utilizzare single\-pixel\-width lettere, ad esempio "i" \(in caratteri maiuscoli o minuscoli\) o minuscolo "l" e non utilizzare caratteri con tratti discendenti \(g, j, p, q e y\) come queste sono difficili da individuare.  
  
 Evitare di utilizzare le chiavi duplicate quando possibile. Nei casi in cui la duplicazione è inevitabile, il sistema di menu gestisce i conflitti in base a tutti i comandi che usano la chiave. Ad esempio, per un ipotetico "Number" comando del menu File che coincide con la chiave di accesso "N", **Alt, F, N** creerebbe un nuovo file, e **Alt, F, N, N** eseguirà il comando "Number".  
  
### L'assegnazione di tasti di scelta rapida  
 Evitare di assegnare nuovi tasti di scelta rapida, poiché non sono necessarie per ogni comando e imposta il sistema e memoria di utente, se eccessivo. Dati dal programma \(analisi\) indicano che gli utenti di Visual Studio utilizzare solo un piccolo subset delle scelte rapide integrate.  
  
 Durante la definizione di tasti di scelta rapida, seguire queste regole:  
  
-   **Utilizzare il controllo \(Ctrl\) e le sequenze di tasti funzione \(Fn\).**  
  
-   **Mantenere i collegamenti utilizzati di frequente.** Mantenere i collegamenti più diffusi.  
  
-   **Più semplice digitare tasti di scelta rapida dell'editor.** Eseguire l'associazione al tipo di scelta rapida ai comandi che gli sviluppatori devono la maggior parte durante la scrittura di codice. Ad esempio, **Edit.InvokeSmartTag** deve disporre di un tasto di scelta rapida come Ctrl \+ e non Alt \+ Maiusc \+ F10.  
  
-   **Tutti i processi in modo coerente con tema tasti di scelta rapida.**  
  
-   **Attenersi alle linee guida di Windows per determinare quali modificatore chiavi da applicare.** Utilizzare le combinazioni di tasti Ctrl per i comandi che hanno effetti su larga scala, ad esempio i comandi che si applicano all'intero documento. Utilizzare le combinazioni di tasti MAIUSC per comandi che consentono di estenderanno o integrano le azioni del tasto di scelta rapida standard. Non utilizzare combinazioni di Ctrl \+ Alt.  
  
-   **Rimuovere i collegamenti estranei.** Se si dispone di una funzionalità legacy, provare a rimuovere i collegamenti che vengono utilizzati con estrema infrequency \(meno di 10 volte dai dati di analisi utilizzo software\) o infrequency moderato \(meno di 100 volte dai dati di analisi utilizzo software\) se una chiave di accesso consente di accedere rapidamente al comando stesso. Ad esempio: C Alt, H, verrà aperto\/sommario della Guida.  
  
 Non è un modo semplice per verificare la disponibilità di scelta rapida. Se si desidera aggiungere un collegamento, seguire questi passaggi:  
  
1.  Controllare l'elenco dei [scelte rapide da Visual Studio 2013](http://visualstudioshortcuts.com/2013/) per determinare se sono presenti comandi simili a quelle in uso con gruppo.  
  
2.  Passare a **Strumenti \> Opzioni \> ambiente \> tastiera** e testare il collegamento. Controllare che ogni schema di mappatura della tastiera dicitura "Applica il seguente schema di mappatura della tastiera aggiuntivi". Controllare i profili in generale, c\#, VB e C\+\+, come quelli condividere collegamenti univoci. Il collegamento è disponibile se non è mappato in uno di tali posizioni.