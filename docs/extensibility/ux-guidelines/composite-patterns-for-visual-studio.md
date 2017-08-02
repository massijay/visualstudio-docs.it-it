---
title: "Modelli compositi per Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Modelli compositi per Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Modelli compositi combinano gli elementi di progettazione e l'interazione di configurazioni distinte. Alcuni dei più importanti compositi modelli in Visual Studio per quanto riguarda la coerenza:  
  
-   [Visualizzazione dei dati](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [Per gli oggetti dell'interfaccia Utente e la lettura](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistenza e il salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="a-namebkmkdatavisualizationa-data-visualization"></a><a name="BKMK_DataVisualization"></a> Visualizzazione dei dati  
  
### <a name="overview"></a>Panoramica  
 I grafici sono uno strumento visivo per aggregare e visualizzare i dati allo scopo di migliorare il processo decisionale. Consentono agli utenti a dover affrontati molti dati, ma vale a dire poco vedere ciò che merita attenzione e ciò che potrebbe essere necessario un'azione.  
  
 L'utente trarranno vantaggio da un grafico se una delle seguenti condizioni sono vere:  
  
-   Consente il grafico agli utenti di identificare le attività in che possono funzionare?  
  
-   Il grafico consentirà agli utenti prevedere le conseguenze potenziali modifiche?  
  
-   Il grafico consentiranno agli utenti individuare tendenze e identificare modelli?  
  
-   Il grafico consentirà agli utenti di prendere decisioni migliori?  
  
-   Il grafico consentirà rispondere a una domanda specifica che gli utenti possono avere nel contesto specificato?  
  
#### <a name="general-rules-for-charts"></a>Regole generali per i grafici  
  
-   Ovviamente i dati di etichetta. Illustrazioni senza spiegazione sono semplicemente belle immagini.  
  
-   Iniziare da zero per evitare le proporzioni inclinazione assi. Dimensione della linea di lunghezza e la barra sono importanti indicatori visivi per comprendere le relazioni tra i punti dati.  
  
-   Creare grafici, non infografiche. Infografiche sono artistiche rappresentazioni di dati e l'obiettivo primario è storytelling visual. I grafici possono (e dovrebbero) essere interessante, ma lasciare che i dati parlino da soli.  
  
-   Evitare di skeumorphism, grafici grafici a barre, contrasto hashmarks e altri elementi infografica.  
  
-   Non utilizzare effetti 3D come elemento decorativo. Utilizzarle solo se è veramente integrale possibilità dell'utente di comprendere le informazioni.  
  
-   Evitare di utilizzare più linee e riempimenti, più di due colori possono rendere difficile da leggere e interpretare correttamente questo tipo di grafico.  
  
-   Non utilizzare un grafico (o qualsiasi illustrazione) come unico mezzo di comprendere il concetto o l'interazione con i dati. Questa operazione presenta difficoltà per gli utenti con problemi visivi.  
  
-   Non utilizzare grafici come gratuiti o decorativi elementi in una pagina. In altre parole, se un grafico non aggiunta che qualsiasi valore o la Guida di utenti a risolvere un problema, non utilizzarlo.  
  
### <a name="chart-types"></a>Tipi di grafico  
 Tipi di grafico utilizzato in Visual Studio includono grafici a barre, grafici a linee, un grafico a torta modificato noto come un grafico ad anello "grafico ad anello," sequenze temporali, a dispersione tracciati (denominati anche "cluster grafici") e i diagrammi di Gantt. Ogni tipo di grafico è utile per la comunicazione di un tipo di informazioni diverso.  
  
### <a name="other-charting-considerations"></a>Altre considerazioni sulla creazione di grafici  
  
#### <a name="color"></a>Colore  
 Esiste una tavolozza di colori definiti per l'utilizzo in Visual Studio di grafici specifica. La tavolozza è accessibile per i tipi principali di distinguere i colori possono essere distinti anche quando utilizzato come sezioni molto ristretto di colore. È possibile utilizzare i colori in qualsiasi combinazione di un tipo di grafico o un grafico nell'interfaccia Utente. Non è necessario utilizzare tutti i sette colori se non è necessaria una quantità di colori distinti. I colori non sono stati progettati per essere utilizzato con qualsiasi elemento di primo piano, in modo da non includere testo o le icone sopra i colori. Questi tonalità dovrebbe essere hardcoded ed esposto per la personalizzazione in **Strumenti > Opzioni** (vedere [esposizione di colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Campione|Esadecimale|RGB|  
|------------|---------|---------|  
|![Campione 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Campione BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Campione FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Campione 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Campione 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Campione 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Campione B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="a-namebkmkonobjectuia-on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Per gli oggetti dell'interfaccia Utente e la lettura  
 Questa sezione fornisce contesto per la lettura, anche noto come visualizzazione visualizzazione codice, un tipo di interfaccia Utente per gli oggetti univoci a Visual Studio.  
  
### <a name="overview"></a>Panoramica  
  
-   Per gli oggetti dell'interfaccia Utente di assegnare all'utente ulteriori informazioni o interattività senza pregiudicare le loro attività principale.  
  
-   Il motivo principale per l'interfaccia Utente per gli oggetti in Visual Studio è noto come "informazioni al momento di attenzione".  
  
-   Interfaccia Utente per gli oggetti in Visual Studio è sia in linea o a virgola mobile e durevole o temporaneo.  
  
    -   Visualizzazione Anteprima di codice, un tipo di oggetto dell'interfaccia Utente in Visual Studio, è in linea e durevole.  
  
    -   CodeLens, un tipo di oggetto dell'interfaccia Utente in Visual Studio, è temporaneo e a virgola mobile  
  
 Informazioni sulle modalità di funzionamento di un frammento di codice o la ricerca di informazioni dettagliate su tale codice, spesso richiede allo sviluppatore di passare contesto e altro contenuto o un'altra finestra. Questi cambiamenti di contesto possono essere problematici, perché gli utenti possono perdere lo stato attivo per le attività originale se si lascia la finestra principale. Inoltre, recupero che ripristinare contesto può essere difficile, soprattutto se il passaggio di windows ha causato il codice originale venga nascosto da altra interfaccia Utente.  
  
 Per gli oggetti dell'interfaccia Utente segue uno schema denominato "informazioni al momento di attenzione". Questi messaggi, le finestre popup e finestre di dialogo concedono agli utenti informazioni aggiuntive, rilevanti che aggiunge chiarimenti o interattività senza perdere lo stato attivo sul loro attività principale. Esempi dell'interfaccia Utente per gli oggetti delle finestre popup che vengono visualizzati quando l'utente passa il puntatore del mouse su un'icona nell'area di notifica, la sottolineatura ondulata rossa sotto una parola e la visualizzazione Anteprima introdotte in Visual Studio 2013.  
  
### <a name="decision-points"></a>Punti decisionali  
 In Visual Studio, esistono diversi modi per usare questo modello di informazioni al momento di attenzione. Scegliere il meccanismo di destra e implementarla in modo coerenza e prevedibile è essenziale per l'esperienza complessiva. In caso contrario, è possibile che venga visualizzati agli utenti un'esperienza di confusione o incoerenti che comporta un peggioramento lo stato attivo dal contenuto stesso.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Relazioni tra principale e di dettaglio del contenuto  
 Informazioni al momento di attenzione viene utilizzate per visualizzare una relazione tra il contenuto che l'utente è attivo (il contenuto "master") e altre correlate (contenuto di "detail"). In questo modello, il contenuto di dettaglio è chiaramente correlato al contenuto, l'utente lavora con e può essere visualizzato vicino il contenuto principale. Informazioni aggiuntive o informazioni che non possono essere riepilogate il contenuto senza appesantire master devono seguire un altro modello, ad esempio una finestra degli strumenti.  
  
-   **Sempre** visualizzare il contenuto di dettaglio in prossimità del contenuto principale.  
  
-   **Sempre** Assicurarsi che il contenuto di dettaglio ancora consente all'utente di rimanere concentrati sul contenuto principale. Il modo migliore per ottenere questo risultato è spesso il rendering del contenuto di dettaglio come vicino del contenuto master come possibili. Questa operazione può essere eseguita per il rendering del contenuto di dettaglio in una finestra popup accanto al contenuto principale o eseguendo il rendering inline contenuto dettaglio sotto il contenuto principale.  
  
-   **Mai** utilizzare informazioni al momento di attenzione che accetta l'utente dal contenuto principale. Se è necessario visualizzare il contenuto di dettaglio separatamente, esporre un'azione esplicita che consente all'utente di eseguire questa operazione.  
  
#### <a name="design-details"></a>Dettagli della progettazione  
 Dopo aver determinato che per gli oggetti dell'interfaccia Utente è la scelta giusta, sono disponibili quattro considerazioni di progettazione principale:  
  
1.  **Persistenza:** il contenuto deve essere permanente o temporaneo?   
    Gli utenti desiderano mantenere visibile per fare riferimento o interagire con le informazioni? O gli utenti dovranno osservare rapidamente le informazioni e quindi continuare con l'attività principale?  
  
2.  **Tipo di contenuto:** il contenuto sarà informativo, eseguibili o spostamento?   
    L'utente necessita di ulteriori dettagli sul contenuto master? L'utente è necessario per completare un'attività che influisce sul contenuto master? O l'utente deve essere indirizzata a un'altra risorsa?  
  
3.  **Tipo di indicatore:** ha un indicatore ambiente senso?   
    Possano le informazioni da riepilogati in modo utile e visualizzare il contenuto senza appesantire master?  
  
4.  **I movimenti:** quali movimenti verrà utilizzato per richiamare e chiudere l'interfaccia Utente?   
    Come verrà visualizzato il contenuto di dettaglio e invia immediatamente l'utente? Esiste il valore per l'aggiunta di un movimento, ad esempio il blocco per passare tra gli stati temporanei e permanenti?  
  
 Ognuno di questi punti di quattro decisione avrà un impatto sui componenti principali dell'interfaccia Utente per gli oggetti.  
  
### <a name="on-object-ui-components"></a>Componenti dell'interfaccia Utente per gli oggetti  
  
1.  Tipo di contenitore (Visualizzatore di contenuto)  
  
    -   Virgola mobile  
  
    -   Inline  
  
2.  Tipo di contenuto  
  
    -   Messaggio informativo: dati che potrebbero essere statica o dinamica  
  
    -   Utilizzabili: i comandi modificare il contenuto principale  
  
    -   Navigazione: collegamenti che porterà l'utente a un'altra finestra o applicazione, ad esempio MSDN  
  
3.  Movimenti  
  
    -   Chiamata  
  
    -   Licenziamento  
  
    -   Il blocco  
  
    -   Altre interazioni  
  
4.  Modello di persistenza e commit  
  
    -   Temporaneo  
  
    -   Durevole  
  
    -   Automatico  
  
    -   Su richiesta  
  
5.  Indicatori di ambiente (facoltativi)  
  
    -   Sottolineatura di linee a zigzag  
  
    -   Icona smart tag  
  
    -   Altri indicatori di ambiente  
  
#### <a name="container-content-presenter-type"></a>Tipo di contenitore (Visualizzatore di contenuto)  
 Sono disponibili due opzioni principali disponibili per presentare il contenuto nel punto di attenzione:  
  
1.  **Inline:** un presentatore inline, ad esempio la visualizzazione Anteprima introdotta nell'Editor di Visual Studio 2013 codice per fare spazio a nuovi contenuti spostando il contenuto esistente.  
  
    -   **Preferisce** Presenter inline se si prevede che gli utenti desiderano dedicare una quantità significativa di tempo che fa riferimento a o l'interazione con il contenuto presente.  
  
    -   **Evitare** Presenter inline se si prevede che gli utenti dovranno visualizzare rapidamente le informazioni è presente, quindi continuare con l'attività principale con un'interruzione minima.  
  
2.  **A virgola mobile:** un presenter mobile si trova più vicino al contenuto selezionato possibile ma non modifica il layout del contenuto esistente. Varie strategie possono essere utilizzate, ad esempio la visualizzazione di un pannello del contenuto mobile tramite il più vicino disponibile spazio per il simbolo selezionato.  
  
    -   **Preferisce** mobile Presenter se si prevede che gli utenti dovranno visualizzare rapidamente le informazioni è presente, quindi continuare con l'attività principale con un'interruzione minima.  
  
    -   **Evitare** mobile Presenter se si prevede che gli utenti dovranno dedicare una quantità significativa di tempo che fa riferimento a o l'interazione con il contenuto è presente.  
  
#### <a name="content-type"></a>Tipo di contenuto  
 Esistono tre tipi di contenuto che possono essere visualizzati all'interno di qualsiasi contenitore dell'interfaccia Utente per gli oggetti. È possibile visualizzare qualsiasi combinazione di questi tipi di informazioni. Sono tre tipi:  
  
1.  **Messaggio informativo:** la maggior parte dell'oggetto contenitori dell'interfaccia Utente verranno visualizzato un tipo di contenuto informativo. Il contenuto può rappresentare informazioni sullo stato attuale dell'ambiente o può rappresentare informazioni su uno stato potenziali future dell'ambiente. Ad esempio, può essere utilizzato per mostrare l'effetto di un comando specifico, ad esempio un'operazione di refactoring, sul codice esistente.  
  
    -   **Sempre** utilizzare la rappresentazione canonica di informazioni da visualizzare. Ad esempio, codice dovrebbe essere simile al codice, con l'evidenziazione della sintassi e deve rispettare qualsiasi tipo di carattere e altre impostazioni di ambiente impostate dall'utente.  
  
    -   **Sempre** considerare il supporto di tutte le azioni sul contenuto informativo che sarebbe possibile se stesse informazioni viene presentate come contenuto principale. Ad esempio, se la presentazione di codice esistente all'interno di un contenitore dell'interfaccia Utente per gli oggetti di prendere in considerazione la possibilità di esplorare e modificare il codice di supporto.  
  
    -   **Sempre** si consiglia di utilizzare un colore di sfondo diverso se la presentazione di contenuto informativo che rappresenta uno stato futuro potenziale.  
  
2.  Eseguibili: alcuni contenitori di oggetto dell'interfaccia Utente fornirà la possibilità di eseguire alcune azioni sul contenuto principale, ad esempio un'operazione di refactoring.  
  
    -   **Sempre** posizionare i comandi utilizzabili separatamente dal contenuto informativo.  
  
    -   **Sempre** abilitare e disabilitare le azioni quando appropriato.  
  
    -   **Sempre** fare riferimento alle linee guida standard per rappresentare comandi all'interno di finestre di dialogo.  
  
    -   **Sempre** mantenere minimo il numero di azioni che vengono esposti in un contenitore dell'interfaccia Utente in oggetto assoluto. L'interazione con l'interfaccia Utente dell'oggetto deve essere un'esperienza semplice e veloce. L'utente non è necessario spendere energia sulla gestione il contenitore dell'interfaccia Utente dell'oggetto stesso.  
  
    -   **Sempre** considerare come e quando un contenitore dell'interfaccia Utente per gli oggetti verrà chiuse o chiusa. Come procedura consigliata, qualsiasi azione che si conclude la finestra di dialogo tra lo schema e i dettagli del contenuto deve chiudere anche il contenitore dell'interfaccia Utente per gli oggetti quando tale azione viene richiamata.  
  
3.  **Spostamento:** alcuni per gli oggetti contenitori dell'interfaccia Utente includono i collegamenti che consentono all'utente a un'altra finestra o applicazione, ad esempio l'apertura di un articolo MSDN in web browser dell'utente.  
  
    -   **Sempre** anteporre qualsiasi collegamento ipertestuale con "Open", in modo che gli utenti non saranno sorpresi da cui si accede ad alcuni altri contenuti.  
  
    -   **Sempre** separare collegamenti utili collegamenti.  
  
#### <a name="ambient-indicators-optional"></a>Indicatori di ambiente (facoltativi)  
 Gli indicatori di ambiente possono essere impercettibile, incluso il testo visualizzato in un colore contrastante dal resto del codice, o ovvio, inclusi i simboli tickler come sottolineature a zigzag e icone di smart tag. Gli indicatori di ambiente comunicano la disponibilità di ulteriori informazioni rilevanti. Idealmente, forniscono informazioni utili anche senza richiedere all'utente di interagire con essi.  
  
-   **Sempre** posizionare un indicatore di ambiente in modo che non distrarre o sovraccaricare l'utente. Se non è possibile posizionare un indicatore di ambiente in modo, si consideri un'altra soluzione.  
  
-   **Sempre** posizionare l'indicatore di ambiente il più vicino possibile al contenuto a cui è correlato.  
  
-   **Sempre** tenta di creare un indicatore che riepiloga le informazioni che vengono resi disponibili. Si consiglia di fornire un conteggio del numero di elementi dati disponibili (ad esempio, "3 riferimenti" anziché semplicemente "Riferimenti") o pensare a un altro modo per riepilogare i dati.  
  
    -   In casi in cui i dati per un indicatore non sono sempre calcolati e visualizzati immediatamente si consiglia di fornire feedback progressivo come vengono calcolati i valori. Si consideri ad esempio di animazione delle modifiche che riflettono gli aggiornamenti ai dati disponibili, simili al modo in cui che il riquadro animato di posta elettronica in Windows Phone consente di aggiornare il numero di messaggi di posta elettronica non letti.  
  
-   **Mai** aggiungere ulteriori indicatori a un utente può eseguire ragionevolmente per una determinata parte del contenuto. Gli indicatori di ambiente devono essere utili senza alcuna interazione da parte dell'utente. Gli indicatori di perdono loro ambiente se richiedono overflow e altri controlli di gestione per importarli in vista.  
  
#### <a name="gestures"></a>Movimenti  
 Un aspetto fondamentale consentendo all'utente di concentrare l'attenzione sul contenuto principale è supportando i movimenti di destra per aprire e chiudere il contenuto di dettagli aggiuntivi.  
  
-   **Sempre** richiedono all'utente di eseguire alcuni movimenti esplicito per aprire i contenuti aggiuntivi. I movimenti aperti comuni includono:  
  
    -   **Al passaggio del mouse:** le descrizioni comandi o contenuto informativo non interattivo  
  
    -   **Comando esplicito:** presenter inline  
  
    -   **Fare doppio clic sull'indicatore di ambiente:** finestra popup CodeLens  
  
-   **Sempre** Elimina il contenuto di dettaglio ogni volta che l'utente preme il tasto Esc.  
  
-   **Sempre** prendere in considerazione il contesto dell'interfaccia Utente per gli oggetti. Per contenuto Presenter che consentono l'interazione all'interno del contenitore, valutare attentamente se si desidera visualizzare informazioni aggiuntive al passaggio del mouse, che è probabile che sia problematica per flusso di lavoro dell'utente.  
  
-   **Mai** visualizzare il contenuto al passaggio del mouse che sembrano essere modificabile o invita l'interazione dell'utente. Questo comportamento può causare frustrazione utenti se si tenta di spostare il cursore sul contenuto del corpo, come il comportamento standard per una descrizione comando per chiudere immediatamente quando il cursore non è più sul master contenuto che l'ha prodotta.  
  
##  <a name="a-namebkmkselectionmodelsa-selection-models"></a><a name="BKMK_SelectionModels"></a> Modelli di selezione  
  
### <a name="overview"></a>Panoramica  
 Un modello di selezione è il meccanismo utilizzato per indicare e confermare le operazioni su uno o più oggetti di interesse all'interno dell'interfaccia utente. Questo argomento vengono illustrati i modelli di interazione selezione all'interno degli editor di documento di Visual Studio: editor di testo, aree di progettazione e modellazione superfici.  
  
 Gli utenti devono disporre di un metodo per indicare a Visual Studio che stanno eseguendo e Visual Studio deve rispondere in modo prevedibile con commenti e suggerimenti per gli utenti su ciò che opera su. Le differenze o una comunicazione tra l'utente e l'interfaccia utente può comportare l'utente non si verifichino più di un'azione può avere conseguenze impreviste. Spesso, l'errore non viene notata fino a quando l'utente visualizza un elemento è manca o è stato modificato. Modelli di selezione sono pertanto una delle parti più importanti della progettazione dell'interfaccia utente. Sebbene i modelli di selezione in Visual Studio sono coerenti con Windows, vi sono variazioni.  
  
 In Visual Studio, come in Windows, modelli di selezione diversi a seconda del contesto in cui si verifica l'interazione. Selezioni possono verificarsi in quattro tipi di oggetti:  
  
-   Testo  
  
-   Oggetti grafici  
  
-   Elenchi e strutture  
  
-   Griglie  
  
 All'interno di questi oggetti, sono disponibili tre tipi di selezioni:  
  
-   Contigue  
  
-   Non contigue  
  
-   Region  
  
#### <a name="scope"></a>Ambito  
 Il componente più importante della selezione consiste nel garantire che l'utente conosca quale finestra lavorano (attivazione) e in cui lo stato attivo è disponibile (selezione). Visual Studio estende la funzionalità di gestione di finestra di Windows, ma lo schema di attivazione è lo stesso: l'interazione con una finestra Visualizza lo stato attivo alla finestra. Visual Studio include due indicatori per l'attivazione: uno per le finestre di documento e uno per le finestre degli strumenti.  
  
 Finestre di documento, la finestra attiva è indicata da una scheda della finestra documento presto in primo piano e la modifica del colore di sfondo:  
  
 ![Selezione della scheda attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")  
  
 **Selezione della scheda attiva**  
  
 Finestre degli strumenti, la finestra attiva è indicata da una modifica il colore dell'area della barra del titolo della finestra degli strumenti:  
  
 ![Selezione della finestra degli strumenti attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")  
  
 **Finestra degli strumenti attiva con la selezione primaria di un nodo**  
  
 ![Selezione della finestra degli strumenti inattiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")  
  
 **Finestra degli strumenti inattiva, con latente selezione del nodo**  
  
 Quando è attiva una finestra, in base ai modelli di selezione descritti in questa sezione delle linee guida è indicato lo stato attivo.  
  
#### <a name="context"></a>Contesto  
 Visual Studio è stato progettato per mantenere un concetto sicuro del contesto, tiene traccia di in cui l'utente sta utilizzando. Solo una finestra è attiva, che si tratti di una finestra del documento o degli strumenti. Tuttavia, la finestra del documento in primo piano mantiene sempre una selezione latente. Anche se lo stato attivo potrebbe trovarsi in una finestra degli strumenti, finestra di documento che era attivo ultima viene visualizzata una selezione, anche in uno stato inattivo. Questa operazione viene eseguita per mantenere il contesto dell'utente nel documento che la modifica, evidenziandoli che Visual Studio mantiene il proprio stato in modo che possano restituire e spostarsi facilmente tra le finestre e finestre di documento.  
  
### <a name="text-selection"></a>Selezione di testo  
 Gli editor di Visual Studio che sono rigorosamente testuali, ad esempio l'editor di testo incorporato, utilizzano lo stesso modello di selezione di testo e aspetto descritte nel [Mouse e puntatori](https://msdn.microsoft.com/en-us/library/dn742466.aspx) pagina le indicazioni di interazione di esperienza utente di Windows su MSDN. Lo stato attivo nell'editor di testo è indicato da una barra verticale definita punto di inserimento. Il punto di inserimento è un singolo pixel spesso e colorato come la funzione inversa di tutti gli elementi presenti dietro di essa. Lampeggia in base alla frequenza impostata dal **velocità di intermittenza del cursore** impostazione nel **velocità** scheda della finestra il **tastiera** applet del Pannello di controllo.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Selezione contigua e indipendente  
 Selezione all'interno dell'editor di testo è solo contigue. Testo selezioni non sono consentite, ma devono essere risolto in Editor oggetti grafici non contigui. Quando il puntatore del mouse su un'area di testo, il cursore cambia in un cursore. Un singolo clic posiziona il punto di inserimento nell'editor di testo in corrispondenza della posizione di clic. Tenendo premuto il pulsante del mouse viene avviata una selezione evidenziata e rilasciare il pulsante del mouse termina la selezione evidenziata.  
  
#### <a name="region-selection-box-selection"></a>Area selezione (finestra)  
 Visual Studio supporta la selezione area nell'editor di testo e si tratta della selezione. Selezione della casella consente all'utente di selezionare un'area di testo che non segue il flusso di testo normale. Come con la selezione di testo standard, la selezione deve essere contigua. Selezione della casella viene avviata tenendo premuto il tasto Alt mentre si trascina con il mouse. Selezione della casella può essere avviata anche tenendo premuto il Alt + Maiusc e utilizzando i tasti di direzione per indicare l'area di selezione. Selezione della casella viene utilizzata la normale selezione evidenziata e Mostra il punto di inserimento lampeggiante alla fine dell'area di selezione.  
  
 ![Casella internazionali &#40; &#41; selezione in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")  
  
 **Selezione di regione (casella) in Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Aspetto di selezione del testo  
 È possibile personalizzare i colori utilizzati per la selezione attiva e inattiva nell'editor. Per personalizzare l'aspetto visivo dell'editor, un utente può passare a **Strumenti > Opzioni**, e quindi cercare in **ambiente > tipi di carattere e colori > Editor di testo**.  
  
### <a name="graphical-selection"></a>Selezione di grafica  
  
#### <a name="interaction"></a>Interazione  
 Selezione degli oggetti grafici può essere complessa e dipende da numerosi fattori:  
  
-   **Modello di selezione principale dell'editor.** Gli editor che contengono gli oggetti grafici consente inoltre di modificare testo o griglie. L'editor, ad esempio, potrebbe essere un editor di testo che supporta anche la posizione degli oggetti grafici, ad esempio la finestra di progettazione XAML di Visual Studio. Supporto di più tipi di oggetto può influire sulla modalità con cui l'utente seleziona gruppi costituiti da diversi tipi di oggetti.  
  
-   **Supporto per gli stati di selezione primaria e secondaria.** Un editor può fornire selezione primaria e secondaria stati in modo che gli oggetti possono essere modificati in contemporanea allineati tra loro, ridimensionare, e così via.  
  
-   **Supporto di modifica sul posto.** Editor consentire anche il contenuto dei rispettivi oggetti grafici da modificare. Ad esempio, un rettangolo potrebbe anche contenere testo all'interno che può essere modificato dall'utente. Inoltre, il testo potrebbe essere centrato o giustificato. La modifica sul posto prevede un livello più dettagliato dell'interazione dell'utente e pertanto richiede un set appropriato di segnali visivi per la presentazione di informazioni sullo stato per l'utente.  
  
#### <a name="mouse-interaction"></a>Interazione del mouse  
  
|Input|Risultato|  
|-----------|------------|  
|Fare clic su un oggetto non selezionato|Seleziona l'oggetto e visualizza una linea tratteggiata e quadratini di ridimensionamento, se l'oggetto è ridimensionabile.|  
|Fare clic su un oggetto selezionato|Attiva se l'oggetto supporta la modifica in loco. Facendo clic all'esterno dell'oggetto disattiva la modalità di modifica sul posto.|  
|Fare doppio clic su un oggetto|Apre il code-behind l'oggetto per la modifica e potrebbe inserire un gestore eventi predefinito, se appropriato.|  
|Puntare a un oggetto|Il puntatore fino al cursore di spostamento. L'aspetto dell'oggetto, ad esempio la luminosità o il colore, potrebbe cambiare.|  
|Scegliere un handle di selezione|Il puntatore per il cursore di ridimensionamento. Per gli oggetti che supportano la rotazione, alcuni quadratini di ridimensionamento potrebbero impostare il puntatore su un cursore rotazione come il puntatore è posizionato in modo diverso (ad esempio, spostata più lontani) per quanto riguarda il quadratino di ridimensionamento.|  
|Trascina|Anche se l'oggetto non è selezionata in precedenza, il puntatore fino al cursore di spostamento e sposta l'oggetto.|  
|Editor perde lo stato attivo|Disattiva la modalità di modifica sul posto, anche se l'oggetto conserva il contenuto e l'aspetto che aveva durante l'ultimo stato di selezione/operazione.|  
|Selezione oggetti|Indicato da un bordo, linea punteggiata o altro tipo di trattamento visivamente distinto per evidenziare i limiti dell'oggetto.|  
|Ridimensionare un oggetto selezionato|Indicato da quadratini di ridimensionamento.<br /><br /> Un oggetto ridimensionabile ha otto handle, che rappresenta ciascuna direzione in cui può essere ridimensionato. Un minor numero di handle possono essere utilizzati se l'oggetto può essere ridimensionata solo in determinate direzioni. Quando si ridimensiona un oggetto verso il basso in otto punti di controllo non è interattivi, quattro handle possono essere utilizzati. Handle dimensioni devono essere collegate alle metriche a bordo e il bordo di finestra con la **GetSystemMetrics** funzione API dimensioni proporzionalmente la risoluzione dello schermo.<br /><br /> ![Quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|  
|Ruotare un oggetto selezionato|![Punti di manipolazione di rotazione](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Interazione della tastiera  
  
|Input|Risultato|  
|-----------|------------|  
|Scheda|Sposta l'indicatore di stato attivo tra l'ordine logico di oggetti nell'editor. Può essere da sinistra a destra oppure dall'alto in basso in base alle **TabIndex** (o equivalenti) il valore di proprietà, ordine di creazione di un oggetto e lo scopo complessivo dell'editor. Maiusc + Tab consente di invertire la direzione dell'indicatore di stato attivo.|  
|Barra spaziatrice|Attiva la modalità Panoramica mentre viene mantenuto pressione di tasto. Input del mouse aggiuntivi è necessario per una panoramica della posizione del riquadro di visualizzazione.|  
|CTRL+BARRA SPAZIATRICE|Attiva la modalità zoom mentre viene mantenuto pressione di tasto. Input del mouse aggiuntivi è necessario per aumentare e diminuire il fattore di zoom.|  
|Ctrl + Alt + segno meno|Consente di ridurre il fattore di zoom di un livello.|  
|Ctrl + Alt + segno più|Aumenta il fattore di zoom di un livello.|  
|MAIUSC o Ctrl|Aggiunge l'oggetto al gruppo di selezione. CTRL consente inoltre di rimuovere gli oggetti singolarmente dal gruppo di selezione.|  
|INVIO|Esegue il comando predefinito per l'oggetto (in genere aprire o modificare).|  
|F2|Attiva la modifica sul posto per l'oggetto.|  
|Tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto premuto, incrementi minimi (ad esempio, 1 pixel alla volta)|  
|CTRL + tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto premuto, in incrementi di dimensioni maggiori (ad esempio, 10 pixel alla volta)|  
|MAIUSC + freccia chiavi|Ridimensiona gli oggetti selezionati nella direzione corrispondente, in incrementi di piccole dimensioni (ad esempio, 1 pixel alla volta)|  
|CTRL + MAIUSC + tasti di direzione|Ridimensiona gli oggetti selezionati nella direzione corrispondente, in incrementi di dimensioni maggiori (ad esempio, 10 pixel alla volta)|  
  
 Quando gli utenti modificano i controlli sul posto, potrebbe essere utile per gli oggetti ridimensionare automaticamente con l'input dell'utente. Ad esempio, se l'utente modifica un controllo label, l'etichetta deve essere incrementato per visualizzare il testo appena digitato dall'utente. Se in caso contrario, l'utente deve ridimensionare il controllo manualmente dopo la modifica del testo. Se l'utente dispone di molti dei controlli, questo diventa un rote e attività compromessa.  
  
#### <a name="graphical-containers"></a>Contenitori di grafici  
 In alcuni casi, gli editor grafici possono essere utilizzati per altri oggetti grafici, ad esempio il controllo Panel Windows Form o il controllo di Layout di griglia nella finestra di progettazione HTML. Se l'editor fornisce contenitori per altri oggetti grafici, il modello di selezione seguente deve essere utilizzato per solo il contenitore (oggetti all'interno di seguire il contenitore il modello standard come descritto in precedenza):  
  
|Input|Risultato|  
|-----------|------------|  
|Fare clic sul contenitore|Seleziona l'oggetto contenitore senza direttamente selezionare uno degli oggetti contenuti. Il contenitore può spostare e/o ridimensionato con standard del mouse e tastiera (come descritto in precedenza). Gli oggetti contenuti vengono spostati in relazione al contenitore, ma gli oggetti contenuti non vengono ridimensionati a meno che non vengono selezionati anche direttamente.|  
|Passare il mouse sull'area di confine del contenitore|Assume il cursore di spostamento, che indica che il contenitore è possibile spostare il puntatore del mouse.|  
|Trascinare l'area del bordo del contenitore|Cambia il mouse fino al cursore di spostamento e sposta il contenitore (e gli oggetti contenuti all'interno). Il contenitore non può essere spostato senza prima selezionato con un solo clic.|  
|Fare clic su un oggetto all'interno del contenitore|Deseleziona il contenitore (se selezionato) e seleziona solo l'oggetto selezionato.|  
|MAIUSC + clic o Ctrl + fare clic su un oggetto contenuto e/o contenitore|Aggiunge l'oggetto selezionato a un gruppo di selezione o la selezione esistente. Se l'oggetto selezionato è già un membro del gruppo di selezione, viene rimosso dal gruppo di selezione.|  
  
 Gli oggetti contenuti devono essere conforme al modello di base la selezione, come descritto nella sezione precedente. Da test di usabilità della finestra di progettazione Windows Form, gli utenti prevede l'accesso trasparente per gli oggetti contenuti senza effettuare dei passaggi coinvolti (imposti dall'oggetto contenuto).  
  
#### <a name="disjoint-and-region-selections"></a>Non contigue e selezioni di area  
 Editor oggetto grafico deve supportare le selezioni non contigui. Si noti che nel grafico non mostra l'aspetto di controllo per Visual Studio. Vedere [Aspetto Selezione oggetto grafico](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) di specifiche dettagliate visual.  
  
 ![Selettori di elementi non contigui e di aree](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")  
  
 **Selezione indipendente**  
  
 Editor grafico deve fornire anche le selezioni di area con un indicatore di selezione tipo di testo scorrevole. Se l'editor grafico supporta altri tipi di oggetto (ad esempio testo), quindi selezioni regione potrebbero non essere possibile in base ai vincoli di tali altri tipi di oggetto.  
  
 ![Selezione di testo scorrevole](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")  
  
 **Selezione di testo scorrevole**  
  
#### <a name="primary-and-secondary-selections"></a>Selezioni primari e secondari  
 Alcuni editor oggetto grafica consente all'utente di modifica o l'allineamento degli oggetti nei gruppi. In questo caso, il concetto di selezioni primarie e secondarie deve essere introdotto. La selezione primaria è l'oggetto a cui rispondono per le operazioni di gruppo tutti gli altri oggetti. L'oggetto che l'utente seleziona innanzitutto diventa il controllo principale e selezioni successive diventano le selezioni secondarie. La selezione primaria ha un trattamento visual distinto dalle selezioni secondarie per indicare quale oggetto è primario:  
  
 ![Selezione primaria e secondaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")  
  
 **Selezione primaria con due selezioni secondarie**  
  
####  <a name="a-namebkmkgraphicalobjectselectionappearancea-graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Aspetto di selezione di oggetti grafici  
 Quadratini di ridimensionamento sono quadratini disegnati in un modello rettangolare intorno alla casella di delimitazione dell'oggetto. Il grafico seguente mostra esempi dei vari stati che può disporre di un oggetto grafico con quadratino di ridimensionamento e aspetto modifica sul posto. Le dimensioni dei quadratini di ridimensionamento devono essere collegate al bordo della finestra e bordo metriche usando la **GetSystemMetrics** API.  
  
|Stato|Aspetto|Dettagli Visual|  
|-----------|----------------|--------------------|  
|**Non selezionato**|Impostazione predefinita|![Stato del pulsante predefinito](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState")||  
|**Selezione primaria**|Ridimensionabile|![Selezione primaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize")|![Selezione primaria con ridimensionare gli handle &#40; ingrandito &#41;](../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713-12_PrimaryResizeZoom")|  
|**Selezione primaria**|Non ridimensionabile|![Selezione primaria senza quadratini di ridimensionamento](~/extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize")|![Selezione primaria senza ridimensionare gli handle &#40; ingrandito &#41;](../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713-14_PrimaryNoResizeZoom")|  
|**Selezione primaria**|Bloccato|![Selezione primaria bloccata](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked")|![Selezione primaria bloccata &#40; ingrandito &#41;](../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713-16_PrimaryLockedZoom")|  
|**Selezione secondaria**|Ridimensionabile|![Selezione secondaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize")|![Selezione secondaria con ridimensionare gli handle &#40; ingrandito &#41;](~/extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713-18_SecondaryResizeZoom")|  
|**Selezione secondaria**|Non ridimensionabile|![Selezione secondaria senza quadratini di ridimensionamento](~/extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize")|![Selezione secondaria senza quadratini &#40; ingrandito &#41;](~/extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713-20_SecondaryNoResizeZoom")|  
|**Selezione secondaria**|Bloccato|![Selezione secondaria bloccata](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked")|![Selezione secondaria bloccata &#40; ingrandito &#41;](../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713-22_SecondaryLockedZoom")|  
|**Attivi dell'interfaccia Utente**|Impostazione predefinita|![Stato attivo dell'interfaccia utente](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive")|![Interfaccia Utente lo stato attivo &#40; ingrandito &#41;](../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713-24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Visualizzazione di modelli di selezione  
  
#### <a name="tree-view"></a>Visualizzazione albero  
 Selezione di una visualizzazione albero viene visualizzato con una semplice evidenziazione. Se l'utente fa clic sull'icona di un nodo o un nome di nodo, viene selezionato il nodo. Le icone triangolari a sinistra del nodo di espandere o il controllo struttura ad albero del contratto ma non influiscono sulla selezione dell'utente, con un'unica eccezione: dopo la compressione di un nodo padre quando la selezione si trova su un elemento figlio di tale nodo, la selezione si sposta al padre.  
  
 ![Visualizzazione albero tipica in Visual Studio](~/extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")  
  
 **Visualizzazione ad albero tipica in Visual Studio**  
  
 Visualizzazioni ad albero possono supportare selezioni contigue e non contigui, anche attraverso più livelli della struttura. Contigui o non contigui nei nodi dell'albero visibile è necessario effettuare più selezioni. Se un nodo è compresso, la selezione non contiguo viene persa e il nodo che era stato compresso Ottiene la selezione. In questo modo, l'utente può visualizzare i nodi che verranno influenzati da un'operazione. Quando i nodi vengono compressi, risulta chiaro quali nodi possono essere influenzati.  
  
 Quando si seleziona un nodo padre, applicare l'operazione per l'elemento padre, sebbene possano esistere casi in cui è utile per un'operazione da applicare al padre e i relativi figli. In questo caso, fornire aggiuntivi dell'interfaccia Utente durante l'operazione, ad esempio una casella di controllo o finestra di dialogo di conferma per rendere esplicito all'utente l'opzione "applicato a tutti i figli".  
  
##### <a name="renaming"></a>Ridenominazione  
 Nodi dell'albero supportano la ridenominazione, ridenominazione deve essere effettuata nella posizione. L'operazione sul posto deve essere lo standard per tutti i controlli struttura ad albero in Visual Studio. Specificare un comando rename che immediatamente attiva la modalità di modifica sul posto, con la selezione di testo che copre l'intero nome del nodo, pronto per accettare l'input dell'utente. Se il nodo rappresenta un file, il nome del file deve contenere l'estensione. La selezione evidenziata deve includere solo il corpo del nome file e non l'estensione.  
  
|Input|Risultato|  
|-----------|------------|  
|INVIO (tasto)|Esegue il commit dell'operazione di ridenominazione|  
|Tasto ESC|Annulla l'operazione di ridenominazione|  
|Facendo clic all'esterno dell'area di modifica sul posto|Esegue il commit dell'operazione di ridenominazione|  
|Annulla|Fornire facile Annulla per annullare l'operazione di ridenominazione|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Selezione all'interno di elenchi e i controlli griglia  
 Il concetto chiave nella selezione dell'elenco è che è basato su riga, il che significa che quando viene effettuata una selezione all'intera riga è selezionato come unità. Al contrario, le griglie consente di celle specifiche da selezionare senza influire sull'aspetto della riga. Griglie possono inoltre contenere una gerarchia di righe nidificate (ad esempio un TreeGrid) che consentono di intere diramazioni della gerarchia per essere selezionato e deselezionato interagendo con le righe padre. Negli elenchi di selezione è indicata da un colore di evidenziazione semplice per l'intera riga di dati. Lo stato attivo è indicato da un bordo punteggiato singolo pixel intorno alla riga modificabile corrente o di una cella (riga se tutte le celle sono di sola lettura).  
  
> [!NOTE]
>  **Lo stato attivo** e **selezione** sono due concetti diversi. *Lo stato attivo* indica quale dell'interfaccia Utente di elemento, viene indirizzato per ricevere l'input non esplicitamente indirizzati a un altro oggetto, mentre *selezione* fa riferimento allo stato di inclusione di un oggetto in un set di oggetti in cui le operazioni successive possono aver luogo.  
  
 Le selezioni negli elenchi possono essere contigui, non contigui, o area geografica. Quando selezioni multiple sono consentite, contigue e selezione indipendente deve sempre essere supportata, mentre il supporto per selezioni per l'area (casella) è facoltativo. Selezioni per l'area possono essere avviate mediante il trascinamento nello spazio vuoto del corpo dell'elenco.  
  
|Oggetto|Selezione|  
|------------|---------------|  
|Elenco|Contigue|Sempre supportate (se sono consentite più selezioni).|  
|Elenco|Non contigue|Sempre supportate (se sono consentite più selezioni).|  
|Elenco|Region|Supporto facoltativo. Avviato trascinando il puntatore del mouse nello spazio vuoto del corpo dell'elenco.|  
  
 Fare clic su una sola volta in un elenco selezionare la riga in cui si è verificato il clic. Se l'utente di fare clic su una cella di elenco che supporta la modifica sul posto, la cella viene attivata anche immediatamente per la modifica sul posto. In caso contrario, l'intera riga viene immediatamente selezionato e viene illustrata un'evidenziazione.  
  
 Trascinare nel corpo elenco esegue una delle tre operazioni:  
  
-   Avvia la selezione di una regione se l'elenco supporta l'elemento e il mouse verso il basso è lo spazio vuoto  
  
-   Se la cella dell'elenco o la riga supporta da un'origine di trascinamento avvia un'operazione di trascinamento  
  
-   Seleziona la riga corrente  
  
##### <a name="in-place-editing"></a>La modifica sul posto  
 Quando è consentita la modifica sul posto, sono disponibili due modelli di base: selezione proprietà e controllo di modifica semplice. Con un controllo di modifica semplice, il contenuto è evidenziato e pronto per l'input non appena viene attivata la modifica sul posto dell'utente. Dove è implementato un selettore di proprietà, il pulsante che richiama la selezione di proprietà viene visualizzato una volta attivata la modalità di modifica sul posto e la selezione corrente non è evidenziata. Il pulsante di selezione deve essere allineata a destra della cella. Per esempi di modifica sul posto, vedere il **finestra proprietà** e **elenco attività** in Visual Studio.  
  
##### <a name="keyboard-support"></a>Supporto della tastiera  
 Supporto di tastiera per la selezione in elenchi e griglie segue le convenzioni standard di Windows:  
  
-   Tasti di direzione spostarsi nell'elenco, selezionare ogni riga o cella, come lo stato attivo viene spostato.  
  
-   MAIUSC + freccia esegue una selezione contigua nella direzione dei tasti di direzione.  
  
-   CTRL + freccia seguita da attiva o disattiva la barra spaziatrice tra l'aggiunta e rimozione di elementi di elenco dalla selezione, creazione di una selezione non contiguo.  
  
-   Per le griglie contenenti le gerarchie annidate, il tasto freccia destra espande una riga padre e il tasto freccia sinistra comprime uno.  
  
-   Il tasto Tab sposta lo stato attivo tra le celle nella riga corrente, se le celle sono modificabili.  
  
-   Il tasto INVIO esegue il comando predefinito sull'elemento nell'elenco (spesso **aprire**).  
  
-   Il tasto F2 Attiva modifica sul posto per la cella attualmente selezionata.  
  
##  <a name="a-namebkmkpersistenceandsavingsettingsa-persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistenza e il salvataggio delle impostazioni  
  
### <a name="overview"></a>Panoramica  
 Anche se ogni componente software in Visual Studio è in genere responsabile per il proprio stato e la persistenza, Visual Studio Salva automaticamente le impostazioni in alcuni casi, ad esempio con le posizioni e dimensioni di finestra. Nella tabella seguente è una combinazione di impostazioni che richiedono un utente esplicito o programmato azione da intraprendere e le impostazioni salvate automaticamente.  
  
|Oggetto|Gli elementi da salvare|Quando Salva|Percorso di salvataggio|  
|------------|------------------|------------------|-------------------|  
|Oggetto selezionabile (ad esempio, una riga di codice)|Un punto di interruzione su una riga di codice<br /><br /> Un collegamento utente associato alla riga di codice|Quando il progetto venga salvato|Il **Opzioni utente (con estensione suo)** file per il progetto|  
|Finestra di dialogo|La posizione della finestra di dialogo, se è stato spostato<br /><br /> La visualizzazione che l'utente può essere utilizzato per ultimo nella finestra di dialogo|Quando si chiude la finestra di dialogo<br /><br /> Quando termina la sessione di Visual Studio|In memoria<br /><br /> Nel Registro di sistema **HKEY_Current_User**|  
|Finestra|Le dimensioni e la posizione della finestra|Quando la finestra viene chiusa<br /><br /> Quando cambia la modalità di Visual Studio<br /><br /> Quando termina la sessione di Visual Studio|Il **Opzioni utente (con estensione suo)** file per il progetto<br /><br /> File di opzioni personalizzate per le impostazioni della finestra|  
|Documento|La selezione corrente nel documento<br /><br /> La visualizzazione del documento<br /><br /> L'ultimo diverse posizioni visitato dall'utente|Quando il documento viene salvato|Il **Opzioni utente (con estensione suo)** file per il progetto|  
|Progetto|Riferimenti ai file<br /><br /> Riferimenti a directory su disco<br /><br /> Riferimenti ad altri software<br /><br /> Componenti<br /><br /> Informazioni sullo stato relative al progetto stesso|Quando il progetto venga salvato|Il file di progetto|  
|Soluzione|Riferimenti a progetti<br /><br /> Riferimenti ai file|Quando viene salvata il progetto o soluzione|Il **soluzione (sln)** file|  
|Le impostazioni in **Strumenti > Opzioni**|Personalizzazioni tastiera<br /><br /> Personalizzazioni barra degli strumenti<br /><br /> Combinazioni di colori|Quando il **Strumenti > Opzioni** finestra di dialogo viene chiusa<br /><br /> Quando termina la sessione di Visual Studio|Nel Registro di sistema **HKEY_Current_User**|  
  
 Ciò che l'utente sta eseguendo e quando si eseguono, determina se un'impostazione viene salvata in memoria (durante la sessione), salvata su disco (tra le sessioni come un'impostazione del Registro di sistema), come parte del file di progetto o soluzione stessa, come parte di **Opzioni di soluzione (con estensione suo)** file o le impostazioni personalizzate di un file che solo tale componente software è a conoscenza. Nella tabella precedente sono diversi eventi in cui è possono salvare le impostazioni. Tuttavia, esistono altri casi in cui si desidera salvare lo stato:  
  
-   Quando l'utente modifica posizione all'interno di una finestra o la finestra di dialogo  
  
-   Quando l'utente trasferisce lo stato attivo a un'altra finestra  
  
-   Quando l'utente passa dalla progettazione alla modalità di debug  
  
-   Quando l'utente si disconnette il proprio account  
  
-   Quando il computer entra in ibernazione o arrestato  
  
-   Quando il disco rigido/computer sta per essere riformattato e configurare di nuovo  
  
### <a name="window-configurations"></a>Configurazioni di finestre  
 Configurazione di una finestra è la presentazione di base dell'ambiente di sviluppo, è una combinazione costituita l'elenco di finestre degli strumenti presente e il modo in cui vengono disposti. Per windows gestiti dall'IDE (IDE windows), le informazioni di layout viene mantenute per ogni utente, quindi quando si avvia un utente dell'IDE, il layout della finestra viene visualizzato lo stesso come quando si ha terminato Visual Studio. Lo stato e posizione delle finestre IDE è persistente in un file di opzioni personalizzate in formato XML. Finestre degli strumenti che vengono create pacchetti caricati nell'IDE di rendere persistenti le informazioni sullo stato nel Registro di sistema e possono o non sia per ogni utente.  
  
#### <a name="profile-specific-layouts"></a>Layout per il profilo  
 Ogni profilo include layout di finestra dello strumento, organizzati in modo familiare agli utenti specifici degli sviluppatori (prevede che gli sviluppatori di Visual C++ visualizzare il **Esplora** sul lato sinistro dell'IDE, mentre gli sviluppatori c# dovrebbero essere presenti il **Esplora soluzioni** a destra). Layout di finestra per il profilo vengono caricati dopo che l'utente sceglie un profilo all'avvio. Autore di un pacchetto è necessario determinare il layout delle finestre più adatto per la loro esperienza, sapendo che le modifiche apportate dall'utente per la configurazione della finestra quindi vengono rese persistenti.  
  
##  <a name="a-namebkmktouchinputa-touch-input"></a><a name="BKMK_TouchInput"></a> Input tocco  
 Gli utenti stanno utilizzando prodotti di sviluppo Microsoft nei dispositivi touch. Tuttavia, esistono ostacoli che rendono difficile utilizzare gli strumenti di sviluppo dispositivi touch. Gli utenti si aspetta di ricevere i prodotti per fornire un'esperienza touch affidabile e precisa. Lo scopo di queste linee guida è informare decidere quali funzionalità di tocco per incorporare e per favorire un'esperienza touch coerente in Visual Studio e prodotti correlati.  
  
### <a name="levels-of-experience"></a>Livelli di esperienza  
 I seguenti livelli di esperienza servono a fungono da Guida per aiutare i team di decidere le funzionalità di tocco per offrire in base al relativo livello desiderato di interesse di investimento in contatto.  
  
-   Il **base** per i team che vogliono fornire touch funzionalità pertanto non vi sono strade in tutto il lavoro.  
  
-   Il **ottimizzato esperienza** è per i team che desidera funzionalità più comuni di tocco (ad esempio quelle disponibili in genere nelle applicazioni browser internet).  
  
-   Il **elevati esperienza** è per i team che desidera aggiungere funzionalità di questo tipo di azioni o altre funzionalità facoltative che rendono le applicazioni a primo tocco descrittivo.  
  
||Esperienza di base|Esperienza ottimizzata|Esperienza con privilegi elevato|  
|-|----------------------|--------------------------|-------------------------|  
|Consente agli utenti di...|Correzione di codice e soluzione o progetto del livello di lettura senza strade|Eseguire attività di manutenzione, refactoring ed esplorazione|Operare in un'esperienza coerenza, intuitiva e fluida con certezza|  
|Editor|Selezione e la panoramica tocco<br /><br /> Barra di scorrimento touch per passare e premere + trascinamento|Zoom indietro avanti<br /><br /> Scorrimento veloce<br /><br /> Selezione<br /><br /> Semplice utilizzo dei menu di scelta rapida||  
|Finestre degli strumenti superiore|Panoramica di elenco<br /><br /> Selezione di elementi<br /><br /> Barra di scorrimento touch per passare e premere + trascinamento|Selezione e lo scorrimento di un elemento semplice||  
|Windowing||Ridimensiona finestra<br /><br /> Barra di accesso rapido||  
|Documento e||Semplificare la navigazione tra i file aperti||  
|Movimenti||Assicurare il funzionano dei movimenti comuni all'interno dell'IDE|Azioni basate sui movimenti<br /><br /> Il supporto di trascinamento e rilascio e finestre di progettazione|  
|Altre considerazioni|||Tastiera su schermo personalizzata|  
  
#### <a name="gestures"></a>Movimenti  
 I movimenti di forniscono agli utenti un scelta rapida ai comandi che richiedono un'interazione più complicata. Fare riferimento alle linee guida di Windows in [i movimenti di tocco comune per le applicazioni Desktop](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx), e attenersi alle istruzioni per la maggior parte dei movimenti, inclusi i movimenti, ad esempio la panoramica e zoom.