---
title: Modelli di applicazione per Visual Studio | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
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
ms.openlocfilehash: 83b586273dcc60f56ad81fd451adce7860df4033
ms.lasthandoff: 02/22/2017

---
# <a name="application-patterns-for-visual-studio"></a>Modelli di applicazione per Visual Studio
##  <a name="a-namebkmkwindowinteractionsa-window-interactions"></a><a name="BKMK_WindowInteractions"></a>Interazioni di finestra  
  
### <a name="overview"></a>Panoramica  
 I due tipi di finestra principale utilizzati in Visual Studio sono editor di documenti e finestre degli strumenti. Rare, ma possibile, è finestre di dialogo non modale di grandi dimensioni. Anche se questi sono tutti non modali nella shell, i modelli sono sostanzialmente diversi. Questo argomento illustra la differenza tra le finestre di documento, finestre e finestre di dialogo non modale. Vengono descritti i modelli di finestra di dialogo modale in [finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Il confronto dei modelli di utilizzo della finestra  
 **Finestre di documento** sono quasi sempre visualizzate anche all'interno del documento. In questo modo l'editor di documento, una "fase center" per disporre le finestre degli strumenti supplementari intorno.  
  
 Oggetto **finestra degli strumenti** viene spesso visualizzato come una finestra separata di piccole dimensioni, che può essere visibile, nascosto o nascoste automaticamente – compresso contro il bordo dell'IDE. Tuttavia, talvolta sono presentate all'interno del documento e, se si deseleziona la **finestra/ancoraggio** proprietà nella finestra. Il risultato è più ampia, ma anche decisioni di progettazione comune: quando si tenta di integrare in Visual Studio, è necessario decidere se la funzionalità deve essere visualizzata una finestra degli strumenti o una finestra del documento.  
  
 **Le finestre di dialogo non modali** non sono sempre in Visual Studio. In larga misura, essi sono – per definizione, finestre degli strumenti mobili e deve essere implementate come tale. Le finestre di dialogo non modali sono consentiti nei casi in cui la dimensione di una finestra normale degli strumenti ancorata al lato della shell potrebbe essere troppo restrittivo. Sono consentiti anche nei casi in cui l'utente sarebbe probabilmente spostare la finestra di dialogo per un monitor secondario.  
  
 Considerare attentamente il tipo contenitore è necessario. Considerazioni sul modello di utilizzo comune per la progettazione dell'interfaccia utente sono nella tabella seguente.  
  
||Finestra del documento|Finestra degli strumenti|Finestra di dialogo non modo|  
|-|---------------------|-----------------|---------------------|  
|**Posizione**|Sempre posizionato anche all'interno del documento e non ancorare intorno ai bordi dell'IDE. È possibile "estrarre" in modo da spostarla separatamente dalla shell principale.|In genere ancorata ai bordi dell'IDE, ma può essere personalizzato per essere a virgola mobile, nascosta automaticamente (rimozione) o ancorata all'interno del documento anche.|Finestra mobile grandi separato dall'IDE.|  
|**Eseguire il commit del modello**|*Commit ritardato*<br /><br /> Per salvare i dati in un documento, l'utente deve eseguire il comando File/Salva, Salva o Salva tutto. Una finestra del documento include anche il concetto dei dati in esso contenuti venga "scritto" quindi vincolato a uno dei Salva i comandi. Quando si chiude una finestra del documento, tutti i contenuti vengono salvati su disco o perso.|*Commit immediato*<br /><br /> Non vi è alcun Salva modello. Per finestre di strumento di controllo che consentono di modificare un file, il file deve essere aperto nell'editor attivo o nella finestra di progettazione e l'editor o la finestra di progettazione possiede il salvataggio.|*Invio immediato o posticipato commit*<br /><br /> In genere, una finestra di dialogo non modo grandi richiede un'azione per eseguire il commit delle modifiche e consente di un'operazione "Annulla", ovvero il rollback di tutte le modifiche apportate all'interno della sessione di conversazione.  In questo modo una finestra di dialogo non modale da una finestra degli strumenti in finestre degli strumenti dispongono sempre di un modello di commit immediato.|  
|**Visibilità**|*Aprire o creare (file) e Chiudi*<br /><br /> Apertura di finestre di documento avviene tramite l'apertura di un documento esistente o utilizzare un modello per creare un nuovo documento. Non esiste alcun "Apri \<un editor specifico >" comando.|*Mostra e Nascondi*<br /><br /> Finestre degli strumenti a istanza singola possono essere nascoste o visualizzate. Contenuto e gli stati all'interno della finestra degli strumenti persistono se durante la visualizzazione o nascosto. Finestre degli strumenti multi-istanza possono essere chiusa nonché nascoste. Quando una finestra degli strumenti multi-istanza è chiusa, viene eliminato il contenuto e lo stato all'interno della finestra degli strumenti.|*Avviato da un comando*<br /><br /> Finestre di dialogo vengono avviate da un comando basato su attività.|  
|**Istanze**|*Multi-istanza*<br /><br /> Diversi editor possono essere aperti alla stessa ora e modifica diversi file, mentre alcuni editor consentono inoltre lo stesso file da aprire in più di un editor (utilizzando il **finestra > nuova finestra** comando).<br /><br /> Un singolo editor può modificare uno o più file contemporaneamente (progettazione).|*Singolo o più instance*<br /><br /> Contenuto modificato per riflettere contesto (come illustrato nel Visualizzatore proprietà) o push lo stato attivo/contesto ad altre finestre (elenco attività, Esplora soluzioni).<br /><br /> Finestre degli strumenti a istanza singola e a istanza multipla devono essere associate alla finestra del documento attivo, a meno che non vi è un motivo a.|*A istanza singola*|  
|**Esempi**|**Editor di testo**, ad esempio l'editor di codice<br /><br /> **Aree di progettazione**, ad esempio una finestra di progettazione di form o un'area di modellazione<br /><br /> **Controllo di layout simili alle finestre di dialogo**, ad esempio la finestra Progettazione manifesto|Il **Esplora** fornisce una soluzione e i progetti contenuti all'interno della soluzione<br /><br /> Il **Esplora Server** offre una visualizzazione gerarchica di connessioni server e dei dati che l'utente sceglie di aprire la finestra. Apertura di un oggetto dalla gerarchia di database, ad esempio una query, verrà visualizzata una finestra del documento e consente all'utente di modificare la query.<br /><br /> Il **Visualizzatore proprietà** consente di visualizzare le proprietà dell'oggetto selezionato in una finestra del documento o un'altra finestra degli strumenti. Le proprietà vengono presentate in una visualizzazione gerarchica della griglia o in controlli finestra di dialogo complessi e consentono all'utente di impostare i valori per tali proprietà.||  
  
##  <a name="a-namebkmktoolwindowsa-tool-windows"></a><a name="BKMK_ToolWindows"></a>Finestre degli strumenti  
  
### <a name="overview"></a>Panoramica  
 Le finestre supportano le attività dell'utente che si verifica in finestre di documento. Possono essere utilizzati per visualizzare una gerarchia che rappresenta un oggetto radice fondamentali che Visual Studio fornisce e consente di modificare.  
  
 Quando si considera una nuova finestra degli strumenti nell'IDE, gli autori devono:  
  
-   Utilizzo di finestre esistente appropriati e non crearne uno nuovo con funzionalità simili. Nuove finestre devono essere create solo se offrono un "strumento" significativamente diverso o una funzionalità che non può essere integrata in una finestra simile o attivando una finestra esistente a un hub tramite pivot.  
  
-   Utilizzare una barra dei comandi standard, se necessario, nella parte superiore della finestra degli strumenti.  
  
-   Essere coerenti con i modelli presenti in altre finestre degli strumenti per lo spostamento di presentazione e della tastiera di controllo.  
  
-   Essere coerenti con la presentazione di controllo in altre finestre degli strumenti.  
  
-   Finestre di documento specifico devono essere automaticamente visibile quando possibile in modo che vengano visualizzati solo quando viene attivato il documento principale.  
  
-   Verificare che il contenuto della finestra è esplorabile da tastiera (tasti di direzione supporto).  
  
#### <a name="tool-window-states"></a>Stati della finestra degli strumenti  
 Le finestre di Visual Studio hanno diversi stati, alcuni dei quali sono utente attivato (ad esempio, la funzionalità Nascondi automaticamente). Altri Stati, ad esempio automaticamente visibile, consentire le finestre vengono visualizzati in modo corretto e nascondere quando non è necessario. Vi sono cinque stati della finestra degli strumenti in totale.  
  
-   **Ancorata/bloccato** finestre degli strumenti possono essere collegate a uno qualsiasi dei quattro lati dell'area del documento. Questa icona viene visualizzata nella barra del titolo di finestra dello strumento. La finestra degli strumenti può essere ancorata orizzontalmente o verticalmente lungo il bordo della shell e altre finestre degli strumenti e può anche essere collegata a schede.  
  
-   **Nascoste automaticamente** finestre degli strumenti vengono sbloccate. Non è più visualizzata, lasciando una scheda (con il nome della finestra degli strumenti e la relativa icona) sul bordo dell'area del documento può spostare la finestra. La finestra degli strumenti verrà espanso in modo quando un utente viene posizionato sopra la scheda.  
  
-   **Auto-visibile** finestre degli strumenti vengono visualizzati automaticamente quando viene avviata un'altra parte dell'interfaccia utente, ad esempio un editor o lo stato attivo.  
  
-   **A virgola mobile** finestre degli strumenti al passaggio del mouse all'esterno dell'IDE. Ciò è utile per le configurazioni a più monitor.  
  
-   **Documento a schede** finestre degli strumenti ancorabili anche all'interno del documento. Ciò è utile per finestre degli strumenti di grandi dimensioni, ad esempio il Visualizzatore oggetti, che richiedono più ampia di ancoraggio per i bordi del frame, è possibile.  
  
 ![Stati della finestra in Visual Studio degli strumenti](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702&01;_ToolWindowStates")  
  
 **Stati della finestra degli strumenti in Visual Studio**  
  
#### <a name="single-instance-and-multi-instance"></a>A istanza singola e a istanza multipla  
 Finestre degli strumenti sono a istanza singola o multi-istanza. Alcune finestre degli strumenti a istanza singola potrebbero essere associate alla finestra del documento attivo, mentre le finestre degli strumenti multi-istanza potrebbero non. Finestre degli strumenti multi-istanza rispondono al comando finestra finestra/Nuovo creando una nuova istanza della finestra. Nell'immagine seguente viene illustrata una finestra degli strumenti se si abilita il comando nuova finestra quando un'istanza della finestra è attiva:  
  
 ![Comandi di Visual Studio per abilitare la finestra strumento](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702&02;_ToolWindowEnablingCommand")  
  
 **Finestra degli strumenti consente di comando 'Nuova finestra' quando è attiva un'istanza della finestra**  
  
 Finestre degli strumenti a istanza singola possono essere nascoste o visualizzate, mentre le finestre degli strumenti multi-istanza possono essere chiusa nonché nascoste. Tutte le finestre degli strumenti possono essere ancorate, collegata a schede, a virgola mobile o impostato come una finestra figlio di interfaccia a documenti multipli (MDI) (simile a una finestra del documento). Tutte le finestre degli strumenti devono rispondere ai comandi nel menu della finestra Gestione finestra appropriata:  
  
 ![Comandi di gestione di finestra in Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702&03;_WindowManagementControls")  
  
 **Comandi della finestra Gestione nel menu finestra di Visual Studio**  
  
#### <a name="document-specific-tool-windows"></a>Finestre di documento specifico  
 Alcune finestre sono progettate per modificare in base a un determinato tipo di documento. Queste finestre vengono aggiornati continuamente per riflettere funzionalità applicabili alla finestra del documento attivo nell'IDE.  
  
 Sono esempi di finestre degli strumenti il cui contenuto viene modificato per riflettere l'editor selezionato la casella degli strumenti e la struttura del documento. Queste finestre mostrano una filigrana quando attivo che non offre il contesto per la finestra è un editor.  
  
#### <a name="navigable-list-tool-windows"></a>Finestre degli strumenti elenco esplorabile  
 Alcune finestre visualizzare un elenco di elementi esplorabili, che l'utente può interagire con. In questo tipo di finestra, deve esistere sempre commenti e suggerimenti per l'elemento corrente nell'elenco, anche se la finestra è inattiva. L'elenco deve rispondere il **GoToNextLocation** e **GoToPrevLocation** anche la modifica dell'elemento attualmente selezionato nella finestra dei comandi  
  
 Esplora soluzioni e la finestra Risultati ricerca sono esempi di finestre degli strumenti elenco esplorabile.  
  
### <a name="tool-window-types"></a>Tipi di finestra dello strumento  
  
#### <a name="common-tool-windows-and-their-functions"></a>Comuni finestre degli strumenti e le relative funzioni  
  
|Tipo|Finestra degli strumenti|Funzione|  
|----------|-----------------|--------------|  
|**Gerarchia**|Esplora soluzioni|Struttura ad albero gerarchica che visualizza un elenco dei documenti contenuti in elementi di soluzione, progetti e file esterni. La visualizzazione degli elementi all'interno dei progetti è definita dal pacchetto che possiede il tipo di progetto (ad esempio, i tipi basati su riferimenti, basate su directory o in modalità mista).|  
|**Gerarchia**|Visualizzazione classi|Una struttura gerarchica delle classi e i vari elementi nel working set di documenti, indipendenti dei file stessi.|  
|**Gerarchia**|Esplora server|Struttura ad albero gerarchica che visualizza tutte le connessioni server e dei dati nella soluzione.|  
|**Gerarchia**|Struttura documento|La struttura gerarchica del documento attivo.|  
|**Griglia**|Proprietà|Una griglia che visualizza un elenco di proprietà per l'oggetto selezionato, insieme ai controlli di selezione valore per modificare le proprietà.|  
|**Griglia**|Elenco attività|Una griglia che consente all'utente di commenti e attività di creazione, modifica ed eliminazione.|  
|**Contenuto**|?|Una finestra che consente agli utenti l'accesso a diversi metodi di visualizzazione della Guida, da "How Do I?" video ai forum MSDN.|  
|**Contenuto**|Guida dinamica|Una finestra degli strumenti che visualizza i collegamenti agli argomenti applicabili per la selezione corrente della Guida.|  
|**Contenuto**|Visualizzatore oggetti|Una pagina con frame due colonne con un elenco di componenti gerarchico di oggetti nel riquadro a sinistra e l'oggetto proprietà e metodi nella colonna destra.|  
|**Finestra di dialogo**|Trova, ricerca avanzata|Una finestra di dialogo che consente all'utente di ricerca o Trova e Sostituisci nei file diversi all'interno della soluzione.|  
|**Altro**|Casella degli strumenti|La finestra degli strumenti utilizzata per archiviare gli elementi che verranno eliminati su superfici di progettazione, fornendo un'origine di trascinamento coerenza per tutte le finestre di progettazione.|  
|**Altro**|Pagina iniziale|Portale dell'utente a Visual Studio, con accesso al feed di notizie per gli sviluppatori, la Guida di Visual Studio e progetti recenti. Gli utenti possono inoltre creare pagine iniziali personalizzate copiando il file contiene dalla directory del file di programma "Common7\IDE\StartPages\" Visual Studio nella cartella StartPages nella directory di documenti di Visual Studio e quindi modificare manualmente il codice XAML o aprirlo in Visual Studio o un altro codice di editor.|  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Auto||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Controllo immediato||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Output|Finestra di output può essere utilizzata quando si dispone di stato per dichiarare o eventi testuali.|  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Memoria||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Punti di interruzione||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|In esecuzione||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Documenti||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Stack di chiamate||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Variabili locali||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Espressioni di controllo||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Disassembly||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Registri||  
|**Debugger:** un gruppo di windows specifiche attività di debug e monitoraggio delle attività|Thread||  
  
##  <a name="a-namebkmkdocumenteditorconventionsa-document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Convenzioni di editor  
  
### <a name="document-interactions"></a>Interazioni di documento  
 "Documento ben" è lo spazio massimo all'interno dell'IDE e in cui l'utente in genere è stata esaminata la loro attenzione per poter completare le attività, assistite da finestre aggiuntive. Editor di documento rappresentano l'unità fondamentale di lavoro che l'utente viene aperto e salvato all'interno di Visual Studio. Mantenendo un forte senso di selezione collegata a Esplora soluzioni o altra gerarchia active. L'utente deve essere in grado di scegliere una di queste finestre di gerarchia e sapere in cui è contenuto il documento e la relativa relazione per la soluzione, il progetto o un altro oggetto di primo livello forniti da un pacchetto Visual Studio.  
  
 Modifica di documenti richiede un'esperienza utente coerente. Per consentire all'utente di concentrarsi su attività in questione anziché sulla gestione delle finestre e trovare i comandi, scegliere una strategia di visualizzazione documento più adatto alle attività dell'utente per la modifica di tale tipo di documento.  
  
#### <a name="common-interactions-for-the-document-well"></a>Interazioni comuni per il documento e  
  
-   Gestire un modello di interazione coerente in comune **nuovo File** e **Apri** esperienze.  
  
-   Funzionalità correlate nei menu e finestre correlate vengono aggiornate quando si apre la finestra di documento.  
  
-   I comandi di menu sono integrati in modo appropriato nel menu comuni, ad esempio **modificare**, **formato**, e **visualizzazione** menu. Se sono disponibili una notevole quantità di comandi specializzati, quindi un nuovo menu è possibile creare che è visibile solo quando il documento è attivo.  
  
-   Una barra degli strumenti incorporato può essere posizionato nella parte superiore dell'editor. Ciò è preferibile disporre di una barra degli strumenti separato che viene visualizzato all'esterno dell'editor.  
  
-   Mantenere sempre una selezione di Esplora soluzioni o attivo simile finestra gerarchia.  
  
-   Fare doppio clic su un documento in Esplora soluzioni è necessario eseguire la stessa azione **aprire**.  
  
-   Se più di un editor può essere utilizzato in un tipo di documento, l'utente deve essere in grado di eseguire l'override o reimpostare l'azione predefinita in un tipo di documento specificato utilizzando il **Apri con** la finestra di dialogo pulsante destro del mouse sul file e selezionando **Apri con** dal menu di scelta rapida.  
  
-   Non creare anche una procedura guidata in un documento.  
  
### <a name="user-expectations-for-specific-document-types"></a>Aspettative dell'utente per i tipi di documento specifico  
 Esistono diversi tipi base di editor di documento e ognuno presenta una serie di interazioni che siano coerenti con altri utenti dello stesso tipo.  
  
-   **Editor di testo:** editor di codice, i file di log  
  
-   **Area di progettazione:** WPF, Progettazione Windows Form  
  
-   **Editor di stile di finestra di dialogo:** progettazione manifesto, proprietà progetto  
  
-   **Progettazione modelli:** finestra di progettazione del flusso di lavoro, codemap, diagramma dell'architettura, progressione  
  
 Esistono inoltre diversi tipi di non di editor che utilizzano anche il documento. Mentre non modificano documenti stessi, è necessario eseguire interazioni standard per le finestre di documento.  
  
-   **Report:** IntelliTrace report, Hyper-V, report del profiler  
  
-   **Dashboard:** Hub diagnostica  
  
#### <a name="text-based-editors"></a>Editor basato su testo  
  
-   Il documento fa parte del modello di scheda Anteprima, consentendo la visualizzazione in anteprima il documento senza aprirlo.  
  
-   La struttura del documento può essere rappresentata all'interno di una finestra degli strumenti complementare, ad esempio una struttura del documento.  
  
-   IntelliSense (se appropriato) si comporterà in modo coerente con altri editor di codice.  
  
-   I popup o un'interfaccia utente per l'accesso facilitato seguire gli stili e modelli simili per interfaccia utente simile esistente, ad esempio CodeLens.  
  
-   I messaggi riguardanti lo stato del documento verranno visualizzati in un controllo barra informazioni nella parte superiore del documento o nella barra di stato.  
  
-   L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere e colori mediante un **Strumenti > opzioni** pagina della pagina tipi di carattere e colori condivisa o uno specifico per l'editor.  
  
#### <a name="design-surfaces"></a>Aree di progettazione  
  
-   Una finestra di progettazione vuota deve avere una filigrana nell'area di che indica come iniziare.  
  
-   Cambio di visualizzazione meccanismi seguirà modelli esistenti, ad esempio fare doppio clic per aprire un editor di codice o nelle schede all'interno della finestra di documento che consente l'interazione con entrambi i riquadri.  
  
-   Aggiunta di elementi nell'area di progettazione deve essere eseguita tramite la casella degli strumenti, a meno che non è necessaria una finestra degli strumenti molto specifici.  
  
-   Gli elementi nell'area di seguirà un modello di selezione coerente.  
  
-   Barre degli strumenti incorporate contenere comandi non comuni, solo i comandi specifici dei documenti, ad esempio **salvare**.  
  
#### <a name="dialog-style-editors"></a>Editor di stile di finestra di dialogo  
  
-   Controllo del layout deve seguire convenzioni di layout di finestra di dialogo standard.  
  
-   Schede all'interno dell'editor non devono corrispondere l'aspetto delle schede del documento, deve corrispondere a uno dei due stili consentiti scheda interni.  
  
-   Gli utenti devono essere in grado di interagire con i controlli mediante tastiera. Per attivare l'editor e la tabulazione tra controlli o utilizzando i tasti di scelta standard.  
  
-   La finestra di progettazione deve utilizzare la finestra Salva modello comune. Non salva generale o commit deve essere posizionata nell'area di, anche se sono presenti altri pulsanti potrebbero essere appropriato.  
  
#### <a name="model-designers"></a>Progettisti di modelli  
  
-   Una finestra di progettazione vuota deve avere una filigrana nell'area di che indica come iniziare.  
  
-   Aggiunta di elementi nell'area di progettazione deve essere eseguita tramite la casella degli strumenti.  
  
-   Gli elementi nell'area di seguirà un modello di selezione coerente.  
  
-   Barre degli strumenti incorporate contenere comandi non comuni, solo i comandi specifici dei documenti, ad esempio **salvare**.  
  
-   Una legenda può visualizzati nell'area di, indicativo o una filigrana.  
  
-   L'utente deve essere in grado di personalizzare l'aspetto dei colori o tipi di carattere utilizzando un **Strumenti > opzioni** pagina della pagina tipi di carattere e colori condivisa o uno specifico per l'editor.  
  
#### <a name="reports"></a>Report  
  
-   I report vengono in genere solo informazioni e non fanno parte del modello di salvataggio. Tuttavia, possono includere l'interazione, ad esempio collegamenti ad altre informazioni rilevanti o sezioni di espandere e comprimere.  
  
-   La maggior parte dei comandi sulla superficie dovrebbero essere collegamenti ipertestuali, non i pulsanti.  
  
-   Layout deve includere un'intestazione e seguire le linee guida layout di report standard.  
  
#### <a name="dashboards"></a>Dashboard  
  
-   Dashboard non dispongono di un modello di interazione autonomamente, ma servono allo scopo di offrire un'ampia gamma di altri strumenti.  
  
-   Essi non fanno parte del modello di salvataggio.  
  
-   Gli utenti devono essere in grado di interagire con i controlli mediante tastiera, solo l'editor di attivazione e la tabulazione tra controlli o utilizzando i tasti di scelta standard.  
  
##  <a name="a-namebkmkdialogsa-dialogs"></a><a name="BKMK_Dialogs"></a>Finestre di dialogo  
  
### <a name="introduction"></a>Introduzione  
 Finestre di dialogo in Visual Studio deve in genere supportano un unità discreta di lavoro dell'utente e quindi essere chiuse.  
  
 Se si è stabilito che è necessario che una finestra di dialogo, sono disponibili tre opzioni, in ordine di preferenza:  
  
1.  Integrare le funzionalità in una delle finestre di dialogo condivisi in Visual Studio.  
  
2.  Creare il proprio finestra di dialogo tramite un modello di trovare in una finestra di dialogo simile esistente.  
  
3.  Creare una nuova finestra di dialogo, interazione seguente e linee guida di layout.  
  
 In questo argomento viene descritto come scegliere il modello di finestra di dialogo corretto all'interno dei flussi di lavoro di Visual Studio e le convenzioni comuni per la progettazione di finestra di dialogo.  
  
### <a name="themes"></a>Themes  
 Finestre di dialogo in Visual Studio attenersi a uno dei due stili di base:  
  
#### <a name="standard-unthemed"></a>Standard (unthemed)  
 La maggior parte delle finestre di dialogo sono finestre di dialogo utilità standard e devono essere unthemed. Non controlli comuni di re-template o tentare di creare pulsanti "moderni" stilizzati o controlli. Controlli e l'aspetto di chrome seguire [le indicazioni di interazione Desktop di Windows standard per le finestre di dialogo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>Con tema  
 Le finestre di dialogo di specializzazione "firma" potrebbe essere a tema. Le finestre di dialogo con tema hanno un aspetto distinto, che presenta anche alcuni modelli di interazione speciale associati allo stile. Tema della finestra di dialogo solo se soddisfa questi requisiti:  
  
-   La finestra di dialogo è un'esperienza comune che verrà visualizzata e usata spesso o da molti utenti (ad esempio, il **nuovo progetto** finestra di dialogo.  
  
-   La finestra di dialogo contiene gli elementi del marchio prodotto principali (ad esempio, il **le impostazioni dell'Account** finestra di dialogo).  
  
-   La finestra di dialogo viene visualizzata come parte integrante di un flusso più grande che include altre finestre di dialogo con tema (ad esempio, il **Aggiungi servizio connesso** finestra di dialogo).  
  
-   La finestra di dialogo è una parte importante di un'esperienza che svolge un ruolo strategico innalzamento di livello o una versione prodotto di differenziazione.  
  
 Quando si crea una finestra di dialogo con tema, utilizzare i colori di ambiente appropriate e seguire il layout corretto e modelli di interazione. (Vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md))  
  
### <a name="dialog-design"></a>Progettazione di finestra di dialogo  
 Le finestre di dialogo ben progettate considerare i seguenti elementi:  
  
-   L'attività utente supportato  
  
-   Lo stile del testo della finestra, lingua e alla terminologia di  
  
-   Scelta del controllo e le convenzioni dell'interfaccia utente  
  
-   Allineamento specifica e il controllo di layout visivo  
  
-   Accesso da tastiera  
  
#### <a name="content-organization"></a>Organizzazione del contenuto  
 Prendere in considerazione le differenze tra questi tipi di base delle finestre di dialogo:  
  
-   [Le finestre di dialogo semplice](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentare controlli in una singola finestra modale. La presentazione potrebbe includere le variazioni del pattern di controllo complesso, inclusi un selettore di campo o una barra degli strumenti.  
  
-   [A più livelli di finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) vengono utilizzati per eseguire la maggior parte dell'area dello schermo quando un singolo elemento di interfaccia utente è costituito da più gruppi di controlli. I raggruppamenti della finestra di dialogo sono "a più livelli" tramite controlli delle schede, controlli di elenco di navigazione o pulsanti in modo che l'utente può scegliere di raggruppamento per visualizzare in qualsiasi momento.  
  
-   [Procedure guidate](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sono utili per indirizzare l'utente attraverso una sequenza logica di passi verso il completamento di un'attività. Sono disponibili una serie di scelte in pannelli sequenziali, talvolta introdurre diversi flussi di lavoro ("rami") dipendente da una selezione effettuata nel pannello precedente.  
  
####  <a name="a-namebkmksimpledialogsa-simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Finestre di dialogo semplice  
 Finestra di dialogo semplice è una presentazione dei controlli in una singola finestra modale. In questa presentazione potrebbe includere le variazioni del pattern di controllo complesso, ad esempio una selezione di campi. Per le finestre di dialogo semplice, seguire il layout generale standard, nonché qualsiasi layout specifici necessari per i raggruppamenti di controllo complesso.  
  
 ![Finestra di dialogo semplice in Visual Studio](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704&01;_CreateStrongNameKey")  
  
 **Crea chiave con nome sicuro è riportato un esempio di finestra di dialogo semplice in Visual Studio.**  
  
####  <a name="a-namebkmklayereddialogsa-layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Finestre di dialogo a più livelli  
 Le finestre di dialogo a più livelli include schede, dashboard e strutture incorporate. Vengono utilizzati per ottimizzare immobiliare quando sono presenti più gruppi di controlli disponibili in un singolo elemento di interfaccia utente. I raggruppamenti sono disposti in modo che l'utente può scegliere di raggruppamento per visualizzare in qualsiasi momento.  
  
 Nel caso più semplice, il meccanismo per il cambio tra raggruppamenti è un controllo struttura a schede. Sono disponibili diverse alternative. Vedere assegnazione di priorità sulle e livelli per informazioni su come scegliere lo stile più appropriato.  
  
 Il **Strumenti > opzioni** finestra di dialogo è riportato un esempio di finestra di dialogo a più livelli utilizzando una struttura ad albero incorporato:  
  
 ![Finestra di dialogo a più livelli in Visual Studio](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704&02;_ToolsOptions")  
  
 **Strumenti > opzioni è riportato un esempio di finestra di dialogo a più livelli in Visual Studio.**  
  
####  <a name="a-namebkmkwizardsa-wizards"></a><a name="BKMK_Wizards"></a>Procedure guidate  
 Procedure guidate sono utili per indirizzare l'utente attraverso una sequenza di passaggi logica per il completamento di un'attività. Sono disponibili una serie di scelte in pannelli sequenziali e l'utente deve continuare a ogni passaggio prima di procedere al successivo. Una volta sufficienti valori predefiniti sono disponibili, il **fine** pulsante è abilitato.  
  
 Modale procedure guidate vengono utilizzate per le attività che:  
  
-   Contenere diramazioni, in cui sono disponibili percorsi diversi a seconda delle scelte utente  
  
-   Contiene dipendenze tra i passaggi, in cui i passaggi successivi dipendono l'input dell'utente dal passaggio precedente  
  
-   Sono sufficientemente complesse che l'interfaccia utente deve essere utilizzata per spiegare le scelte disponibili e i possibili risultati in ogni passaggio  
  
-   Sono transazionali, che richiedono una serie di passaggi da completare nel suo complesso prima di tutte le modifiche vengono sottoposte a commit  
  
### <a name="common-conventions"></a>Convenzioni comuni  
 Ai fini della progettazione ottimale e funzionalità con le finestre di dialogo, seguire le convenzioni in dimensioni di finestra di dialogo posizione, standard, configurazione di controllo e l'allineamento, dell'interfaccia utente testo, barre del titolo, pulsanti di controllo e di chiavi di accesso.  
  
 Per le istruzioni di layout specifiche, vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Dimensione  
 Finestre di dialogo deve rientrare una risoluzione minima dello schermo 1024 x 768 e dimensioni di finestra di dialogo iniziale non devono superare i 900 x 700 pixel. Finestre di dialogo possono essere ridimensionati, ma non è un requisito.  
  
 Esistono due suggerimenti per le finestre di dialogo ridimensionabile:  
  
1.  Che la dimensione minima è definito per la finestra di dialogo che consente di ottimizzare per il controllo impostare senza troncamenti e regolare per supportare la crescita di localizzazione ragionevole.  
  
2.  Che le dimensioni in scala utente viene mantenuto da una sessione. Ad esempio, se l'utente ridimensiona una finestra di dialogo 150%, un avvio successivo della finestra di dialogo verrà visualizzato in 150%.  
  
#### <a name="position"></a>Posizione  
 Finestre di dialogo deve essere visualizzato centrati all'interno dell'IDE primo avvio. Per le finestre di dialogo non ridimensionabile, non è necessario che l'ultima posizione della finestra di dialogo rese persistenti, pertanto verrà visualizzato al centro su Avvia successive. Per le finestre di dialogo ridimensionabile, la dimensione deve essere mantenuta su Avvia successive. Per i dialoghi ridimensionabili che sono modali, la posizione non devono essere mantenute. La visualizzazione centrata all'interno dell'IDE impedisce la possibilità della finestra di dialogo visualizzata in una posizione non prevedibile o inutilizzabile quando configurazione dello schermo dell'utente è stato modificato. Per i dialoghi non modali che possono essere riposizionati, la posizione dell'utente deve essere mantenuta in successivi avvii, come la finestra di dialogo può essere utilizzato di frequente come parte integrante di un flusso di lavoro più grande.  
  
 Quando le finestre di dialogo deve generare altre finestre di dialogo, deve propagare la finestra di dialogo più in alto a destra e dall'elemento padre in modo che risulti chiaro per l'utente che si è spostati in un altro punto.  
  
#### <a name="modality"></a>Modalità  
 Corso modale significa che gli utenti sono necessari per completare o annullare la finestra di dialogo prima di continuare. Poiché le finestre di dialogo modale bloccare l'utente di interagire con altre parti dell'ambiente, flusso di attività della funzionalità di utilizzo con moderazione possibile. Quando è necessaria un'operazione modale, un numero di finestre di dialogo condivise in che è possibile integrare le funzionalità Visual Studio. Se è necessario creare una nuova finestra di dialogo, seguire il modello di interazione della finestra di dialogo esistente con funzionalità simili.  
  
 Quando gli utenti devono eseguire due attività in una sola volta, ad esempio **trovare** e **sostituire** durante la scrittura di nuovo codice, la finestra di dialogo deve essere non modale in modo che l'utente può passare facilmente tra loro. Visual Studio utilizza in genere le finestre degli strumenti per questo tipo di supporto di editor attività collegata.  
  
#### <a name="control-configuration"></a>Configurazione di controllo  
 Essere coerente con le configurazioni del controllo esistente che eseguire la stessa operazione in Visual Studio.  
  
#### <a name="title-bars"></a>Barre del titolo  
  
-   Il testo nella barra del titolo deve riflettere il nome del comando che l'ha avviata.  
  
-   Nessuna icona deve essere utilizzata nella barra del titolo della finestra. Nei casi in cui il sistema richiede uno, utilizzare il logo di Visual Studio.  
  
-   Finestre di dialogo non è necessario ridurre o ingrandire i pulsanti.  
  
-   I pulsanti della Guida nella barra del titolo sono stati deprecati. Non verranno aggiunte alle nuove finestre di dialogo. Quando sono presenti, avviano un argomento della Guida concettualmente rilevanti per l'attività.  
  
 ![Title bar specifiche per Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704&03;_TitleBarSpecs")  
  
 **Specifiche di linee guida per le barre del titolo nelle finestre di dialogo di Visual Studio.**  
  
#### <a name="control-buttons"></a>Pulsanti di controllo  
 In generale, **OK**/**Annulla**/**Guida** pulsanti devono essere disposte in orizzontale nella parte inferiore destra della finestra di dialogo. La pila verticale alternativa è consentita se una finestra di dialogo è presenti diversi altri pulsanti nella parte inferiore della finestra di dialogo che presenta visual confusione con i pulsanti di controllo.  
  
 ![Controllare le configurazioni di pulsante in Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704&04;_ControlButtonConfig")  
  
 **Configurazioni accettabile per i pulsanti di controllo nelle finestre di dialogo di Visual Studio**  
  
 La finestra di dialogo deve includere un pulsante di controllo predefinito. Per determinare il comando migliore da utilizzare come valore predefinito, scegliere le opzioni seguenti (elencate in ordine di precedenza):  
  
-   Scegliere il comando più sicuro e sicuro come il valore predefinito. Ciò significa che se si sceglie il comando più probabile evitare perdite di dati ed evitare l'accesso al sistema imprevisti.  
  
-   Se sicurezza e la perdita di dati non sono fattori, quindi scegliere il comando predefinito in base alla comodità. Incluso il comando probabilmente come predefinito determinerà un miglioramento del flusso di lavoro dell'utente quando la finestra di dialogo supporta le attività frequenti o ripetitive.  
  
 Evitare di scegliere un'azione distruttiva in modo permanente per il comando predefinito. Se è presente un comando di questo tipo, scegliere un comando sicuro come impostazione predefinita.  
  
#### <a name="access-keys"></a>Chiavi di accesso  
 Non utilizzare i tasti di scelta per **OK**/**Annulla**/**Guida** pulsanti. Per impostazione predefinita, questi pulsanti sono mappati a tasti di scelta rapida:  
  
|Nome del pulsante|Tasti di scelta rapida|  
|-----------------|-----------------------|  
|OK|INVIO|  
|Annulla|ESC|  
|?|F1|  
  
#### <a name="imagery"></a>Immagini  
 Utilizzare le immagini con moderazione nelle finestre di dialogo. Non utilizzare icone grandi nelle finestre di dialogo semplicemente l'utilizzo massimo dello spazio. Utilizzare immagini solo se sono una parte importante di trasmettere il messaggio all'utente, ad esempio le icone di avviso o stato animazioni.  
  
###  <a name="a-namebkmkprioritizingandlayeringa-prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Assegnazione delle priorità e sovrapposizione  
  
#### <a name="prioritizing-your-ui"></a>Assegnazione delle priorità dell'interfaccia utente  
 Potrebbe essere necessario visualizzare alcuni elementi dell'interfaccia utente a forefront e inserire il comportamento più avanzato e in finestre di dialogo Opzioni (inclusi i comandi incomprensibili). Offrire funzionalità comunemente utilizzate a forefront rendendo spazio e da renderlo visibile per impostazione predefinita nell'interfaccia utente con un'etichetta di testo quando viene visualizzata la finestra di dialogo.  
  
#### <a name="layering-your-ui"></a>Disposizione su livelli dell'interfaccia utente  
 Se si è stabilito che una finestra di dialogo è necessario ma le funzionalità correlate da presentare all'utente vanno oltre ciò che può essere visualizzato in una semplice finestra di dialogo, è necessario per l'interfaccia utente di livello. I metodi più comuni di livelli utilizzato Visual Studio sono schede e corridoi o dashboard. In alcuni casi, le aree che è possono espandere e comprimere potrebbero essere appropriate. Interfaccia utente adattiva non è consigliabile in Visual Studio.  
  
 Esistono vantaggi e svantaggi diversi metodi di sovrapposizione tramite i controlli delle schede di interfaccia utente. Esaminare l'elenco seguente per assicurarsi che si sceglie una tecnica di sovrapposizione adatto alla propria situazione.  
  
##### <a name="tabbing"></a>Con il tasto TAB  
  
|Meccanismo di commutazione|Vantaggi e utilizzo appropriato|Utilizzo inappropriato e svantaggi|  
|-------------------------|------------------------------------|-----------------------------------------|  
|Controllo Tab|Raggruppare logicamente finestre di dialogo in gruppi correlati<br /><br /> Utile per meno di cinque, o il numero di schede che rientrano in una riga tra la finestra di dialogo, pagine di controlli correlati nella finestra di dialogo<br /><br /> Scheda etichette devono essere breve: una o due parole in grado di identificare facilmente il contenuto<br /><br /> Uno stile di finestra di dialogo comuni di sistema<br /><br /> Esempio: **Esplora File > le proprietà degli elementi**|L'impostazione di etichette descrittive brevi può risultare difficile<br /><br /> In genere non è sufficientemente scalabile oltre cinque schede in una finestra di dialogo<br /><br /> Non appropriato se si dispone di un numero eccessivo di schede per una riga. utilizzare una tecnica di sovrapposizione alternativo<br /><br /> Non estendibile|  
|Navigazione nella barra laterale|Dispositivo di commutazione semplice che può contenere altre categorie di schede<br /><br /> Elenco semplice di categorie (alcuna gerarchia)<br /><br /> Estendibile<br /><br /> Esempio: **personalizzare … > Aggiungi comando**|Non è un utilizzo corretto di spazio orizzontale se sono presenti meno di tre gruppi<br /><br /> Attività potrebbe essere più adatti per un elenco a discesa|  
|Controllo Tree|Consente di numero illimitato di categorie<br /><br /> Consente di raggruppamento e/o gerarchia di categorie<br /><br /> Estendibile<br /><br /> Esempio: **Strumenti > opzioni**|Gerarchie molto annidate possono causare un numero eccessivo di scorrimento orizzontale<br /><br /> Visual Studio include un eccesso di visualizzazioni ad albero|  
|Wizard|Facilita il completamento dell'attività tramite le quali passaggi sequenziali, basato su attività. La procedura guidata rappresenta un'attività di alto livello e i singoli pannelli rappresentano sottoattività necessarie per eseguire l'attività complessiva.<br /><br /> Utile quando l'attività attraversa i limiti dell'interfaccia utente, come quando l'utente sarebbe altrimenti necessario utilizzare più editor e finestre per completare l'attività<br /><br /> Utile quando l'attività richiede l'esecuzione del branching<br /><br /> Utile quando l'attività contiene dipendenze tra i passaggi<br /><br /> Risulta utile quando più attività simile con fork di una decisione possono essere visualizzate in una finestra di dialogo per ridurre il numero di diverse finestre di dialogo simile.|Per qualsiasi attività che non richiede un flusso di lavoro sequenza<br /><br /> Gli utenti possono diventare sovraccarico e confusi da una procedura guidata con un numero eccessivo di passaggi<br /><br /> Procedure guidate non dispongono implicitamente area dello schermo|  
  
##### <a name="hallways-or-dashboards"></a>Corridoi o dashboard  
 Corridoi e i dashboard sono pannelli che fungono da avvio punti alle altre finestre di dialogo e finestre o finestre di dialogo. Ben progettata "corridoio" superfici immediatamente solo i più comuni opzioni, comandi e le impostazioni, consentendo all'utente di eseguire rapidamente attività comuni. Come un corridoio reali fornisce porte per accedere alle chat su cui si basano, in questo caso l'interfaccia utente meno comuni verrà raccolti in "locali" (spesso altre finestre di dialogo) di funzioni correlate che è possibile accedere da corridoio principale.  
  
 In alternativa, un'interfaccia utente che offre tutte le funzionalità disponibili in un'unica raccolta piuttosto che le funzionalità meno comuni in posizioni separate di refactoring è semplicemente un dashboard.  
  
 ![Concetto hallway in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704&08;_Hallway")  
  
 **Concetto hallway per esporre l'interfaccia utente aggiuntiva in Outlook**  
  
##### <a name="adaptive-ui"></a>Interfaccia utente adattiva  
 Mostrare o nascondere l'interfaccia utente in base all'utilizzo o Self-segnalati esperienza di un utente è un altro modo di presentazione dell'interfaccia utente necessaria nascondendo altre parti. Questa operazione è sconsigliata in Visual Studio come gli algoritmi per decidere quando mostrare o nascondere l'interfaccia utente possono essere difficili, e le regole saranno sempre errate per alcuni set di case.  
  
##  <a name="a-namebkmkprojectsa-projects"></a><a name="BKMK_Projects"></a>Progetti  
  
### <a name="projects-in-the-solution-explorer"></a>Progetti in Esplora soluzioni  
 La maggior parte dei progetti sono classificati come basato su riferimenti, basate su directory o misto. I tre tipi di progetti sono supportati contemporaneamente in Esplora soluzioni. La radice dell'esperienza utente in utilizzo di progetti viene eseguita all'interno di questa finestra. Sebbene i nodi di progetto diversi progetti di tipo modalità mista, directory o riferimento, esiste un modello di interazione comune che deve essere applicato a un punto di partenza prima divergente in modelli di progetto specifico utente.  
  
 Deve sempre essere progetti:  
  
-   Supporta la possibilità di aggiungere le cartelle dei progetti per organizzare il contenuto di progetto  
  
-   Gestire un modello coerente per la persistenza del progetto  
  
 Progetti devono anche gestire modelli di interazione coerente per:  
  
-   Rimozione di elementi di progetto  
  
-   Salvataggio di documenti  
  
-   Modifica delle proprietà di progetto  
  
-   Modifica del progetto in una visualizzazione alternativa  
  
-   Operazioni di trascinamento e rilascio  
  
### <a name="drag-and-drop-interaction-model"></a>Modello di interazione di trascinamento e rilascio  
 Progetti di se stesso come base di riferimento (in grado di rendere persistente solo i riferimenti agli elementi di progetto nel servizio di archiviazione), classificare in genere basate su directory (in grado di mantenere solo elementi di progetto fisicamente archiviato all'interno di una gerarchia del progetto), o mista (in grado di mantenere i riferimenti o gli elementi fisici). L'IDE supporta tutti e tre i tipi di progetti contemporaneamente all'interno di **Esplora**.  
  
 Da una prospettiva di trascinamento e rilascio, applicare le caratteristiche seguenti per ogni tipo di progetto all'interno di **Esplora**:  
  
-   **Progetto basato sul riferimento:** il punto principale è che il progetto sta trascinando intorno a un riferimento a un elemento nell'archivio. Quando un progetto basato sul riferimento funge da origine per un'operazione di spostamento, è necessario rimuovere solo il riferimento all'elemento dal progetto. L'elemento non deve effettivamente eliminato dal disco rigido. Quando un progetto basato sul riferimento costituisce una destinazione per un'operazione di spostamento (o copia), è necessario aggiungere un riferimento all'elemento di origine originale senza creare una copia privata dell'elemento.  
  
-   **Progetto basato su directory:** dal punto di vista, trascinamento e rilascio sta trascinando il progetto per l'elemento fisico anziché un riferimento. Quando un progetto basato su directory funge da origine per un'operazione di spostamento, deve finire eliminazione dell'elemento fisico dal disco rigido, nonché di rimuoverlo dal progetto. Quando un progetto basato su directory costituisce una destinazione per un'operazione di spostamento (o copia), deve creare una copia dell'elemento di origine nella posizione di destinazione.  
  
-   **Progetto di destinazione mista:** dal punto di vista, trascinamento e il comportamento di questo tipo di progetto è basato sulla natura dell'elemento viene trascinato (un riferimento a un elemento nello spazio di memorizzazione) o l'elemento stesso. Il comportamento corretto per i riferimenti e gli elementi fisici sono descritti in precedenza.  
  
 Se fossero un solo tipo di progetto nel **Esplora**, operazioni di trascinamento e rilascio sarà semplice. Poiché ogni sistema del progetto ha la possibilità di definire il comportamento di trascinamento e rilascio, alcune linee guida (in base al comportamento di trascinamento e rilascio di Windows Explorer) da seguire per garantire un'esperienza utente prevedibile:  
  
-   Invariato un'operazione di trascinamento **Esplora** (quando Ctrl né MAIUSC vengono mantenuti verso il basso) dovrebbe tradursi in un'operazione di spostamento.  
  
-   Operazione di trascinamento MAIUSC dovrebbe restituire anche un'operazione di spostamento.  
  
-   Operazione di trascinamento CTRL dovrebbe restituire un'operazione di copia.  
  
-   Sistemi di progetto basato sul riferimento e mista supportano la nozione di aggiunta di un collegamento (o riferimento) all'elemento di origine. Quando questi progetti sono la destinazione di un'operazione di trascinamento e rilascio (quando **Ctrl + Maiusc** si tiene premuto), dovrebbe restituire un riferimento all'elemento da aggiungere al progetto  
  
 Non tutte le operazioni di trascinamento e rilascio sono intelligente tra le combinazioni di progetti basati su riferimenti, basate su directory e misti. In particolare, risulta problematico di consentire un'operazione di spostamento tra un progetto di origine basato su directory e un progetto di destinazione basato sul riferimento perché dispone di un progetto basato su directory di origine eliminare l'elemento di origine al termine dello spostamento. Il progetto di destinazione basato sul riferimento sarebbe quindi necessario con un riferimento a un elemento eliminato.  
  
 È inoltre fuorviante di consentire un'operazione di copia tra questi tipi di progetti perché il progetto di destinazione basato sul riferimento non deve effettuare una copia indipendente dell'elemento di origine. Analogamente, Ctrl + MAIUSC il trascinamento di un progetto di destinazione basate su directory non è consentita perché un progetto basato su directory è in grado di mantenere i riferimenti. Nei casi in cui non è supportato l'operazione di trascinamento e rilascio, l'IDE deve impedire l'eliminazione e visualizzare all'utente, il cursore di non rilascio (mostrato nella seguente tabella puntatore).  
  
 Per implementare correttamente il comportamento di trascinamento e rilascio, il progetto di origine dell'operazione di trascinamento deve comunicare la sua natura (ad esempio, è basata su riferimento o directory?) al progetto di destinazione. Queste informazioni sono indicate per il formato degli Appunti che viene offerto dall'origine. Come origine di trascinamento (un'operazione di copia negli Appunti) un progetto deve offrire uno **CF_VSREFPROJECTITEM**S o **CF_VSSTGPROJECTITEMS** , rispettivamente, a seconda se il progetto è basato su directory o riferimento. Questi due formati hanno lo stesso contenuto di dati, che è simile a Windows **CF_HDROP** formattare ad eccezione del fatto che gli elenchi di stringhe, anziché essere nomi di file, sono un double -**NULL** terminato l'elenco di **Projref** stringhe (come restituito da **IVsSolution::GetProjrefOfItem** o **:: GetProjrefOfProject** come appropriato).  
  
 Come destinazione di un rilascio (o l'operazione Incolla negli Appunti), un progetto deve accettare entrambi **CF_VSREFPROJECTITEMS** e **CF_VSSTGPROJECTITEMS**, anche se la gestione dell'operazione di trascinamento e rilascio esatto varia a seconda della natura del progetto di destinazione e il progetto di origine. Il progetto di origine dichiara la sua natura, che offre **CF_VSREFPROJECTITEMS** o **CF_VSSTGPROJECTITEMS**. La destinazione del trascinamento riconosce propria natura e è pertanto le informazioni necessarie per prendere decisioni a se un spostamento, copia o collegamento deve essere eseguito. L'utente modifica anche l'operazione di trascinamento e deve essere eseguita premendo Ctrl, MAIUSC, o sia Ctrl e MAIUSC. È importante per la destinazione di rilascio indicare in modo corretto l'operazione verrà eseguita in anticipo in relativo **DragEnter** e **con trascinamento** metodi. Il **Esplora** automaticamente sa se il progetto di origine e il progetto di destinazione sono nello stesso progetto.  
  
 Il trascinamento degli elementi di progetto tra più istanze di Visual Studio (ad esempio, da un'istanza di devenv.exe a un'altra) non è supportato. Il **Esplora** direttamente disabilita questo.  
  
 L'utente deve essere sempre in grado di determinare l'effetto di un'operazione di trascinamento e selezionando un elemento, trascinarlo nel percorso di destinazione e osservare che i seguenti puntatori del mouse viene visualizzato prima del rilascio dell'elemento:  
  
|Puntatore del mouse|Comando|Descrizione|  
|-------------------|-------------|-----------------|  
|![Icona di "Nessun trascinamento" del mouse](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706&01;_MouseNoDrop")|Nessun trascinamento|Impossibile eliminare l'elemento nel percorso specificato.|  
|![Icona "copia" del mouse](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706&02;_MouseCopy")|Copia|Elemento verrà copiato nel percorso di destinazione.|  
|![Spostamento del mouse"" icona](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706&03;_MouseMove")|Move|Elemento verrà spostato nel percorso di destinazione.|  
|![Icona "Aggiungi riferimento" del mouse](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706&04;_MouseAddRef")|Aggiungi riferimento|Verrà aggiunto un riferimento all'elemento selezionato nel percorso di destinazione.|  
  
#### <a name="reference-based-projects"></a>Progetti basati su riferimento  
 Nella tabella seguente sono riepilogate le operazioni di trascinamento e rilascio (nonché Taglia/Copia/Incolla) che devono essere eseguite in base alla natura delle chiavi di elemento e il modificatore di origine selezionato per i progetti di destinazione in base a cui fa riferimento:  
  
|||Elemento di origine: / collegamento di riferimento|Elemento di origine: fisico del file o un elemento system (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Nessun modificatore|Azione|Move|Collegamento|  
|Nessun modificatore|destinazione|Aggiunge i riferimenti all'elemento originale|Aggiunge i riferimenti all'elemento originale|  
|Nessun modificatore|Origine|Elimina riferimento all'elemento originale|Mantiene l'elemento originale|  
|Nessun modificatore|Risultato|**DROPEFFECT_MOVE** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|**DROPEFFECT_LINK** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|  
|Maiusc + trascinamento|Azione|Move|Nessun trascinamento|  
|Maiusc + trascinamento|destinazione|Aggiunge i riferimenti all'elemento originale|Nessun trascinamento|  
|Maiusc + trascinamento|Origine|Elimina riferimento all'elemento originale|Nessun trascinamento|  
|Maiusc + trascinamento|Risultato|**DROPEFFECT_MOVE** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|Nessun trascinamento|  
|CTRL + trascinamento|Azione|Copia|Nessun trascinamento|  
|CTRL + trascinamento|destinazione|Aggiunge i riferimenti all'elemento originale|Nessun trascinamento|  
|CTRL + trascinamento|Origine|Mantiene il riferimento all'elemento originale|Nessun trascinamento|  
|CTRL + trascinamento|Risultato|**DROPEFFECT_COPY** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|Nessun trascinamento|  
|CTRL + MAIUSC + trascinamento|Azione|Collegamento|Collegamento|  
|CTRL + MAIUSC + trascinamento|destinazione|Aggiunge i riferimenti all'elemento originale|Aggiunge i riferimenti all'elemento originale|  
|CTRL + MAIUSC + trascinamento|Origine|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|  
|CTRL + MAIUSC + trascinamento|Risultato|**DROPEFFECT_LINK** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|**DROPEFFECT_LINK** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|  
|CTRL + MAIUSC + trascinamento|Nota|Come comportamento di trascinamento e rilascio per tasti di scelta rapida in Esplora risorse.||  
|Taglia e Incolla|Azione|Move|Collegamento|  
|Taglia e Incolla|destinazione|Aggiunge i riferimenti all'elemento originale|Aggiunge i riferimenti all'elemento originale|  
|Taglia e Incolla|Origine|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|  
|Taglia e Incolla|Risultato|Elemento rimane nella posizione originale nel servizio di archiviazione|Elemento rimane nella posizione originale nel servizio di archiviazione|  
|Copiare e incollare|Azione|Copia|Collegamento|  
|Copiare e incollare|Origine|Aggiunge i riferimenti all'elemento originale|Aggiunge i riferimenti all'elemento originale|  
|Copiare e incollare|Risultato|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|  
|Copiare e incollare|Azione|Elemento rimane nella posizione originale nel servizio di archiviazione|Elemento rimane nella posizione originale nel servizio di archiviazione|  
  
#### <a name="directory-based-projects"></a>Progetti basati su directory  
 Nella tabella seguente sono riepilogate le operazioni di trascinamento e rilascio (nonché Taglia/Copia/Incolla) che devono essere eseguite in base alla natura delle chiavi di elemento e il modificatore di origine selezionato per i progetti basati su directory di destinazione:  
  
|||Elemento di origine: / collegamento di riferimento|Elemento di origine: fisico del file o un elemento system (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Nessun modificatore|Azione|Move|Move|  
|Nessun modificatore|destinazione|Elemento di copie da percorso di destinazione|Elemento di copie da percorso di destinazione|  
|Nessun modificatore|Origine|Elimina riferimento all'elemento originale|Elimina riferimento all'elemento originale|  
|Nessun modificatore|Risultato|**SPOSTARE DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|**SPOSTARE DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|  
|Maiusc + trascinamento|Azione|Move|Move|  
|Maiusc + trascinamento|destinazione|Elemento di copie da percorso di destinazione|Elemento di copie da percorso di destinazione|  
|Maiusc + trascinamento|Origine|Elimina riferimento all'elemento originale|Elimina elemento dal percorso originale|  
|Maiusc + trascinamento|Risultato|**SPOSTARE DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|**SPOSTARE DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|  
|CTRL + trascinamento|Azione|Copia|Copia|  
|CTRL + trascinamento|destinazione|Elemento di copie da percorso di destinazione|Elemento di copie da percorso di destinazione|  
|CTRL + trascinamento|Origine|Mantiene il riferimento all'elemento originale|Mantiene il riferimento all'elemento originale|  
|CTRL + trascinamento|Risultato|**Copia DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|**Copia DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|  
|CTRL + MAIUSC + trascinamento||Nessun trascinamento|Nessun trascinamento|  
|Taglia e Incolla|Azione|Move|Move|  
|Taglia e Incolla|destinazione|Elemento di copie da percorso di destinazione|Elemento di copie da percorso di destinazione|  
|Taglia e Incolla|Origine|Elimina riferimento all'elemento originale|Elimina elemento dal percorso originale|  
|Taglia e Incolla|Risultato|Elemento rimane nella posizione originale nel servizio di archiviazione|Elemento viene eliminato dal percorso originale di archiviazione|  
|Copiare e incollare|Azione|Copia|Copia|  
|Copiare e incollare|destinazione|Aggiunge i riferimenti all'elemento originale|Elemento di copie da percorso di destinazione|  
|Copiare e incollare|Origine|Mantiene l'elemento originale|Mantiene l'elemento originale|  
|Copiare e incollare|Risultato|Elemento rimane nella posizione originale nel servizio di archiviazione|Elemento rimane nell'archivio di aggiuntivi percorso originale|  
  
#### <a name="mixed-target-projects"></a>Progetti di destinazione misto  
 Nella tabella seguente sono riepilogate le operazioni di trascinamento e rilascio (nonché Taglia/Copia/Incolla) che devono essere eseguite in base alla natura delle chiavi di elemento e il modificatore di origine selezionato per i progetti di destinazione mista:  
  
|||Elemento di origine: / collegamento di riferimento|Elemento di origine: fisico del file o un elemento system (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Nessun modificatore|Azione|Move|Move|  
|Nessun modificatore|destinazione|Aggiunge i riferimenti all'elemento originale|Elemento di copie da percorso di destinazione|  
|Nessun modificatore|Origine|Elimina riferimento all'elemento originale|Elimina riferimento all'elemento originale|  
|Nessun modificatore|Risultato|**SPOSTARE DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|**SPOSTARE DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento viene eliminato dal percorso originale di archiviazione|  
|Maiusc + trascinamento|Azione|Move|Move|  
|Maiusc + trascinamento|destinazione|Aggiunge i riferimenti all'elemento originale|Elemento di copie da percorso di destinazione|  
|Maiusc + trascinamento|Origine|Elimina riferimento all'elemento originale|Elimina elemento dal percorso originale|  
|Maiusc + trascinamento|Risultato|**SPOSTARE DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|**SPOSTARE DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento viene eliminato dal percorso originale di archiviazione|  
|CTRL + trascinamento|Azione|Copia|Copia|  
|CTRL + trascinamento|destinazione|Aggiunge i riferimenti all'elemento originale|Elemento di copie da percorso di destinazione|  
|CTRL + trascinamento|Origine|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|  
|CTRL + trascinamento|Risultato|**Copia DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|**Copia DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|  
|CTRL + MAIUSC + trascinamento|Azione|Collegamento|Collegamento|  
|CTRL + MAIUSC + trascinamento|destinazione|Aggiunge i riferimenti all'elemento originale|Aggiunge i riferimenti all'elemento di origine originale|  
|CTRL + MAIUSC + trascinamento|Origine|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|  
|CTRL + MAIUSC + trascinamento|Risultato|**COLLEGAMENTO DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|**COLLEGAMENTO DROPEFFECT_** viene restituito come azione da **:: Drop** e l'elemento rimane nella posizione originale nel servizio di archiviazione|  
|Taglia e Incolla|Azione|Move|Move|  
|Taglia e Incolla|destinazione|Elemento di copie da percorso di destinazione|Elemento di copie da percorso di destinazione|  
|Taglia e Incolla|Origine|Elimina riferimento all'elemento originale|Elimina elemento dal percorso originale|  
|Taglia e Incolla|Risultato|Elemento rimane nella posizione originale nel servizio di archiviazione|Elemento viene eliminato dal percorso originale di archiviazione|  
|Copiare e incollare|Azione|Copia|Copia|  
|Copiare e incollare|destinazione|Aggiunge i riferimenti all'elemento originale|Elemento di copie da percorso di destinazione|  
|Copiare e incollare|Origine|Mantiene l'elemento originale|Mantiene l'elemento originale|  
|Copiare e incollare|Risultato|Elemento rimane nella posizione originale nel servizio di archiviazione|Elemento rimane nella posizione originale nel servizio di archiviazione|  
  
 Questi dettagli devono prendere in considerazione quando si implementa il trascinamento nel **Esplora**:  
  
-   Progettazione per più scenari di selezione.  
  
-   I nomi di file (percorso completo) devono essere univoci per il progetto di destinazione o l'eliminazione non è consentita.  
  
-   I nomi delle cartelle deve essere univoci (tra maiuscole e minuscole) a livello di essi vengono eliminati.  
  
-   Vi sono differenze di comportamento tra i file che sono aperti o chiusi in fase di trascinamento (non indicata negli scenari precedenti).  
  
-   File di primo livello si comportano in modo leggermente diverso rispetto ai file nelle cartelle.  
  
 Un altro problema da considerare è la modalità di gestione di operazioni di spostamento di elementi che dispongono di editor o aprire finestre di progettazione. Il comportamento previsto è come indicato di seguito (si applica a tutti i tipi di progetto):  
  
1.  Se l'editor o finestra di progettazione aperta non dispone di eventuali modifiche non salvate, quindi la finestra dell'editor di progettazione deve essere automaticamente chiuso.  
  
2.  Se l'editor o di progettazione aprire dispone le modifiche non salvate, l'origine dell'operazione di trascinamento deve attendere per l'eliminazione e quindi chiedere all'utente di salvare le modifiche non salvate nei documenti aperti prima di chiudere la finestra con un messaggio analogo al seguente:  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
 In questo modo l'utente la possibilità di salvare lavoro in corso prima che la destinazione effettui la copia. Un nuovo metodo **IVsHierarchyDropDataSource2::OnBeforeDropNotify** è stato aggiunto per abilitare questo tipo di gestione.  
  
 La destinazione copierà quindi lo stato dell'elemento come se fosse nel servizio di archiviazione (senza includere le modifiche non salvate nell'editor se l'utente sceglie **n**). Dopo la destinazione è stata completata la copia (in **IVsHierarchyDropDataSource::Drop**), l'origine è data la possibilità di completare la parte di eliminazione dell'operazione di spostamento (in **IVsHierarchyDropDataSource::OnDropNotify**).  
  
 Deve essere lasciato aperto un editor con le modifiche non salvate. Per questi documenti con le modifiche non salvate, ciò significa che la fase di copia dell'operazione di spostamento verrà eseguita ma la parte di eliminazione verrà interrotta. In uno scenario di selezione più quando l'utente sceglie **n**, tali documenti con le modifiche non salvate non devono essere chiuso o rimosso, ma quelli senza modifiche non salvate deve essere chiuso e rimosso.
