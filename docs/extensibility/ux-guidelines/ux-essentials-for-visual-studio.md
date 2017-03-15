---
title: Essentials UX per Visual Studio | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7f10e2cefc0986a2457cc61945a60acfd1a4ef78
ms.lasthandoff: 02/22/2017

---
# <a name="ux-essentials-for-visual-studio"></a>Essentials UX per Visual Studio
## <a name="best-practices"></a>Procedure consigliate  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Garantire la coerenza all'interno dell'ambiente di Visual Studio.  
  
-   Seguire i modelli di interazione esistenti all'interno della shell.  
  
-   Funzionalità siano coerenti con requisiti di lingua e abilità visual della shell di progettazione.  
  
-   Utilizzo dei controlli e i comandi condivisi quando esistono.  
  
-   Comprendere la gerarchia di Visual Studio e come stabilisce contesto e l'interfaccia utente delle unità.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Utilizzare il servizio di ambiente per i tipi di carattere e colori.  
  
-   Interfaccia utente deve rispettare l'impostazione tipo di carattere ambiente corrente, a meno che non è esposto per la personalizzazione nella pagina tipi di carattere e colori nella finestra di dialogo Opzioni.  
  
-   Elementi dell'interfaccia utente devono utilizzare il VSColor Service, utilizzando token ambiente condiviso o specifiche funzionalità.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Rendere coerente con il nuovo stile di Visual Studio tutte le immagini.  
  
-   Seguire i principi di progettazione di Visual Studio per le icone, icone e altri elementi grafici.  
  
-   Non inserire testo in elementi grafici.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Struttura da una prospettiva incentrata sull'utente.  
  
-   Creare il flusso di attività prima le singole funzionalità all'interno di esso.  
  
-   Acquisire familiarità con gli utenti e rendono le informazioni esplicita nella specifica.  
  
-   Quando si esaminano l'interfaccia utente, valutare l'esperienza completa, nonché i dettagli.  
  
-   Progettare l'interfaccia utente in modo che rimanga funzionale e accurato indipendentemente dal linguaggio o delle impostazioni locali.  
  
## <a name="screen-resolution"></a>Risoluzione dello schermo  
  
### <a name="minimum-resolution"></a>Risoluzione minima  
 La risoluzione minima per Visual Studio Dev14 è 1280 x 1024. Ciò significa che è *possibili* a utilizzare Visual Studio questa risoluzione, sebbene non sia un'esperienza utente ottimale. Non è garantito che tutti gli aspetti sarà utilizzabili risoluzioni inferiori a 1280 x 1024.  
  
 Dimensioni di finestra di dialogo iniziale non devono superare 1000 pixel in altezza, in modo da adattarsi all'interno del frame dell'IDE all'interno di questa risoluzione minima 96 DPI.  
  
### <a name="high-density-displays"></a>Display ad alta densità  
 Interfaccia utente in Visual Studio deve funzionano bene in tutti i DPI che Windows supporto di fattori di scala: 150%, 200% e % 250.  
  
## <a name="anti-patterns"></a>Anti-modelli  
 Visual Studio contiene molti esempi di interfaccia utente che il nostro linee guida e procedure consigliate. Allo scopo di essere coerente, gli sviluppatori spesso prestito da modelli di progettazione dell'interfaccia utente del prodotto simile a ciò che sta creando. Si tratta di un buon approccio che consente di noi maggiore coerenza nella progettazione e l'interazione dell'utente, in alcuni casi fornite funzionalità con alcuni dettagli che non soddisfano nostre linee guida a causa dei vincoli di pianificazione o l'esclusione di assegnazione delle priorità. In questi casi, i team di copiare uno di questi "anti-pattern" non è desiderabile perché essi proliferare dell'interfaccia utente non valido o non coerente nell'ambiente di Visual Studio.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>I campi o le impostazioni necessarie in stato di errore visualizzate per impostazione predefinita  
  
#### <a name="feature-team-goals"></a>Funzionalità degli obiettivi del team  
  
-   Avvisare gli utenti che siano aggiunti un elemento che deve essere configurato.  
  
-   Attirare l'attenzione dell'utente per le aree che richiedono l'input.  
  
#### <a name="anti-pattern-solution"></a>Anti-pattern della soluzione  
 Non appena l'utente ha avviato un'azione e prima che l'attività è stata completata, posizionare immediatamente arresto critico icone accanto le aree che richiedono una configurazione.  
  
#### <a name="example-manifest-designer-declarations"></a>Esempio: Le dichiarazioni di progettazione del manifesto  
 Aggiunta di una dichiarazione all'elenco immediatamente colloca in uno stato di errore, viene mantenuto finché l'utente imposta le proprietà necessarie.  
  
 In questo caso, esiste un problema aggiuntivo perché l'icona utilizzata per l'avviso contiene una "x", rimuovere comuni in modo non è possibile utilizzare icona accanto a esso. Di conseguenza, l'interfaccia utente utilizza un pulsante Rimuovi, un controllo più difficili.  
  
 ![Manifesto errore anti-pattern della dichiarazione progettazione](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-modello")  
  
 **Inserimento dell'interfaccia utente in uno stato di errore per impostazione predefinita è un anti-modello di Visual Studio.**  
  
#### <a name="alternatives"></a>Alternative  
 Una soluzione migliore a questo problema, è possibile:  
  
-   Consentire all'utente di aggiungere una dichiarazione senza avviso e quindi spostare immediatamente impostare le proprietà dell'elemento.  
  
-   Aggiungere l'icona di avviso (triangolo gold) quando lo stato attivo viene spostata dall'elemento, ad esempio per aggiungere un'altra dichiarazione all'elenco o per tentare di modificare le schede nella finestra di progettazione.  
  
-   Se l'utente tenta di modificare le schede prima di impostare le proprietà di qualsiasi dichiarazione, visualizzata una finestra di dialogo che indica che l'applicazione non verrà compilato (o tutte le implicazioni) finché non vengono risolti gli avvisi. Se l'utente chiude la finestra di dialogo e sostituisce le tabulazioni comunque, un'icona (critica o avviso, come appropriata) viene aggiunto alla scheda dichiarazioni.  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>L'utilizzo forzato all'utente di leggere il testo prima della chiusura dell'interfaccia utente  
  
#### <a name="feature-team-goals"></a>Funzionalità degli obiettivi del team  
 Non consentire all'utente di chiudere l'interfaccia utente senza prima visualizzare il testo di spiegazione.  
  
#### <a name="anti-pattern"></a>Anti-pattern  
 Il team di inserimento di collegamenti video in varie posizioni nell'interfaccia utente di Visual Studio pronunciato contro il modello comune di una "X" chiusura spiegazione pulsante e una descrizione come specificato da UX e implementato invece un elenco a discesa e il collegamento "Non visualizzare più".  
  
 ![Testo esplicativo anti-pattern-errato](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **Non è corretto: obbligando l'utente per la lettura del testo esplicativo prima della chiusura dell'interfaccia utente è un anti-pattern all'interno di Visual Studio.**  
  
#### <a name="result"></a>Risultato  
 Anziché un semplice pulsante chiude (un solo clic), l'utente è costretto a utilizzare due clic distinti per ignorare semplicemente l'interfaccia utente in ogni punto in cui vengono visualizzati i collegamenti a video.  
  
#### <a name="alternatives"></a>Alternative  
 La progettazione corretta per questa situazione, è possibile seguire il modello comune per Internet Explorer, Office e Visual Studio: al passaggio del mouse, l'utente può visualizzare la descrizione della descrizione e un solo clic consente di nascondere l'interfaccia utente.  
  
 ![Testo esplicativo anti-pattern-corretto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti modello corretti")  
  
 **Corretto: come progettato, collegamenti video devono visualizzare una descrizione comando con informazioni aggiuntive al passaggio del mouse e fare clic sulla "X" deve chiudere il messaggio senza necessità di ulteriore interazione.**  
  
### <a name="using-command-bars-for-settings"></a>Utilizzo di barre dei comandi per le impostazioni  
 ![Anti-pattern barra dei comandi-figura A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-modello-FigureA")  
  
 **Figura a: comando barra anti-pattern**  
  
 **Figura A** rappresenta l'anti-pattern: inserimento di un'impostazione di sotto di un pulsante di comando che si applica solo al comando. In questo esercizio, sono disponibili comandi oltre Avvia debug, ad esempio visualizza nel Browser, Avvia senza eseguire debug ed Esegui istruzione, che rispetta l'impostazione selezionata.  
  
 ![Anti-pattern barra dei comandi-Figura B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-modello-FigureB")  
  
 **Figura b: migliore, ma comunque un anti-pattern della barra dei comandi**  
  
 Scherzo leggermente migliore, ma è ancora, è l'inserimento di impostazioni di questo tipo nelle barre degli strumenti, come illustrato nella **Figura B**. Mentre i pulsanti di divisione richiede meno spazio e pertanto un miglioramento rispetto a discesa, entrambi i progetti utilizza ancora una barra degli strumenti per promuovere un elemento che non è un comando.  
  
 ![Anti-pattern barra dei comandi-figura C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-modello-FigureC")  
  
 **Figura c: corretto utilizzo di pattern barra dei comandi di Visual Studio**  
  
 In **figura C**, l'impostazione è collegata a una serie di comandi. Non esiste alcuna impostazione globale e si passa semplicemente tra quattro comandi. Si tratta dell'unica situazione in cui i comandi della barra degli strumenti sono accettabili.  
  
### <a name="control-anti-patterns"></a>Anti-pattern di controllo  
 Alcuni anti-modelli sono utilizzo semplicemente non corretto o la presentazione di un controllo o un gruppo di controlli.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sottolineatura utilizzata come etichetta di gruppo, non un collegamento ipertestuale  
 Sottolineare il testo deve essere utilizzato solo per i collegamenti ipertestuali.  
  
 **Non valido:**  
  
 ![Sottolineatura di anti-pattern in etichette gruppo](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "g_GroupLabelIncorrect&0102;")  
  
 **Testo sottolineato che non è un collegamento ipertestuale è un anti-modello di Visual Studio.**  
  
 **Buona:**  
  
 ![Sottolineatura di anti-pattern in etichette gruppo (corretto)](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "h_GroupLabelCorrect&0102;")  
  
 **Stile correttamente, non hyperlink testo verrà visualizzato solo il tipo di carattere ambiente.**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Facendo clic su una casella di controllo di risultati in una finestra di dialogo popup  
 Selezionare la casella di controllo "Abilita Desktop remoto per tutti i ruoli" della procedura guidata "Pubblica l'applicazione Windows Azure" immediatamente, viene visualizzata una finestra di dialogo popup, un anti-modello di Visual Studio. Inoltre, il campo casella di controllo non viene riempita con una casella di controllo dopo la selezione, un'altra interazione anti-pattern.  
  
 ![Casella di controllo popup anti-pattern](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "i_CheckboxPopup&0102;")  
  
 **Accedere a una finestra di dialogo al termine fare clic su una casella di controllo un anti-modello di Visual Studio.**  
  
### <a name="hyperlink-anti-patterns"></a>Collegamenti ipertestuali per anti-pattern  
 Nell'esempio seguente contiene due anti-pattern.  
  
1.  In primo piano rosso accensione al passaggio del mouse significa che non viene utilizzato il corretto colore condiviso dal servizio di tipo di carattere.  
  
2.  "Informazioni" non è il testo appropriato per un collegamento a un argomento concettuale. Obiettivo dell'utente non è ulteriori informazioni, che consiste nel comprendere le implicazioni di propria scelta.  
  
 ![Collegamenti ipertestuali per anti-pattern](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "j_HyperlinkIncorrect&0102;")  
  
 **Ignorando il servizio di colore e usando "Ulteriori informazioni" per i collegamenti ipertestuali sono anti-modelli di Visual Studio.**  
  
 **Migliore soluzione:** la questione potrebbe chiedere all'utente facendo clic sul collegamento.  
  
-   Come funzionano i servizi di Windows Azure?  
  
-   Quando è necessario un progetto di servizi mobili di Azure?  
  
#### <a name="using-click-here-for-links"></a>Utilizzando "Fare clic qui" per i collegamenti  
 Collegamenti ipertestuali dovrebbero essere autodescrittivi. È un anti-modello da utilizzare "Fare clic qui" o qualsiasi variazione simile.  
  
 **Bad:** "Fare clic qui per istruzioni su come creare un nuovo progetto."  
  
 **Buona:** "Come creare un nuovo progetto?"
