---
title: Le notifiche e l&quot;avanzamento di Visual Studio | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 6
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
ms.openlocfilehash: 1f7823754601161200edafdce998ebe9aeab2723
ms.lasthandoff: 02/22/2017

---
# <a name="notifications-and-progress-for-visual-studio"></a>Le notifiche e l'avanzamento di Visual Studio
##  <a name="a-namebkmknotificationsystemsa-notification-systems"></a><a name="BKMK_NotificationSystems"></a>Sistemi di notifica  
  
### <a name="overview"></a>Panoramica  
 Esistono diversi modi per informare l'utente ciò che accade in Visual Studio sulla loro attività di sviluppo software.  
  
 Durante l'implementazione di qualsiasi tipo di notifica:  
  
-   **Mantenere il numero di notifiche per il valore minimo** numero effettivo. I messaggi di notifica devono applicare alla maggior parte degli utenti di Visual Studio o agli utenti di un'area specifica funzionalità. Un uso eccessivo di notifiche sidetrack l'utente o diminuire percepita facilità di utilizzo del sistema.  
  
-   **Assicurarsi che si intende presentare messaggi chiare e utilizzabili** che l'utente può utilizzare per richiamare il contesto appropriato per la scelta di opzioni più complesse e richiedere ulteriori interventi.  
  
-   **Presentare in modo appropriato i messaggi sincroni e asincroni.** Le notifiche sincrone indicano che un elemento richiede attenzione immediata, ad esempio quando si blocca un servizio web o un codice di eccezione. L'utente deve essere informata di tali situazioni immediatamente in modo che richiede l'input, ad esempio in una finestra di dialogo modale. Notifiche asincrone sono quelle che l'utente deve conoscere ma non sono tenuto ad agire immediatamente, ad esempio quando viene completata un'operazione di compilazione o distribuzione di siti web completata. Tali messaggi devono essere più ambiente e non interrompere il flusso di attività dell'utente.  
  
-   **Utilizzare le finestre di dialogo modale solo quando è necessario impedire all'utente di richiedere ulteriori interventi** prima di riconoscere il messaggio o di prendere una decisione presentata nella finestra di dialogo.  
  
-   **Rimuovere le notifiche di ambiente quando non sono più validi.** Non richiedono all'utente di ignorare una notifica nel caso siano state già azione per risolvere il problema che sono stati informati.  
  
-   **Tenere presente che le notifiche possono portare a false correlazioni.** Gli utenti potrebbero ritenere che uno o più delle azioni è attivata una notifica quando in realtà non esiste alcuna relazione causale. Essere chiaro il messaggio di notifica relativo contesto, il trigger e l'origine della notifica.  
  
### <a name="choosing-the-right-method"></a>Scelta del metodo  
 Utilizzare questa tabella per agevolare la scelta del metodo per notificare all'utente del messaggio.  
  
|Metodo|Uso|Non utilizzare|  
|------------|---------|----------------|  
|[Finestre di messaggio di errore modale](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Utilizzarlo quando è necessaria una risposta dell'utente prima di procedere.|Non utilizzare quando non è necessario bloccare l'utente e interrompere il flusso. Evitare di utilizzare le finestre di dialogo modale se è possibile visualizzare il messaggio in un altro modo meno intrusiva.|  
|[Barra di stato IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Utilizzare quando sono presenti informazioni testuali ambiente relativi allo stato di un processo.|Non utilizzare da soli. Utilizzate in combinazione con un altro meccanismo di commenti e suggerimenti.|  
|[Barra informazioni incorporata](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|In una finestra degli strumenti o una finestra del documento, utilizzata per notificare lo stato di avanzamento, lo stato di errore, risultati e/o informazioni utilizzabili.|Non utilizzare se le informazioni non sono pertinente per il percorso in cui si trova sulla barra informazioni.<br /><br /> Non usare all'esterno di una finestra del documento o strumento.|  
|[Modifiche del cursore del mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Può essere utilizzata per notificare che un processo in corso. Utilizzato anche per notificare che è una modifica dello stato di mouse, ad esempio quando trascinamento è in corso o che il cursore del mouse è una modalità specifica, ad esempio modalità di disegno.|Non utilizzare per le modifiche di stato di avanzamento breve o se gelatinoso del cursore è probabile (ad esempio, quando associato alle parti di un processo in esecuzione più lunga anziché per l'intero processo).|  
|[Indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Utilizzarlo quando è necessario segnalare lo stato (determinato o indeterminato). Esistono diversi tipi di indicatori di stato di avanzamento e di utilizzo specifici per ogni. Vedere [indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Finestra di Visual Studio notifiche](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La finestra delle notifiche non è estendibile pubblicamente. Tuttavia, utilizzato per comunicare un intervallo di messaggi relativi a Visual Studio, inclusi i problemi critici e notifiche informative degli aggiornamenti per Visual Studio o per i pacchetti licenze.|Non utilizzare per altri tipi di notifiche.|  
|[Elenco errori](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Quando il problema fa riferimento direttamente alla soluzione attualmente aperta dell'utente verificato un errore (errore/avviso/informazioni), si potrebbe essere necessario intervenire sul codice.<br /><br /> Questo dovrebbe includere, ad esempio:<br /><br /> -I messaggi del compilatore (errore/avviso/informazioni)<br /><br /> -Messaggi di diagnostica/Analyzer codice sul codice<br /><br /> -I messaggi di compilazione<br /><br /> Può essere appropriato per i problemi relativi ai file di progetto o soluzione, ma è consigliabile innanzitutto un'indicazione di Esplora soluzioni.|Non utilizzare per gli elementi che non dispongono di alcuna relazione con il codice dell'utente soluzione aperta.|  
|Le notifiche di editor: lampadina|Utilizzarlo quando si dispone di una correzione disponibile per risolvere un problema che esiste nel file aperto.<br /><br /> Lampadina deve inoltre essere utilizzato per l'hosting di azioni rapide che vengono eseguite nel codice dell'utente su richiesta, ad esempio refactoring, ma in questo caso non verrà visualizzato "stile notifica".|Non utilizzare per gli elementi che non ha alcuna relazione al file aperto.|  
|Le notifiche di editor: linee a zigzag|Utilizzare per avvisare l'utente a un problema con un intervallo particolare del codice aperto (ad esempio, una sottolineatura ondulata rossa per gli errori).|Non utilizzare per gli elementi che non sono correlati a un intervallo particolare del codice aperto.|  
|[Barre di stato incorporata](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Utilizzare per fornire lo stato relative al contenuto o processo nel contesto di una finestra strumento specifico, una finestra del documento o una finestra di dialogo.|Non utilizzare per le notifiche di categoria, processi o gli elementi che non dispongono di alcuna relazione con il contenuto all'interno della finestra di specifica.|  
|[Notifiche nella barra delle applicazioni di Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Utilizzare per le notifiche per i processi di out-of-process della superficie di attacco o complementare di applicazioni.|Non utilizzare per le notifiche relative all'IDE.|  
|[Bolle di notifica](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Consente di inviare una notifica di un processo remoto o modificare **all'esterno di** dell'IDE.|Non utilizzare come mezzo per notificare all'utente di processi **all'interno di** l'IDE.|  
  
### <a name="notification-methods"></a>Metodi di notifica  
  
####  <a name="a-namebkmkmodalerrormessagedialogsa-modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Finestre di messaggio di errore modale  
 Una finestra di messaggio di errore modale viene utilizzata per visualizzare un messaggio di errore che richiede la conferma dell'utente o un'azione.  
  
 ![Messaggio di errore modale](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "01_ModalErrorMessage&0901;")  
  
 **Una finestra di messaggio di errore modale segnalazione all'utente di una stringa di connessione non valida per un database**  
  
####  <a name="a-namebkmkidestatusbara-ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>Barra di stato IDE  
 La probabilità che gli utenti si noti il testo della barra di stato è correlato a tutto tondo computer degli utenti e specifica esperienza con la piattaforma Windows. La base clienti di Visual Studio tendono a essere esperti in entrambi i casi, anche se gli utenti di Windows anche competente potrebbero mancare modifiche nella barra di stato. Pertanto, la barra di stato è più adatta per scopi informativi o come un segnale ridondante per le informazioni visualizzate in un' posizione. In una finestra di dialogo o nella finestra strumento di notifica, è necessario specificare qualsiasi tipo di informazioni critiche che l'utente deve essere risolto immediatamente.  
  
 La barra di stato di Visual Studio è progettata per consentire più tipi di informazioni da visualizzare. Si è suddivisa in aree commenti e suggerimenti, finestra di progettazione, indicatore di stato, animazione e client.  
  
 L'area di commenti e suggerimenti e l'area di progettazione sono sempre visibili. La barra di avanzamento e l'animazione aree sono sempre dinamica e basata sul contesto utente. L'area di progettazione ha una larghezza statica dipende dalla lunghezza della stringa estratte da una risorsa associata per il messaggio di testo. In questo modo la localizzazione di ridimensionare la larghezza senza richiedere una modifica del codice. Per l'inglese, la larghezza di questa stringa è circa 220 pixel. L'area di progettazione si comporterà in genere e l'area di commenti e suggerimenti sarà assorbire lo spazio rimanente.  
  
 La barra di stato ha anche colori per aggiungere interesse visivo e il valore funzionale comunicando vari cambiamenti di stato IDE, ad esempio quando l'IDE è in modalità debug.  
  
 ![Modifiche ai colori della barra di stato dell'IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "02_IDEStatusBar&0901;")  
  
 **Colori della barra di stato IDE**  
  
####  <a name="a-namebkmkembeddedinfobara-embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Barra informazioni incorporata  
 Utilizzare una barra informazioni nella parte superiore di una finestra del documento o una finestra degli strumenti per informare l'utente di uno stato o una condizione. Inoltre possibile includere comandi in modo che l'utente può avere un modo per effettuare con facilità un'azione. Sulla barra informazioni sono un controllo standard della shell. Evitare di crearne uno personalizzato, che agiscono e vengono visualizzati non coerente con altri utenti nell'IDE. Vedere [visualizzazione](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) per indicazioni sull'utilizzo e i dettagli di implementazione.  
  
 ![Barra informazioni incorporata](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "03_EmbeddedInfobar&0901;")  
  
 **Una barra informazioni incorporate in una finestra del documento, avvisa l'utente che è in modalità debug cronologico dell'IDE e l'editor non risponderà esattamente come avviene in modalità di debug standard.**  
  
####  <a name="a-namebkmkmousecursorchangesa-mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Modifiche del cursore del mouse  
 Quando si modifica il cursore del mouse, utilizzare i colori che sono associati al servizio VSColor e sono già associate con il cursore. Cursore assume l'aspetto possono essere utilizzati per indicare un'operazione in corso, nonché premere aree in cui l'utente viene posizionato su una destinazione che può essere trascinata, trascinata o utilizzata per selezionare un oggetto.  
  
 Utilizzare il cursore occupato/attesa solo quando tutto il tempo della CPU disponibile deve essere riservata per un'operazione, impedendo all'utente di esprimere qualsiasi ulteriore input. Nella maggior parte dei casi con applicazioni ben scritte tramite il multithreading, devono essere rari volte quando gli utenti possono eseguire altre operazioni.  
  
 Tenere presente che le modifiche cursore sono utili quando una pila ridondante per le informazioni presentate in un' posizione. Non fare affidamento su una modifica di cursore come unico metodo di comunicare con l'utente, soprattutto quando si desidera comunicare qualcosa che è fondamentale che l'utente deve indirizzare.  
  
####  <a name="a-namebkmknotsysprogressindicatorsa-progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Indicatori di stato  
 Gli indicatori di stato sono importanti per fornire i commenti degli utenti durante i processi di più di pochi secondi per il completamento. Gli indicatori di stato possono essere visualizzati sul posto (quasi il punto di avvio dell'azione in corso), in una barra di stato incorporata, nella finestra di dialogo modale o nella barra di stato di Visual Studio. Seguire le indicazioni fornite in [indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) relative all'uso e l'implementazione.  
  
####  <a name="a-namebkmkvsnotificationstoolwindowa-visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Finestra di Visual Studio notifiche  
 La finestra di notifiche di Visual Studio notifica sviluppatori sulle licenze, ambiente (Visual Studio), estensioni e aggiornamenti. Gli utenti possono ignorare notifiche specifiche o possono scegliere di ignorare determinati tipi di notifiche. L'elenco delle notifiche ignorate viene gestito in un **Strumenti > opzioni** pagina.  
  
 La finestra delle notifiche non è attualmente estendibile.  
  
 ![Finestra di Visual Studio notifiche](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "06_VSNotificationsWindow&0901;")  
  
 **Finestra di Visual Studio notifiche degli strumenti**  
  
####  <a name="a-namebkmkerrorlista-error-list"></a><a name="BKMK_ErrorList"></a>Elenco errori  
 Una notifica all'interno dell'elenco di errori indicano errori e avvisi che si è verificato durante la compilazione e o processo di compilazione e consente all'utente di spostarsi nel codice di errore codice specifico.  
  
 ![Elenco errori](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "08_ErrorList&0901;")  
  
 **Elenco di errori in Visual Studio**  
  
####  <a name="a-namebkmkembeddedstatusbarsa-embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Barre di stato incorporata  
 Poiché la barra di stato IDE è dinamica, con contesto area client impostato per la finestra di documento attivo e le informazioni di aggiornamento nel contesto dell'utente e/o di risposte del sistema, è difficile mantenere una visualizzazione continua delle informazioni o fornire lo stato su processi asincroni a lungo termine. Ad esempio, la barra di stato IDE non è appropriata per le notifiche dei risultati dei test eseguiti per più esecuzioni e/o le selezioni delle voci immediatamente utilizzabili. È importante mantenere tali informazioni sullo stato nel contesto della finestra del documento o lo strumento in cui l'utente effettua una selezione o avvia un processo.  
  
 ![Barra di stato incorporata](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "09_EmbeddedStatusBar&0901;")  
  
 **Barra di stato incorporata in Visual Studio**  
  
####  <a name="a-namebkmkwindowstraya-windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Notifiche nella barra delle applicazioni di Windows  
 Area di notifica è accanto il sistema di Windows dell'orologio della barra delle applicazioni di Windows. Molte utilità e componenti software forniscono icone in quest'area, in modo che l'utente può ottenere un menu di scelta rapida per le attività a livello di sistema, ad esempio modifica risoluzione dello schermo o ottenere gli aggiornamenti software.  
  
 Notifiche a livello di ambiente devono essere replicate nell'hub notifiche di Visual Studio, non l'area di notifica di Windows.  
  
####  <a name="a-namebkmknotificationbubblesa-notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Bolle di notifica  
 Fumetti notifica possono essere visualizzati come informativi all'interno di un editor o la finestra di progettazione o come parte dell'area di notifica di Windows. L'utente visualizza le bolle come i problemi che consentono di risolvere in un secondo momento, che è un vantaggio per le notifiche non critiche. Le bolle non sono appropriate per le informazioni critiche che l'utente deve risolvere immediatamente. Se si utilizza fumetti notifica in Visual Studio, seguire la [linee guida per Windows Desktop per fumetti notifica](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx).  
  
 ![Fumetto della notifica](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "07_NotificationBubbles&0901;")  
  
 **Fumetto della notifica nell'area di notifica di Windows utilizzato per Visual Studio**  
  
##  <a name="a-namebkmkprogressindicatorsa-progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Indicatori di stato  
  
### <a name="overview"></a>Panoramica  
 Gli indicatori di stato sono una parte importante di un sistema di notifica per dare all'utente un feedback. Indicano l'utente quando i processi e le operazioni verranno completata. Tipi di indicatori familiare includono indicatori di stato, i cursori di rotazione e icone animate. Il tipo e il posizionamento di un indicatore di stato dipende dal contesto, tra cui ciò che viene segnalato e quanto tempo il processo o un'operazione è necessari per completare.  
  
#### <a name="factors"></a>Fattori  
 Per determinare il tipo di indicatore appropriato, è necessario determinare i fattori seguenti.  
  
1.  **Durata:** tempo richiederà l'operazione  
  
2.  **Modalità:** se l'operazione è modale per l'ambiente (blocchi dell'interfaccia utente fino al completamento del processo)  
  
3.  **Permanente o temporaneo:** se il risultato finale dello stato di avanzamento deve essere segnalato e/o visualizzabile in un secondo momento  
  
4.  **Determinato o indeterminato:** se l'ora di fine operazione e lo stato può essere calcolati  
  
5.  **Posizione immagine/Textual:** se lo stato di avanzamento o il processo viene acquisita inline, nel corpo di un messaggio o un controllo specifico, ad esempio il controllo struttura ad albero  
  
6.  **Prossimità:** se lo stato di avanzamento deve essere in prossimità dell'interfaccia utente che non si riferisce alla. (Ad esempio, è possibile nella barra di stato, che potrebbe essere portata di mano, o e deve necessariamente trovarsi accanto al pulsante che ha avviato il processo?)  
  
#### <a name="determinate-progress"></a>Stato determinato  
  
|Tipo di stato di avanzamento|Quando e come utilizzare|Note|  
|-------------------|-------------------------|-----------|  
|Indicatore di stato (determinata)|Durata prevista >&5; secondi.<br /><br /> Può includere una descrizione dei dettagli del processo.|**Non** incorporare testo animazione.|  
|Barra informazioni|Messaggistica associata a scelta rapida dell'interfaccia utente. Vedere [visualizzazione](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Può includere una descrizione dei dettagli del processo.|**Non** utilizzare più visualizzazione quando è necessario indicare più processi. Utilizzare le barre di avanzamento in pila.|  
|Finestra di output|Notifica temporanea: processo a livello di applicazione che l'utente desidera **esaminare** dettagli di dopo il completamento.|**Non** utilizzare se l'utente dovrà fare riferimento ai dati in un secondo momento.|  
|File di log|Abbinato notifica intransient in casi quando è importante **salvare** dettagli dopo il completamento.||  
|Barra di stato|Notifica temporanea: processo a livello di applicazione che l'utente avrà **non è necessario** dettagli di dopo il completamento.<br /><br /> Include un indicatore di stato incorporata.<br /><br /> Può includere una descrizione dei dettagli del processo.||  
  
#### <a name="indeterminate-progress"></a>Indicatore di stato indeterminato  
  
|Tipo di stato di avanzamento|Quando e come utilizzare|Note|  
|-------------------|-------------------------|-----------|  
|Indicatore di stato (indeterminato)|Durata prevista >&5; secondi.<br /><br /> Può includere una descrizione dei dettagli del processo.|**Non** incorporare testo animazione.|  
|ANTS (animati punti orizzontale)|Round trip al server.<br /><br /> Trova il punto di near del contesto parte superiore del contenitore padre.|**Non** utilizzare se non è associato dall'intero contenitore.|  
|Spinner (anello di stato)|Processo associate a scelta rapida dell'interfaccia utente o in cui lo spazio è un fattore importante.<br /><br /> Può includere una descrizione dei dettagli del processo.||  
|Barra informazioni|Messaggistica associata a scelta rapida dell'interfaccia utente. Vedere [visualizzazione](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Non** utilizzare più visualizzazione quando è necessario indicare più processi. Utilizzare le barre di avanzamento in pila.|  
|Finestra di output|Notifica temporanea: processo a livello di applicazione che l'utente desidera **esaminare** dettagli di dopo il completamento.|**Non** utilizzare per le informazioni necessarie per rendere persistenti tra le sessioni.|  
|File di log|Abbinato notifica intransient in casi quando è importante **salvare** dettagli dopo il completamento.||  
|Barra di stato|Notifica temporanea: processo a livello di applicazione che l'utente avrà **non è necessario** dettagli di dopo il completamento.<br /><br /> Include l'indicatore di stato incorporata.<br /><br /> Può includere una descrizione dei dettagli del processo.||  
  
### <a name="progress-indicator-types"></a>Tipi di indicatore di stato  
  
#### <a name="progress-bars"></a>Indicatori di stato  
  
##### <a name="indeterminate"></a>Indeterminato  
 ![Indicatore di stato indeterminato](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "04_Indeterminate&0901;")  
  
 **Indicatore di stato indeterminato**  
  
 "Indeterminato" significa che lo stato generale di un'operazione o processo non può essere determinato. Utilizzare le barre di stato indeterminato per operazioni che richiedono una quantità di tempo illimitata o che accedono a un numero sconosciuto di oggetti. Utilizzare una descrizione testuale a complemento di ciò che accade. Utilizzare i timeout dei limiti per operazioni basate sul tempo. Barre di stato indeterminato utilizzano animazioni per mostrare che lo stato di avanzamento è stata effettuata, ma non forniscono altre informazioni. Non scegliere un indicatore di stato indeterminato basato solo sull'eventuale mancanza di accuratezza da solo.  
  
##### <a name="determinate"></a>Determinata  
 ![Indicatore di stato determinato](../../extensibility/ux-guidelines/media/0901-05_determinate.png "05_Determinate&0901;")  
  
 **Indicatore di stato determinato**  
  
 "Determinato" significa che un'operazione o un processo richiede una quantità limitata di tempo, anche se tale quantità di tempo non è possibile prevedere con precisione. Indicare chiaramente il completamento. Non lasciare un indicatore di stato di passare al 100%, a meno che non è stata completata l'operazione. Animazione della barra di stato determinato sposta da sinistra a destra da 0 a 100%.  
  
 Non spostare l'indicatore di stato con le versioni precedenti durante un'operazione. La barra deve passare costantemente quando inizia l'operazione e raggiungere 100% quando termina. Il punto dell'indicatore di stato è consentire all'utente un'idea di quanto tempo richiede dell'intera operazione, indipendentemente dalla quanti passaggi sono necessari.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Simultanee reporting (indicatori di stato in pila)  
 Se un'operazione richiederà molto tempo, ad esempio possibile utilizzare diversi minuti, quindi due indicatori di stato, uno che mostra lo stato di avanzamento complessivo per un'operazione e l'altra per l'avanzamento del passaggio corrente. Ad esempio, se un programma di installazione copia numerosi file, un indicatore di stato può essere utilizzato per indicare l'intero processo di tempo durante il secondo può indicare la percentuale del file corrente o directory vengono copiata. Non segnalare più di cinque operazioni simultanee o i processi usando le barre di avanzamento in pila. Se si dispone di più di cinque operazioni simultanee o processi per report, utilizzare una finestra di dialogo modale con un pulsante Annulla e indicare i dettagli di stato di avanzamento nella finestra di Output.  
  
##### <a name="textual-descriptions"></a>Descrizioni testuali  
 Utilizzare una descrizione testuale per accompagnare qual è il problema e il tempo stimato di completamento. Se non è possibile determinare il tempo richiesto un'operazione, un'icona animata anziché un indicatore di stato potrebbe essere una scelta migliore per commenti e suggerimenti.  
  
 Visual Studio fornisce un indicatore di stato standard nella barra di stato che può essere utilizzato da qualsiasi prodotto integrato in Visual Studio. Per descrizioni testuali di ciò che accade quando l'indicatore di stato viene animato, il testo della barra di stato può essere aggiornato.  
  
#### <a name="other-progress-indicators"></a>Altri indicatori di stato  
  
##### <a name="ants-animated-horizontal-dots"></a>ANTS (animati punti orizzontale)  
 ![Stato di avanzamento ants](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903&01;_Ants")  
  
 "Formiche," animati punti orizzontali, fornire un riferimento visivo per un processo del server di andata e ritorno indeterminato.  
  
##### <a name="spinner-progress-ring"></a>Spinner (anello di stato)  
 ![Indicatore di avanzamento](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903&02;_Spinner")  
  
 La casella di selezione (noto anche come un "anello di stato") è un indicatore di stato indeterminato utilizzato principalmente in relazione a scelta rapida dell'interfaccia utente. Visualizzare una casella di selezione in prossimità al relativo contenuto correlato, ad esempio un'intestazione di categoria testuale, messaggistica o controllo.  
  
##### <a name="cursor-feedback"></a>Commenti e suggerimenti del cursore  
 Per le operazioni che prendono da 2 a 7 secondi, fornire commenti e suggerimenti del cursore. In genere, ciò significa utilizzare il cursore di attesa fornito dal sistema operativo. Per ulteriori informazioni, vedere l'articolo MSDN [Cursors.Wait proprietà](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).  
  
#### <a name="progress-indicator-locations"></a>Percorsi di indicatore di stato di avanzamento  
  
##### <a name="status-bar"></a>Barra di stato  
 La barra di stato fornisce all'applicazione una posizione in cui visualizzare i messaggi e informazioni utili per l'utente senza interrompere le attività dell'utente. In genere visualizzato nella parte inferiore di una finestra, lo stato di avanzamento sarà un riquadro di suggerimento di strumenti che include un messaggio relativo alla misura dello stato di avanzamento in combinazione con un indicatore.  
  
 ![Barra di stato con indicatore di stato](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903&03;_StatusBarProgressBar")  
  
 **Barra di stato con indicatore di stato**  
  
 ![Barra di stato con messaggistica](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903&04;_StatusBarMessage")  
  
 **Barra di stato con la descrizione testuale**  
  
##### <a name="infobar"></a>Barra informazioni  
 È simile alla barra di stato, la barra informazioni fornisce notifica contesto e messaggistica, che può anche essere abbinata a indicatori di stato indeterminato, ad esempio la barra di stato o una casella di selezione. Barra informazioni non deve fornire lo stato di avanzamento livello granulare o indicazione di stato determinato. Vedere [visualizzazione](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Barra informazioni con indicatore di stato e messaggistica](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903&05;_InfoBar")  
  
 **Barra informazioni con indicatore di stato e la descrizione testuale**  
  
 ![Barra informazioni in una finestra](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903&06;_InfoBarInWindow")  
  
 **Barra informazioni nella finestra Analisi codice**  
  
##### <a name="inline"></a>Inline  
 Indica lo stato di avanzamento inline può essere rappresentato da uno dei tipi di caricatore lo stato di avanzamento. In genere è associata l'indicatore di stato con funzionalità di messaggistica, ma questo non è un requisito.  
  
 ![Indicatore di avanzamento inline](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903&07;_InlineSpinner")  
  
 **Casella combinata con la descrizione testuale di selezione**  
  
 ![Indicatori di stato in pila inline](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903&08;_InlineStackedProgress")  
  
 **Barre di stato determinato in pila**  
  
 ![Messaggistica sullo stato inline](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903&09;_InlineText")  
  
 **Testo inline Esplora server: aggiornamento...**  
  
##### <a name="tool-windows"></a>Finestre degli strumenti  
 Indicazione di stato globale è rappresentato da una barra di stato indeterminato trova direttamente sotto la barra degli strumenti.  
  
 ![Indicatore di stato indeterminato globale](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903&23;_GlobalIndeterminate")  
  
 **Barra di stato indeterminato globale di Team Explorer**  
  
##### <a name="dialogs"></a>Finestre di dialogo  
 Finestre di dialogo può contenere i tipi di stato di avanzamento del caricatore. Gli indicatori di stato possono essere associati con la messaggistica nonché combinati con più livelli di indicazione di stato di avanzamento per rappresentare granulare e processi secondari.  
  
 ![Finestra di dialogo con più tipi di indicatori di stato di avanzamento](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903&11;_Dialog")  
  
 **Finestra di dialogo Visual Studio con più tipi di indicatori di stato di avanzamento e processi simultanei**  
  
 ![Finestra di dialogo con caricatore dello stato e messaggistica](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903&12;_Dialog2")  
  
 **Finestra di dialogo Visual Studio con caricatore dello stato e messaggistica inline dei comandi**  
  
##### <a name="document-well"></a>Documento e  
 Il documento può anche visualizzare più tipi di stato del caricatore in combinazione con i controlli.  
  
 ![Lo stato di avanzamento e di messaggistica nel documento](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903&13;_DocumentWell")  
  
 **Barra di stato indeterminato di sotto della barra degli strumenti**  
  
##### <a name="output-window"></a>Finestra di output  
 La finestra di Output è appropriata per la gestione di progressione di processo e lo stato di avanzamento tramite messaggistica testuale inline. È consigliabile utilizzare la barra di stato e qualsiasi Output finestra avanzamento.  
  
 ![Messaggistica sullo stato nella finestra di Output](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903&14;_OutputWindow")  
  
 **Finestra di output con stato del processo in corso e attendere la messaggistica**  
  
##  <a name="a-namebkmkinfobarsa-infobars"></a><a name="BKMK_Infobars"></a>Visualizzazione  
  
### <a name="overview"></a>Panoramica  
 Visualizzazione assegnare all'utente un indicatore vicino al relativo punto di attenzione e utilizzo del controllo barra informazioni condivise assicura la coerenza nell'aspetto e l'interazione.  
  
 ![Barra informazioni](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904&01;_Infobar")  
  
 **Visualizzazione in Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Utilizza appropriato per una barra informazioni  
  
-   Per consentire all'utente un messaggio non bloccante ma importante rilevante per il contesto corrente  
  
-   Per indicare che l'interfaccia utente in un determinato stato o una condizione che comporta alcune implicazioni di interazione, ad esempio il debug cronologico  
  
-   Per notificare all'utente che il sistema ha rilevato dei problemi, ad esempio quando un'estensione causa problemi di prestazioni  
  
-   Per fornire all'utente un modo per effettuare con facilità un'azione, ad esempio quando l'editor rileva che un file è mista spazi e tabulazioni  
  
##### <a name="do"></a>Eseguire:  
  
-   Mantenere il testo del messaggio sulla barra informazioni breve e il punto.  
  
-   Mantenere breve il testo su collegamenti e pulsanti.  
  
-   Verificare le opzioni "action" è fornire agli utenti sono minime, che mostra solo le azioni necessarie.  
  
##### <a name="dont"></a>Non:  
  
-   Utilizzare una barra informazioni per rendere disponibili i comandi standard che devono essere inseriti in una barra degli strumenti.  
  
-   Utilizzare una barra informazioni al posto di una finestra di dialogo modale.  
  
-   Creare un messaggio di fuori di una finestra mobile.  
  
-   Utilizzare visualizzazione più in diverse posizioni all'interno della stessa finestra.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Visualizzazione più possibile visualizzare contemporaneamente?  
 Sì, visualizzazione più possibile visualizzare contemporaneamente. Vengono visualizzati in ordine cronologico primo arrivato con la prima barra informazioni che mostrano in che Mostra visualizzazione superiore e aggiuntive seguente.  
  
 L'utente vedrà un massimo di tre visualizzazione alla volta, dopo che, se altre visualizzazione sono disponibili, l'area della barra informazioni non sarà più scorrevole.  
  
### <a name="creating-an-infobar"></a>Creazione di una barra informazioni  
 Sulla barra informazioni con quattro sezioni, da sinistra a destra:  
  
-   **Icona:** tratta dove aggiungere qualsiasi icona si desidera visualizzare la barra delle informazioni, ad esempio un'icona di avviso.  
  
-   **Testo:** è possibile aggiungere testo per descrivere l'utente scenario/situazione è, insieme a collegamenti all'interno del testo, se necessario. Tenere presente che il testo conciso.  
  
-   **Azioni:** in questa sezione deve contenere collegamenti e i pulsanti per le azioni che l'utente può richiedere la barra informazioni.  
  
-   **Pulsante Chiudi:** l'ultima sezione a destra può disporre di un pulsante Chiudi.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Creazione di una barra informazioni standard nel codice gestito  
 La classe InfoBarModel può essere utilizzata per creare un'origine dati per una barra informazioni. Utilizzare uno di questi quattro costruttori:  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 Di seguito è riportato un esempio che crea un InfoBarModel con un testo con un collegamento ipertestuale, un pulsante di azione e un'icona.  
  
 ![Barra informazioni con collegamento ipertestuale](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904&02;_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>Creazione di una barra informazioni standard nel codice nativo  
 Implementare IVsInfoBar l'interfaccia per fornire una barra informazioni dal codice nativo.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Recupero di una barra informazioni UIElement da una barra informazioni  
 L'implementazione InfoBarModel o IVsInfoBar sono modelli di dati che devono essere trasformati in un oggetto UIElement affinché venga visualizzato nell'interfaccia utente. Un oggetto UIElement può essere recuperato con il servizio SVsInfoBarUIFactory/IVsInfoBarUIFactory.  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>Selezione host  
 Visualizzazione possono essere visualizzati in uno o più delle seguenti posizioni:  
  
-   Finestre degli strumenti  
  
-   All'interno di una scheda di documento  
  
> [!IMPORTANT]
>  È possibile posizionare una barra informazioni per fornire un messaggio relativo contesto globale. Questo verrà visualizzato tra le barre degli strumenti e il documento e. Questa operazione è sconsigliata perché causa problemi "passare e jerk" dell'IDE e deve essere evitato se non assolutamente necessario e appropriato.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Inserire una barra informazioni in un ToolWindowPane  
 Il metodo ToolWindowPane.AddInfoBar(IVsInfoBar) può essere utilizzato per aggiungere una barra informazioni a una finestra degli strumenti. Questa API è possibile aggiungere un IVsInfoBar (di cui InfoBarModel è un'implementazione predefinita), o un IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Inserire una barra informazioni in un documento o non ToolWindowPane  
 Per inserire una barra informazioni in qualsiasi IVsWindowFrame, utilizzare la proprietà VSFPROPID_InfoBarHost per ottenere il IVsInfoBarHost per il frame e quindi aggiungere la barra informazioni UIElement.  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>Inserimento di una barra informazioni nella finestra principale  
 Per inserire una barra informazioni nella finestra principale, utilizzare VSSPROPID_MainWindowInfoBarHost del servizio IVsShell per ottenere IVsInfoBarHost della finestra principale e quindi aggiungere la barra informazioni UIElement.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Saprà quando l'utente esegue un'operazione la barra informazioni  
 Sì, si tornerà ogni azione di evento per l'autore sulla barra informazioni. È l'autore sulla barra informazioni per eseguire l'azione nell'IDE in base alla selezione utente sulla barra informazioni. Visualizzazione verrà automaticamente rimossa dall'host il cui pulsante Chiudi è stato fatto clic, ma altre operazioni sono necessario se altri visualizzazione devono essere rimosse dopo la chiusura. I dati di telemetria anche dovranno essere registrati in modo indipendente da ogni barra informazioni.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Ricezione di eventi sulla barra informazioni in un ToolWindowPane  
 ToolWindowPane dispone di due eventi per la visualizzazione. L'evento InfoBarClosed viene generato quando una barra informazioni all'interno di ToolWindowPane viene chiuso. L'evento InfoBarActionItemClicked viene generato quando viene selezionato un collegamento ipertestuale o un pulsante sulla barra informazioni.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Ricezione di eventi sulla barra informazioni direttamente da UIElement  
 IVsInfoBarUIElement.Advise consente di sottoscrivere gli eventi direttamente da UIElement di una barra informazioni. Implementazione di IVsInfoBarUIEvents consente all'autore di chiusura di ricezione e fare clic su eventi.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="a-namebkmkerrorvalidationa-error-validation"></a><a name="BKMK_ErrorValidation"></a>Convalida di errore  
 Quando un utente immette le informazioni che non sono accettabile, ad esempio quando un campo obbligatorio è stato ignorato o quando si immettono dati in formato non corretto, è preferibile utilizzare la convalida o commenti e suggerimenti vicino al controllo anziché utilizzare una finestra di dialogo di errore popup blocco.  
  
### <a name="field-validation"></a>Convalida campo  
 Convalida di moduli e campi è costituita da tre componenti: un controllo, un'icona e una descrizione comando. Sebbene diversi tipi di controlli è possono utilizzare questo, una casella di testo verrà utilizzata come esempio.  
  
 ![Campo convalida (vuoto)](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905&01;_FieldValidation")  
  
 Se il campo è obbligatorio, deve essere presente filigrana testo indicante ** \<obbligatorio >** e lo sfondo del campo deve essere chiaro giallo (VSColor: `Environment.ControlEditRequiredBackground`) e primo piano deve essere grigio (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Campo di convalida con etichetta "Obbligatorio"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905&02;_FieldValidationRequired")  
  
 Il programma può determinare che il controllo è in uno stato di *il contenuto non valido inserito* quando lo stato attivo viene spostato su un altro controllo o quando l'utente fa clic su un pulsante di conferma [OK] o quando l'utente salva il documento o il form.  
  
 Quando si determina lo stato del contenuto non valido, viene visualizzata un'icona all'interno del controllo o semplicemente accanto a esso. La descrizione dell'errore dovrebbe essere visualizzato al passaggio del mouse sull'icona o il controllo. Inoltre, dovrebbe visualizzato un bordo di 1 pixel intorno al controllo che sta creando lo stato non valido.  
  
 ![Specifiche del layout della convalida campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905&03;_LayoutSpecs")  
  
 **Specifiche del layout per la convalida dei campi**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Variazioni accettabili per le icone  
 Esistono innumerevoli casi in cui gli utenti devono essere informati sugli errori di convalida. Se si considera il tipo di controllo e la configurazione dell'interfaccia utente, scegliere la posizione sull'icona della situazione.  
  
 ![Posizioni accettabili per icona](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905&04;_IconLocation")  
  
 **Variazioni accettabili per le posizioni icona convalida campo**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Convalida che richiede un round trip a un server o connessione di rete  
 In alcuni casi, è necessario un round trip al server per verificare il contenuto e sarebbe importante visualizzare lo stato utente, la verifica e gli stati di errore. La figura riportata di seguito viene illustrato un esempio di questo caso e l'interfaccia utente consigliata.  
  
 ![Convalida che prevede un round trip a un server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905&05;_RoundTrip")  
  
 **Convalida che prevede un round trip a un server**  
  
 Spazio disponibile sufficiente a destra del controllo deve essere fornita per supportare la "verifica". e il testo "Riprova".  
  
#### <a name="in-place-warning-text"></a>Testo dell'avviso sul posto  
 Quando c'è spazio disponibile per inserire il messaggio di errore vicino al controllo in uno stato di errore, questo è preferibile utilizzare la descrizione comando da solo.  
  
 ![Avviso sul posto](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905&06;_InPlaceWarning")  
  
 **Testo dell'avviso sul posto**  
  
#### <a name="watermarks"></a>Filigrane  
 Talvolta un intero controllo o finestra è in stato di errore. In questo caso, utilizzare una filigrana per indicare l'errore.  
  
 ![Filigrana](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905&07;_Watermark")  
  
 **Convalida campo filigrana**
