---
title: "Animazioni per Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
---
# Animazioni per Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Nozioni fondamentali di animazione  
  
### Procedure consigliate di animazione in Visual Studio  
 Seguire queste regole per garantire stili di animazione semplice e coerente tra IDE di Visual Studio.  
  
-   **In modo selettivo.** Limitare le animazioni a quelle utilizzate per scopi specifici.  
  
-   **Intervallo e la velocità sono importanti** per garantire che le transizioni aspetto naturale e veloce:  
  
    -   Completare le transizioni animate all'interno di un mezzo secondo \(500 millisecondi\).  
  
    -   Le animazioni che si verificano spesso devono essere sufficientemente rapido che non interrompono del flusso di lavoro dell'utente.  
  
    -   Le animazioni non devono essere in modo rapido o jarring che è difficile da comprendere, ma non tanto lenta che rende uno impazienti per la transizione alla fine.  
  
    -   Utilizzare la proprietà variabile per enfatizzare l'importanza. Ad esempio, durante l'esplorazione tramite una sequenza di elementi in un diagramma classi, velocità e le transizioni tra gli elementi quindi rallentare per concentrarsi sugli elementi importanti.  
  
-   **Utilizzare interpolazione lineare graduale** da uno stato a altro, fornendo un senso di movimento naturale e tranquilla  
  
-   Quando possibile, **utilizzare un'animazione sottile al passaggio del mouse** per indicare elementi interattivi sotto il mouse.  
  
-   Se si utilizzano frequentemente animazioni nelle funzionalità quindi **forniscono un mezzo per disattivarli** locale \(per tutte le caratteristiche\) come opzione nel **Strumenti \> Opzioni** finestra di dialogo.  
  
-   **Solo un'animazione deve verificarsi in un momento** e trasmettere solo una parte delle informazioni.  
  
-   **Accorgimento è importante.** Nella maggior parte dei casi animazione non dispone di un intervento dell'utente richiesta per soddisfare lo scopo. Piccole modifiche nell'intervallo, la sequenza e il comportamento potrebbero influire significativamente sulle percezione e possono fare la differenza tra un'animazione efficace e inefficace.  
  
-   Quando si utilizza l'animazione per attirare l'attenzione su qualcosa, **Assicurarsi che vale la pena di interrompere l'utente**di concentrazione.  
  
-   **Quando lo stato di avanzamento o lo stato** le animazioni:  
  
    -   Non visualizzare più lo spostamento di stato di avanzamento durante il processo sottostante non è un avanzamento.  
  
    -   Distinguere indeterminati processi dai processi determinati.  
  
    -   Assicurarsi che un'animazione disponga identificabili stati di completamento e non riuscite.  
  
    -   Ridurre al minimo l'utilizzo di animazioni di effetto che mostra lo stato e assicurarsi che hanno un valore reale, fornendo informazioni aggiuntive dell'utilizzo effettivo. Esempi di situazioni di emergenza e modifiche di stato temporaneo  
  
#### Non:  
  
-   Utilizzare i movimenti di piccole dimensioni \(spostamento in dimensioni ridotte\), preferendo dissolvenza e modifica tramite lo spostamento di oggetti.  
  
-   Usa animazioni che si verificano su una vasta area dell'area dello schermo. Indipendentemente dalle dimensioni, questo stile di animazione è fuorviante per l'utente.  
  
-   Usa animazioni che non riguardano l'oggetto su che utente è attualmente attivo o l'interazione con.  
  
-   Usa animazioni che richiedono l'interazione dell'utente per reimpostare lo stato, ad esempio imponendo all'utente di rispondere a una notifica in modo da rendere arrestare lampeggiante lampeggiante. L'interazione con essi in alcun modo dovrebbe essere sufficiente per non prenderli in considerazione.  
  
 Per ulteriori informazioni sulle applicazioni per queste procedure consigliate, vedere [Modelli di animazione](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### Metriche di animazione  
  
-   Il sistema deve riflettere in modo visibile ai movimenti utente meno di 10 millisecondi.  
  
-   Transizioni animate non richiede più di 500 millisecondi per il completamento.  
  
-   È un modo per compensare le transizioni che richiedono tempi più lunghi per separarlo in due parti; la prima parte di un'animazione, ad esempio, potrebbe essere il contenitore di contenuto vuoto \(fino a 500 millisecondi\) seguito da dissolvenza contenuta nel contenitore \(fino a 500 millisecondi\).  
  
-   Per i tempi di caricamento che possono essere calcolati, è preferibile utilizzare un indicatore di stato determinante \(indicatore di stato %\-fine\).  
  
-   Per i tempi di caricamento che non possono essere calcolati, un indicatore di occupato, ad esempio un cursore o l'animazione di rotazione incorporato \(caricamento o indicatore di utilizzo\) è appropriato.  
  
### Animazione di communicator  
 Nell'interfaccia utente di Visual Studio, animazione funge solo da uno strumento di comunicazione.  Viene utilizzato per comunicare un'ampia gamma di informazioni, ad esempio modifiche strutturali nell'interfaccia utente. ad esempio, quando un menu apre o chiude. Animazione consente di visualizzare il comportamento di dipendenti dal tempo di sistemi complessi, ad esempio la visualizzazione di stato di installazione o essere utilizzato per attirare l'attenzione con avvisi e notifiche.  
  
 Le animazioni dell'interfaccia utente vengono in genere utilizzati in quattro modi: visualizzare, attirare l'attenzione, simulare e indicare risposta volte\/stato di avanzamento.  
  
#### Visualizzare  
 Animazione può evidenziare la natura degli oggetti tridimensionale e rendono più semplice per gli utenti di visualizzare la struttura spaziale. A tale scopo, l'animazione potrebbe necessario per ruotare l'oggetto in un cerchio completo, lentamente attivarla e viceversa, o portare l'oggetto più vicino e leggermente aumentarne le dimensioni per evidenziare rollover o lo stato attivo.  
  
 Sebbene gli oggetti tridimensionali possono essere spostati con il controllo utente, la finestra di progettazione deve determinare in anticipo \(a livello di codice o manualmente\) come per il miglior animare un movimento che vengono fornite informazioni sugli ottimale dell'oggetto. Questa programmato animazione può quindi essere attivata dall'utente posizionando il cursore sull'oggetto, mentre i movimenti controllata dall'utente richiedono all'utente di capire come modificare l'oggetto. Limitare il movimento di un singolo asse o un orientamento alla volta. la scala, rotazione, o convertire, ma non più di una contemporaneamente.  
  
 La categoria Visualizza include gli aspetti dei dati, relazioni, stato, struttura, sequenza e ora.  
  
##### Dati  
 Vengono illustrate informazioni complesse e variabili:  
  
-   Spostarsi all'interno di visualizzazioni di informazioni quali grafici e diagrammi  
  
-   L'esecuzione di istruzioni tramite una sequenza, tour guidato e paging  
  
-   Chiamare i dettagli, che punta e l'evidenziazione delle informazioni specifiche  
  
-   Sovrapposizione di dettagli e ulteriori informazioni su un elemento con stato attivo  
  
-   Morphing da una rappresentazione struttura o dell'organizzazione a un altro  
  
-   Che rappresentano le modifiche nel tempo utilizzando i dispositivi di scorrimento, ruote scatto riquadro attività e i controlli di trasporto \(play, stop e pause\).  
  
##### Relazioni  
  
-   Viene illustrato come gli elementi sono correlati tra loro o gli elementi che sono correlate a un determinato elemento.  
  
-   Mostra le relazioni di gerarchie e padre\-figlio o pari livello  
  
-   Un elemento genera un'altra  
  
-   Riduce al minimo un elemento a un altro elemento  
  
-   Un elemento collegato a un altro  
  
##### Stato  
  
-   Aggiornamenti del contenuto.  
  
-   Selezione e lo stato attivo per utente  
  
-   Stato  
  
-   Errori  
  
##### Struttura  
  
-   La trasformazione tramite pivot in un nodo della struttura  
  
-   Il riorientamento  
  
-   Ridurre al minimo e ottimizzare, o espandere e comprimere  
  
##### Sequence  
  
-   Sequenza di presentazione  
  
-   Capovolgimento di immagini  
  
##### Ora  
  
-   Mostra modifiche nel tempo, l'intervallo di tempo e screencast  
  
-   Spostarsi smaltimento, Annulla e Ripeti  
  
-   Ripristinare lo stato cronologico  
  
#### Attirare l'attenzione  
 Se l'obiettivo è per attirare l'attenzione dell'utente a un singolo elemento da diversi o per avvisare l'utente per informazioni aggiornate, un'animazione potrebbe essere appropriata. Ad esempio, una pagina iniziale applicazioni potrebbe impiegare un pulsante Guida introduttiva che verrà espanso in posizione dopo il caricamento della pagina.  
  
 Come regola, l'ultimo elemento di spostamento nella schermata attrae l'attenzione dell'utente.  In una serie di elementi animati, l'attenzione dell'utente seguirà l'ultimo oggetto mobile.  
  
##### Avviso  
  
-   Avvisare l'utente, attirare l'attenzione, visualizzare lo stato di avanzamento  
  
-   Mostra che un elemento viene eseguito correttamente o non correttamente o Mostra lo stato di avanzamento o modifiche di stato di avanzamento  
  
-   Richiedere agli utenti durante un'attività, ad esempio ricerca di ulteriori informazioni online o di formazione sull'attività corrente  
  
##### Notifiche  
  
-   Avvisare l'utente su una condizione di errore  
  
-   Interrompere l'utente per vedere se desiderano allontanarsi  
  
-   Delicatamente informare l'utente che un processo è stato completato o modificato, ad esempio quando il download è stato completato.  
  
#### Simulare  
 In questa categoria sono physicality e dimensionalità.  
  
-   Illustrare da dove provengono gli oggetti o in cui accedono al  
  
-   Espandere e comprimere o aprire e chiudere  
  
-   Panoramica, lo scorrimento e pagina attiva  
  
-   Sovrapposizione e l'ordine z  
  
-   Sequenza e accordion  
  
-   Capovolgimento e rotazione dell'interfaccia utente  
  
#### Indicatori di risposta e lo stato di avanzamento  
 Gli indicatori di stato sono un paio di importanti vantaggi:  
  
-   Entrambi gli indicatori di stato indeterminato e determinato rassicurare l'utente che il sistema non danneggiato e sta lavorando il problema.  
  
-   Gli indicatori determinato per assegnare all'utente che un senso di avanzamento dell'azione viene eseguita l'operazione, nonché un'idea di recupero di più da vicino alla fine.  
  
##  <a name="BKMK_AnimationPatterns"></a> Modelli di animazione  
  
### Panoramica  
 Le animazioni in Visual Studio sono progettate per rendere disponibile una funzione specifica e ostacolare la produttività dell'utente. Caratteristiche di animazione generale aderire in modo da includere:  
  
-   Piccole e discreto  
  
-   Naturali e realistici  
  
-   Sottile e avvolta  
  
-   Veloce ed efficiente  
  
-   Ridotti, non accelera l'esecuzione  
  
 Nella figura seguente mostra gli stili di animazione consigliati per l'utilizzo in Visual Studio. Nessuna animazione e animazioni poco evidenti, ad esempio la dissolvenza in entrata \/ dissolvenza sono utilizzati più di frequente. Applicazione limitata dello spostamento animazioni come espandere e comprimere, X e Y posizione, modifica e la rotazione.  
  
 ![Recommended animation styles for Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202\-a\_VSAnimStyles")  
  
 **Stili di animazione consigliati per Visual Studio**  
  
#### Vengono visualizzati e nascosti  
 Con questo modello, un elemento passa da visibili di fuori della visualizzazione e viceversa senza un'animazione di transizione:  
  
 ![Appear&#47;Disappear animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202\-b\_AppearAndDisappear")  
  
##### Utilizzo corretto  
 Elementi dell'interfaccia utente aggiornati che richiedono immediatamente compaiano o scompaiano in modo che l'utente non distrarre né nascosto. Inoltre, animazioni mobile lenta potrebbero essere considerate un trascinamento delle prestazioni, che non verrà eseguita con lo stile vengono visualizzati e scompaiono.  
  
##### Utilizzo non corretto  
 Casi in cui dell'interfaccia utente viene visualizzato immediatamente che l'utente ha idea di cosa è successo e aggiunta di un'animazione contribuirebbe con la comprensione del contesto.  
  
##### Proprietà animazione  
 L'intervallo di tempo in genere è zero secondi.  
  
##### Esempi  
  
-   Nascondi automaticamente le finestre degli strumenti  
  
-   Attivazione della tastiera editor dell'interfaccia utente, ad esempio IntelliSense e la Guida ai parametri  
  
-   Aree di codice di espansione e compressione  
  
#### Dissolvenza in entrata e dissolvenza  
 Con questo modello, un elemento dell'interfaccia utente passa da non visibile \(0% di opacità\) visibile \(opacità al 100%\) o viceversa:  
  
 ![Fade&#45;in&#47;Fade&#45;out animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202\-c\_FadeInFadeOut")  
  
##### Utilizzo corretto  
 Animazione dell'interfaccia utente è più consigliato. Si tratta di un sottile effetto che aggiunge interesse senza interrompere il flusso. In alcuni casi, l'utente potrebbe non anche tenere presente che non vi è un'animazione e semplicemente percepisce un sistema di interfaccia utente semplice e propagazione.  
  
##### Proprietà animazione  
  
-   Avvio di opacità: 0% per la dissolvenza, 100% per la dissolvenza  
  
-   Fine opacità: 100% per la dissolvenza, 0% per la dissolvenza  
  
-   Durata: 200 millisecondi autonoma, 100 millisecondi, utilizzato come parte di una sequenza di animazione di combinazione  
  
-   Stile di interpolazione: InOut seno  
  
##### Esempi  
  
-   Nascondi automaticamente le finestre degli strumenti  
  
-   Menu di aperto e chiusura  
  
-   Transizioni scheda sfondo e primo piano  
  
#### Sfumatura di colore da A B  
 Con questo modello viene modificato un elemento dell'interfaccia utente dal colore colore b:  
  
 ![Color blend animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202\-d\_ColorBlend")  
  
##### Utilizzo corretto  
 Come una transizione animata quando un elemento dell'interfaccia utente cambia colore da uno stato o contesto a altro.  
  
##### Proprietà animazione  
  
-   Colore iniziale: specifico dell'interfaccia utente  
  
-   Colore finale: specifico dell'interfaccia utente  
  
-   Durata: 200 millisecondi autonoma, 100 millisecondi, utilizzato come parte di una sequenza di animazione di combinazione  
  
-   Stile di interpolazione: InOut seno  
  
##### Esempi  
  
-   Documentare le transizioni di stato di finestra \(attivo, ultimo attive e inattive\)  
  
-   Strumento delle transizioni di stato di finestra \(con stato attivo e con stato non attivo\)  
  
#### Espandere e comprimere  
 Con questo modello, un elemento dell'interfaccia utente si espande in X, Y o entrambe le direzioni:  
  
 ![Expand&#47;Contract animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202\-e\_ExpandContract")  
  
##### Utilizzo corretto  
 Come una transizione animata quando un elemento dell'interfaccia utente cambia dimensioni da un contesto a altro.  
  
##### Proprietà animazione  
  
-   Scala x: % o una specifica dimensione \(in pixel\)  
  
-   Scala Y: % o una specifica dimensione \(in pixel\)  
  
-   Posizione di ancoraggio: in genere angolo superiore sinistro \(per le lingue da sinistra a destra\) o superiore a destra \(per le lingue da destra a sinistra\)  
  
-   Durata: 200 millisecondi autonoma, 100 millisecondi, utilizzato come parte di una sequenza di animazione di combinazione  
  
##### Esempi  
  
-   Pannello di Esplora architettura espandere e comprimere  
  
-   Elemento di pagina iniziale espandere e comprimere  
  
#### Modifica di posizione X\-Y  
 Con questo modello, un elemento dell'interfaccia utente modifica la posizione X o Y o entrambi:  
  
 ![X&#47;Y position change animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202\-f\_XYPositionChange")  
  
##### Utilizzo corretto  
 Come una transizione animata quando un elemento dell'interfaccia utente cambia posizione da un contesto a altro.  
  
##### Proprietà animazione  
  
-   Posizione di inizio X e Y: specifico dell'interfaccia utente  
  
-   Posizione finale X e Y: specifico dell'interfaccia utente  
  
-   Tracciato di movimento: nessuno  
  
-   Durata: 200 millisecondi autonoma, 100 millisecondi, utilizzato come parte di una sequenza di animazione di combinazione  
  
-   Stile di interpolazione: InOut seno  
  
##### Esempio  
 Riordinamento di scheda  
  
#### Ruotare  
 Con questo modello consente di ruotare l'elemento dell'interfaccia utente:  
  
 ![Rotate animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202\-g\_Rotate")  
  
##### Utilizzo corretto  
 Solo per l'indicatore di stato indeterminato rotante.  
  
##### Proprietà animazione  
  
-   Grado di rotazione: 360  
  
-   Centro di rotazione: centrale dell'oggetto  
  
-   Durata: continua  
  
##### Esempio  
 Indicatore di stato indeterminato \(rotazione\)  
  
### Azioni dell'interfaccia utente della shell comuni e consigliate le animazioni  
  
#### Scheda aperta  
  
-   Stile: vengono visualizzati  
  
-   Durata: Zero secondi  
  
 ![Tab open animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202\-h\_TabOpen")  
  
#### Scheda chiudere  
  
-   Stile: Modifica della posizione X  
  
-   Durata: 200 millisecondi  
  
 ![Tab close animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202\-i\_TabClose")  
  
#### Riordinamento di scheda  
  
-   Stile: Modifica della posizione X  
  
-   Durata: 200 millisecondi  
  
 ![Tab reorder animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202\-j\_TabReorder")  
  
#### Chiusura documento mobile  
  
-   Stile: vengono visualizzati  
  
-   Durata: 200 millisecondi  
  
 ![Close floating document animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202\-k\_CloseFloatingDocument")  
  
#### Transizione dello stato di finestra  
  
-   Stile: Per garantire la coerenza con le altre finestre, consentono il sistema operativo corrente definire l'animazione di chiusura del documento.  
  
-   Durata: 200 millisecondi  
  
 ![Window state transition animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202\-l\_WindowStateTransition")  
  
#### Menu aprirlo  
  
-   Stile: con dissolvenza in entrata  
  
-   Durata: 200 millisecondi  
  
 ![Menu open animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202\-m\_MenuOpen")  
  
#### Chiudi menu  
  
-   Stile: dissolvenza  
  
-   Durata: 200 millisecondi  
  
 ![Menu close animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202\-n\_MenuClose")  
  
#### Mostra finestra di strumento Nascondi automaticamente  
  
-   Stile: vengono visualizzati  
  
-   Durata: Zero secondi  
  
 ![Auto&#45;hide tool window animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202\-o\_AutoHideToolWindowReveal")