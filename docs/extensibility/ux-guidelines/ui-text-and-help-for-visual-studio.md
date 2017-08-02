---
title: "Testo dell&#39;interfaccia utente e la Guida di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Testo dell&#39;interfaccia utente e la Guida di Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_UITextAndTerminology"></a> Testo dell'interfaccia utente e la terminologia  
 Testo comprensibile è fondamentale per efficace interfaccia utente. Gli utenti di software tendono a leggere le etichette in primo luogo, vale a dire quelli più rilevanti per il completamento dell'attività in questione. Testo statico viene letto con minore frequenza. Piano per gli utenti di avviare le sessioni di lavoro con un'analisi rapida della finestra intera, seguita da una lettura dell'interfaccia utente in questo ordine approssimativo:  
  
1.  Controlli interattivi al centro  
  
2.  Eseguire il commit di pulsanti  
  
3.  Controlli interattivi trovati altrove  
  
4.  Istruzioni principali  
  
5.  Spiegazioni aggiuntive  
  
6.  Titolo della finestra  
  
7.  Altro testo statico nel corpo principale  
  
### Modelli di utilizzo per il testo dell'interfaccia utente  
  
#### Testo della barra del titolo  
 Testo della barra del titolo deve corrispondere il comando che ha generato l'interfaccia utente.  
  
#### Testo esplicativo \(testo di supporto\)  
 In alcune finestre di dialogo, è utile fornire importanti istruzioni principale per spiegare come procedere nella finestra o nella pagina. Ciò è talvolta detta "testo di supporto".  
  
##### Scrittura di regole di stile per il testo di supporto  
  
-   Non vengono spiegati gli evidenti. A meno che non sia assolutamente necessario, non includere testo esplicativo.  
  
-   Testo esplicativo è sempre posizionato nella parte superiore della finestra di dialogo e fare riferimento all'attività in corso.  
  
-   Precisamente spiegare agli utenti è necessaria una. Evitare la ridondanza e comunicazione eccessivo.  
  
-   Esaminare ogni finestra ed eliminare le istruzioni e le parole duplicate.  
  
-   Mantenere breve del testo esplicativo. Se altre informazioni necessarie per alcuni utenti o gli scenari, quindi fornire un collegamento a un argomento online concettuale dettagliato.  
  
-   Scrivere il testo in modo che ogni parola contiene peso e non è necessario.  
  
-   Seguire le indicazioni di Microsoft esistenti per [il testo dell'interfaccia utente](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [lo stile e il segnale](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### Istruzioni aggiuntive  
 Istruzioni aggiuntive forniscono informazioni aggiuntive che consente all'utente informazioni sui controlli o raggruppamenti di controllo. Questo può anche includere testo di suggerimento necessario per comprendere il formato è previsto il controllo di input. Utilizzare le istruzioni aggiuntive con moderazione. Riservarli per i casi in cui è probabile che l'utente non sarà completamente comprendere le implicazioni di si tratta di una scelta.  
  
 ![Supplemental text in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601\-b\_SupplementalText1")  
  
 **Testo supplementare in Visual Studio**  
  
 ![Supplemental text in Visual Studio](~/docs/extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601\-c\_SupplementalText2")  
  
 **Testo supplementare in Visual Studio**  
  
#### Infotip  
 Spesso, il testo esplicativo potrebbe risultare troppo lungo per posizionare sul posto nell'interfaccia utente o potrebbe essere utile solo per i nuovi utenti, ad esempio disordine agli utenti esperti di questa. In questo caso, è consigliabile inserire testo esplicativo informativo o come descrizione comando in una finestra popup.  
  
 Infotip devono essere posizionati in prossimità di controlli correlati e devono usare l'icona della finestra popup specifico, che è discreto evidenti.  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **Esempio di una finestra popup in Visual Studio**  
  
##### Regole di stile di scrittura per Infotip  
  
-   Scrivere Infotip come frasi intere. Richiedono verbi specifici, normale e la punteggiatura finale.  
  
-   Utilizzare Infotip per completare l'istruzione principale o informazioni. Se si utilizza soltanto parole diverse per ridefinire l'idea principale, non è necessario una finestra popup.  
  
-   Mantenere breve e semplice Infotip. Utilizzare parole piccole e semplice, il linguaggio naturale che supporta e incoraggia l'utente.  
  
-   Seguire le indicazioni di Microsoft esistenti per [il testo dell'interfaccia utente](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [lo stile e il segnale](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### Etichette del controllo  
 Etichette del controllo devono essere brevi e concisi e seguire il [linee guida per il Desktop di Windows per i controlli](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Per ulteriori informazioni sulla posizione all'interno dell'interfaccia utente e controllo del formato etichetta, vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### Collegamenti della Guida  
 I collegamenti della Guida possono essere posizionati all'interno del testo esplicativo o nel corpo dell'interfaccia utente. Possono essere forniti collegamenti alla Guida in linea o avviare conversazioni interne.  
  
##### Regole di stile di visualizzazione per i collegamenti della Guida  
  
-   Utilizzare i colori ambiente corretto per i collegamenti ipertestuali. Un collegamento ipertestuale correttamente con stile non lampeggia brevemente rosso quando si fa clic. Se questo è visualizzato, è un'indicazione che non vengono utilizzati i colori di ambiente.  
  
-   Le sottolineature ondulate devono essere utilizzate solo al passaggio del mouse o quando il collegamento viene incorporato in un paragrafo.  
  
-   Per ulteriori informazioni sugli stili visivi e interazione dei collegamenti ipertestuali, vedere i collegamenti ipertestuali e pulsanti.  
  
##### Scrittura di regole di stile per i collegamenti della Guida  
  
-   Quando si avvia le finestre di dialogo, mantenere gli standard per i puntini di sospensione: senza i puntini di sospensione per lo spostamento, quindi sui puntini di sospensione se l'attività richiede aggiuntivi dell'interfaccia utente.  
  
     ![Help link in Visual Studio](~/docs/extensibility/ux-guidelines/media/0601-e_helplink.png "0601\-e\_HelpLink")  
  
     **Puntini di sospensione \(...\) nella Guida di una collegamento indica che l'attività sarà necessario aggiuntivi dell'interfaccia utente.**  
  
-   I collegamenti non possono iniziare con "Informazioni", poiché non è l'obiettivo dell'utente. L'utente desidera rispondere a una domanda specifica, non riceve una formazione generale.  
  
-   Guida di frase i collegamenti in modo che chiedono che l'argomento verrà data risposta alla domanda.  
  
     Non corretto:  
     "Ulteriori informazioni sui prezzi di servizi mobili di Azure"  
  
     Correggere:  
     "Le opzioni relative ai prezzi sono disponibili per servizi mobili di Azure"?  
  
-   Non utilizzare mai *fare clic su...* per il testo del collegamento.  
  
-   Non collegare solo la parola "qui". Questo rappresenta un problema per alcuni lettori di schermo, che verranno vocale solo la parola con collegamento ipertestuale.  
  
     Non corretto:  
     "Informazioni su servizi mobili di Azure **qui**"  
  
     Correggere:  
     "Le opzioni relative ai prezzi sono disponibili per servizi mobili di Azure"?  
  
-   Per ulteriori informazioni sullo stile di scrittura corretti per i collegamenti della Guida, vedere il [linee guida per Desktop di Windows per la Guida](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### Testo di suggerimento  
 Testo di suggerimento viene visualizzato come filigrana all'interno di un controllo o sotto il controllo. La formattazione corretta verrà applicata utilizzando il token VSColors appropriato, `Environment.GrayText`.  
  
 Può essere visualizzato in una serie di moduli.  
  
-   Al posto di etichetta del controllo:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601\-f\_HintText1")  
  
-   Con un verbo, fornendo istruzioni:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601\-g\_HintText2")  
  
-   Con il testo che indica una voce obbligatoria:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601\-h\_HintText3")  
  
#### Testo della filigrana  
 In un'area di progettazione vuota, il testo deve indicare le operazioni da eseguire, nonché fornire collegamenti per aprire altre finestre correlate, se appropriato:  
  
 ![Watermark text in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601\-i\_WatermarkText")  
  
 **Esempio di testo della filigrana in Visual Studio**  
  
### Terminologia comune  
  
|Termine|Descrizione|Commento|  
|-------------|-----------------|--------------|  
|Accedi \/ Esci|Verbi utilizzati come sinonimi con il web per la rappresentazione di autenticazione in una proprietà di web. All'interno di client, utilizziamo questa volta come una nozione di livello superiore per la firma o disattivare la connessione utente IDE, che rappresenta un'identità di livello superiore che fornisce funzionalità di livello superiore, ad esempio roaming e le licenze che non sono disponibili in tutte le altre connessioni.|L'utente IDE è l'unica funzionalità che deve rappresentare una richiesta di accesso \/ Disconnetti verbo, in quanto rappresenta l'utente IDE principale.|  
|Connessione \/ disconnessione|Utilizzare in posizioni in cui una funzionalità mantiene una singola connessione a un servizio online.|Esplora server, in cui si può avere solo una connessione di Azure attiva alla volta, è riportato un esempio di connessione\/disconnessione.|  
|Aggiungere o rimuovere|Non distruttiva. Utilizzo durante l'aggiunta o rimozione di un elemento da un elenco.|Finestra di dialogo Elenco server TFS Connection Manager è un esempio di installazione.|  
|Delete|Distruttiva. Utilizzare solo quando l'elemento viene rimosso verrà definitivamente eliminato o cancellato dal disco.|"Delete" è in genere richiede un prompt dei comandi se il risultato è l'eliminazione di un file dal disco.|  
  
## Messaggi di errore  
  
### Panoramica  
 Si verificano errori. L'impostazione di limitazioni sulle operazioni che l'utente può eseguire è un primo passo per prevenire i messaggi di errore evitabile intelligente. Tuttavia, quando si verifica un errore, un messaggio di errore ben scritta passare in modo limitare il problema. Messaggi di errore rappresentano probabilmente uno dei principali tipi di notifica all'utente che, in quanto sono sincroni e indicare un problema che deve essere risolto. Messaggi di errore mal lasciano gli utenti in propri per stabilire la causa degli errori e le possibili soluzioni.  
  
 Gli utenti potrebbero smettere di prestando attenzione a eccessivo o confusione tra i messaggi di errore, per consentire messaggi scrittura necessario solo aggiungere valore all'utente. Se il messaggio è semplicemente una notifica, utilizzare una presentazione alternativa.  
  
### Regole per la creazione di un messaggio di errore  
  
-   Durante la costruzione di messaggi di errore, scegliere il livello di errore appropriato per il gruppo di destinatari. L'obiettivo per le trame semplice che forniscono un'azione che può richiedere all'utente, se applicabile. Non tutto ciò che l'utente non è necessario conoscere lo stato.  
  
-   Fornire assistenza costruttivo. È facile da leggere e agire su un messaggio di errore contenente l'istruzione.  
  
-   Non usare doppia negativi.  
  
-   Eseguire sia un processo automatico e manuale grammatica e ortografia controllare nei messaggi di errore che scrittura.  
  
-   Per i messaggi di errore complesse, evitare di comunicazioni sequenziale. Non utilizzare mai un aggancio F1 per il messaggio di errore. Il messaggio stesso dovrebbe essere sufficiente.  
  
-   Utilizzare l'icona corretta.  
  
-   Rendere domande facile da comprendere e utilizzare i pulsanti con scelte non crittografate, ad esempio "Delete" e "Annulla".  
  
-   Per gli avvisi, essere chiaramente quali saranno le conseguenze di procedere. I pulsanti devono indicare la conseguenza.  
  
-   Per gli errori, viene descritto ciò che gli utenti possono eseguire per risolvere il problema. I pulsanti da azioni o pronunciare "Chiudi". Non utilizzare un pulsante "OK" per un messaggio di errore.  
  
-   Alcune delle domande da porsi durante la costruzione di un messaggio di errore:  
  
    -   L'utente può scoprire come risolvere il problema con questo errore solo?  
  
    -   L'utente utilizza il vocabolario stesso a questo errore?  
  
    -   È questo ambigua errore o condiviso in diverse situazioni? In questo caso, come guidare gli utenti per la soluzione che più?  
  
#### Errori di compilazione  
 Poiché Visual Studio è uno strumento di sviluppo software, molti dei suoi componenti dispongono di una compilazione, la conversione o la codifica di passaggio per convertire il lavoro degli sviluppatori in formato binario. Queste conversioni possono causare errori quando il compilatore non può elaborare i file creati in modo non corretto o quando le opzioni del compilatore non sono state impostate correttamente.  
  
 Gli utenti di Visual Studio è possono dedicare un numero elevato di ore di sviluppo per la risoluzione degli errori di compilazione. Il tempo di risoluzione aumenta quando gli errori presentano dipendenze o quando i messaggi di errore vengono ridotte scritti, che può rendere difficile scoprire l'origine dell'errore.  
  
 Gli errori di compilazione migliore sono quelli che non si verificano in primo luogo, motivo per cui Visual Studio fornisce il completamento automatico IntelliSense zigzag. Convalida dello schema e strumenti simili offrono lo stesso tipo di commenti e suggerimenti. Questi meccanismi di guidano in modo proattivo l'utente per creare il codice corretto, riducendo la probabilità di errori di compilazione.  
  
 Visual Studio fornisce una finestra degli strumenti in cui gli utenti possono leggere e spostarsi tra gli errori verificatisi nella finestra del documento. Tasti di scelta rapida sono disponibili in modo che l'utente può rapidamente passare grandi quantità di codice e passare direttamente alla posizione del problema. Visual Studio consente inoltre di ogni errore di compilazione a un particolare ID parola chiave\/contesto della Guida in modo che l'utente può accedere direttamente a un argomento della Guida che fornisce informazioni più dettagliate sull'errore.  
  
 Scrivere gli errori di compilazione chiara e concisa:  
  
-   **Utilizzare un linguaggio semplice** che descrive il problema con pochissime gergo del compilatore. Il testo di un errore di compilazione non dovrebbe risultare eccessivamente tecnico.  
  
-   **Descrive le possibili cause.** Ad esempio, "manca un virgola tra proprietà e il valore nel ' \(proprietà\): \(valore\)' dichiarazione."  
  
-   Fornire dettagli sulle potenziali correzioni. Se non c'è spazio sufficiente, dettagli aggiuntivi possono essere messi nell'argomento della Guida corrispondente.  
  
### Componenti di un messaggio di errore ben scritta  
  
#### Utilizzare il servizio di finestra di dialogo della shell per i messaggi di errore.  
 Tramite il servizio di finestra di dialogo shell consente di controllare l'aspetto del messaggio, in particolare i tipi di carattere, ovvero senza principali modifiche apportate a singoli elementi. Utilizzare il **IErrorInfo** meccanismi e segnalarli utilizzando **IVsUIShell::SetErrorInfo\/ReportErrorInfo**.  
  
#### Scegliere una presentazione efficace e appropriato di notifica.  
 Utilizzare una finestra di dialogo modale con un avviso critico se è necessario un intervento immediato per evitare la perdita di dati \(la notifica sincrona\). Icone critiche sono riservate per le situazioni in cui la chiusura del messaggio senza lettura può generare conseguenze negative. Perdita di dati è una situazione critica che richiede un intervento a livello di avviso. Utilizzo eccessivo di icona critico desensitizes agli utenti di importanza. Se il messaggio di errore è di natura informativa, prendere in considerazione alternative per una finestra di dialogo modale \(notifica asincrona\).  
  
#### Viene fornita una spiegazione chiara e concisa del motivo per cui si è verificato il problema piuttosto che una spiegazione.  
 Sovraccaricare gli utenti con dettagli tecnici nella spiegazione relativa renderà più probabile ignorare i messaggi di errore. Esempi di buone messaggistica:  
  
-   "Impossibile aprire il file richiesto."  
  
-   "Impossibile connettersi a Internet".  
  
#### Fornire informazioni su come risolvere il problema.  
 Utente suggerimenti su come risolvere il problema. Se non sono disponibili suggerimenti, essere onesti con l'utente. Fornire collegamenti diretti a origini online alternative, ad esempio il supporto tecnico o il supporto della community. Provare a indirizzare gli utenti a specifiche informazioni online relative al problema. Per un ID di errore, prendere in considerazione la connessione degli utenti a un thread di discussione sull'errore specifico. Esempi di buone messaggistica:  
  
-   "Assicurarsi che si è connessi a Internet e riprovare l'operazione."  
  
-   "Assicurarsi che il file esista e di disporre delle autorizzazioni per aprirlo."  
  
#### Scrivere un messaggio breve e al punto.  
 Può notificare un messaggio di errore, descrivere e offrono una soluzione ma comunque essere ignorato se è troppo prolisso. Una soluzione consiste nell'utilizzare la progressiva diffusione con il pulsante Dettagli. Ad esempio, fornisce una breve descrizione o la stessa soluzione e quindi inserire ulteriori dettagli sotto il pulsante Dettagli. Se si sceglie di leggere ulteriori informazioni sull'errore, è possibile farlo.  
  
 La lingua del messaggio deve essere:  
  
-   **Dominio appropriato.** Utilizzare l'utente sarà in grado di linguaggio. Anche se i clienti sono sviluppatori, spesso non dispongono del contesto e la terminologia che è disponibile.  
  
-   **Specifico.** Evitare di formulazione vaga e assegnare nomi specifici e i percorsi degli oggetti coinvolti. Ad esempio, un messaggio di errore come "carattere non valido" non è utile. Il carattere? "File non trovato". Il file?  
  
-   **Utile.** Non almeno l'utente o farli sentire stupido. Evitare di linguaggio offensivo o ostile \(kill, esecuzione, terminare, irreversibile, non valida\). Evitare di testo in maiuscolo, che viene spesso visualizzato come shouting e non è leggibile come. Non usare humor.  
  
-   **Correggere.** Utilizzare la grammatica e ortografia corretta \(anche in alfa\). Errori di battitura sono disorganizzato e imbarazzante.  
  
-   **In base al contesto appropriato.** Utilizzare il testo del pulsante appropriato. Evitare il pulsante "OK" e utilizzare "Continue" o "Sì\/No."  
  
### Esempi di messaggi di errore  
  
|Good|Non valido|  
|----------|----------------|  
|"Il numero composto non è più nel servizio. Controllare il numero e Riprova o comporre 0 per l'operatore."|-   "Errore \(449\): numero non valido"<br />-   "L'errore di eccezione non gestita indica che l'operazione completata".<br /><br /> ![Bad error message in Visual Studio](~/docs/extensibility/ux-guidelines/media/0602-a_errordialog.png "0602\-a\_ErrorDialog")|  
  
## L'accesso alla Guida  
  
### Panoramica  
 Oltre alla documentazione di MSDN, un utente di Visual Studio include diversi punti di accesso per assistere l'utente mentre nell'interfaccia utente. Per garantire che i punti di accesso disponibili in modo coerente, i team di funzionalità necessario sfruttare la Guida in linea offerti dall'ambiente. I punti di accesso sono:  
  
-   **Testo esplicativo e aggiuntivo nelle finestre di dialogo.** Testo statico che consente di direzione o una spiegazione, sia nell'interfaccia utente disponibile al passaggio del mouse sull'icona finestra popup o area.  
  
-   **F1 Guida in linea** \(solo editor\). All'interno dell'editor di Visual Studio, un utente può considerare attendibili che in qualsiasi momento, se si preme F1 verrà visualizzato un argomento della Guida specifiche per la selezione corrente. Assicurarsi che gli argomenti associati F1 siano appropriate e informativi.  
  
-   **Collegamenti ipertestuali agli argomenti della Guida.** Un collegamento ipertestuale all'interno di una finestra di dialogo, finestra degli strumenti o area di progettazione che avvia un argomento per assistere l'utente ulteriori informazioni su una tecnologia, funzionalità o informazioni su come eseguire un'attività.  
  
-   **Meccanismi dell'interfaccia utente di supporto, ad esempio gli smart tag e le finestre di dialogo di creazione.** Questi meccanismi di assistere l'utente per la comprensione di un elemento dell'interfaccia utente, o facilitano un'attività, ad esempio smart tag o finestre di dialogo Generatore.  
  
-   **Pulsanti della Guida dell'interfaccia utente** \(obsoleto\). Un indicatore visibile nella barra del titolo che fornisce l'accesso per l'argomento della Guida F1 correlato.  
  
### Testo  
  
#### Testo esplicativo e aggiuntivo nelle finestre di dialogo  
 Nelle finestre di dialogo che supportano attività complesse, potrebbe essere necessario fornire istruzioni all'interno dell'interfaccia utente, spesso nella parte superiore della finestra di dialogo o quasi controlli complessi. Vedere [Testo dell'interfaccia utente e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) per informazioni dettagliate sulla scrittura di stile.  
  
#### Infotip  
 Testo esplicativo spesso, potrebbe essere troppo lungo per collocare nella posizione desiderata nell'interfaccia utente o potrebbe essere utile solo per i nuovi utenti, ad esempio disordine agli utenti esperti di questa. In questo caso, è consigliabile inserire testo esplicativo informativo o come descrizione comando in una finestra popup.  
  
 Infotip devono essere posizionati in prossimità di controlli correlati e devono usare l'icona della finestra popup specifico, che è discreto evidenti.  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **Esempio di una finestra popup in Visual Studio**  
  
### Meccanismi di Guida interattive  
  
#### F1 Guida  
 F1 Guida in linea è necessario all'interno di un editor o nell'area di progettazione, ma non altrove nell'ambiente di Visual Studio.  
  
#### Collegamenti ipertestuali agli argomenti della Guida  
 Collegamenti ipertestuali possono essere utilizzati per eseguire un'azione, spostarsi all'interno dell'IDE oppure avviare la Guida in un browser. Vedere [Testo dell'interfaccia utente e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) per informazioni sul linguaggio e 07.10.01 pulsanti e collegamenti ipertestuali per le linee guida visual e layout.  
  
#### Pulsanti \[?\] nella finestra di dialogo barre del titolo \(obsolete\)?  
 Nella maggior parte, i pulsanti della Guida \[?\] nella barra del titolo delle finestre di dialogo sono deprecati. Argomenti dell'interfaccia utente non fanno più parte del modello doc e potrebbe pertanto non essere presente un argomento pertinente a cui collegarsi. In pratica, il pulsante della barra del titolo è lo stesso risultato F1 Guida in linea e che non è più necessario nelle finestre di dialogo. In alcuni casi, comunque utilizzabile come un indicatore che vi sono altre informazioni procedurale o concettuali disponibili, anche se i collegamenti ipertestuali vengono più frequentemente utilizzati nell'interfaccia utente più recente.  
  
##### Finestre di dialogo create tramite l'ambiente  
 Molte finestre di dialogo della shell vengono creati tramite il **VBDialogBoxParam** \(funzione\). Questa funzione condivisa è stata aggiornata per facilitare lo spostamento di **Guida** pulsante nella finestra di dialogo per la **?** pulsante mantenendo un'architettura con le versioni precedenti compatibile ed estensibile.  
  
 In particolare, il **VBDialogBoxParam** funzione esamina il modello di finestra di dialogo per un pulsante il cui ID è **IDHELP** \(9\) o un'etichetta **Guida** o **& Guida**. Se viene trovato un pulsante della Guida in linea, è nascosta e **WS\_EX\_CONTEXTHELP** stile viene aggiunta alla finestra di dialogo, inserisce il **?** pulsante nella barra del titolo della finestra di dialogo.  
  
 Quando viene creata la finestra di dialogo, inserisce la procedura di finestra di dialogo in uno stack e richiama la finestra di dialogo con una procedura di finestra di dialogo pre\-elaborazione denominato **DialogPreProc**. Quando il **?** si fa clic sul pulsante, viene inviato un **messaggio WM\_SYSCOMMAND** di **SC\_CONTEXTHELP** alla finestra di dialogo. Il **DialogPreProc** questo comando acquisisce e le modifiche a un **WM\_HELP** messaggio, che viene passato per il processo di finestra di dialogo originale  
  
 La maggior parte delle finestre di dialogo Creazione ambiente dispone di un pulsante della Guida nella finestra di dialogo. Quando viene visualizzata la finestra di dialogo, il pulsante Guida è nascosta automaticamente e solo il **?** pulsante funziona. Se il **?** pulsante mai rimosse o modificato in Windows, questa soluzione consente di passare rapidamente ai pulsanti della Guida in linea.  
  
 Questa soluzione quattro presupposti che potrebbero causare errori:  
  
-   Pulsante della Guida della finestra di dialogo è **IDHELP** \(9\).  
  
-   La finestra di dialogo l'aspetto corretto quando il pulsante Guida è nascosto.  
  
-   La finestra di dialogo non sostituisce la winproc.  
  
-   La finestra di dialogo non viene incorporato all'interno di un'altra finestra di dialogo.  
  
 Se la finestra di dialogo si trova all'interno di msenv e non usa **VBDialogBoxParam**, provare a utilizzare sfruttando **VBDialogBoxParam** prima di implementare un gestore personalizzato.  
  
##### Finestre di dialogo create tramite altri pacchetti  
 È possibile implementare una soluzione personalizzata per i dialoghi che risiedono all'esterno di msenv. Per una classe finestra di dialogo condiviso il VSPackage, provare a spostare il pulsante della barra del titolo o implementa un gestore in ciascuna finestra. Il codice seguente è una struttura di un'implementazione che consentono di iniziare:  
  
```  
struct DLGPROCITEM { FARPROC proc; // The info used to create the dialog. DLGPROCITEM* procPrev; }; DLGPROCITEM* g_dlgProcStack = NULL; // A dialog starter/wrapper function is used to push the new // dialog proc to the top of our dialog proc stack. int SomeDialogStarterFunction(hinst, id, proc, etc) { if (g_dlgProcStack == NULL) { g_dlgProcStack = new DLGPROCITEM; g_dlgProcStack->procPrev = NULL; } else { DLGPROCITEM* procItem = new DLGPROCITEM; g_dlgProcStack->procPrev = g_dlgProcStack; g_dlgProcStack = procItem; } } // Pop this dialog proc off the dialog proc stack. DialogBoxIndirectParam...(...) { DLGPROCITEM* procItem = g_dlgProcStack->procPrev; delete g_dlgProcStack; g_dlgProcStack = procItem; } // A wrapper dialog procedure will allow us to capture the // SC_CONTEXTHELP button on the title bar from Windows and // forward it as a simple WM_HELP message back to the dialog. INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg, WPARAM wParam, LPARAM lParam) { if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP) { uMsg = WM_HELP; wParam = 0; lParam = 0; } return CallWindowProc((WNDPROC)g_dlgProcStack->proc, hwndDlg, uMsg, wParam, lParam); }  
```  
  
##### Pulsanti della Guida nel codice gestito  
 Override del comportamento predefinito di finestra titolo barra della Guida in linea del pulsante è facile da codice gestito. Di seguito è un'applicazione di dimostrazione completo che illustra questo comportamento. In pratica, è necessario eseguire l'override del form **WndProc** metodo e quindi attivare la Guida F1 quando richiede un **SC\_CONTEXTHELP** messaggio viene intercettato.  
  
```  
using System; using System.Windows.Forms; public class HelpForm : Form { private const int SC_CONTEXTHELP = 0xF180; private const int WM_SYSCOMMAND = 0x0112; public HelpForm() { this.ClientSize = new System.Drawing.Size(300, 250); this.HelpButton = true; this.MaximizeBox = false; this.MinimizeBox = false; this.Name = "HelpForm"; this.Text = "Help Form"; } protected override void WndProc(ref Message m) { if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam) ShowHelp(); else base.WndProc(ref m); } private void ShowHelp() { MessageBox.Show("F1 Help goes here."); } [STAThread] static void Main() { Application.EnableVisualStyles(); Application.EnableRTLMirroring(); Application.Run(new HelpForm()); } }  
```  
  
## Vedere anche  
 [I tipi di carattere e la formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Le notifiche e l'avanzamento di Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)