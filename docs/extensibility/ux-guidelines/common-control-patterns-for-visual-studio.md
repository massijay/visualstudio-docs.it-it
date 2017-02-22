---
title: "Pattern di controllo comune per Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Pattern di controllo comune per Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> Controlli comuni  
  
### Panoramica  
 Controlli comuni costituiscono la maggior parte dell'interfaccia utente in Visual Studio. Controlli più comuni utilizzati nell'interfaccia di Visual Studio devono seguire il [linee guida per l'interazione di Desktop Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). In questo documento è specifico di Visual Studio e vengono illustrati i dettagli che aumentano le linee guida di Windows o situazioni particolari.  
  
#### Controlli comuni in questo argomento  
  
-   [Barre di scorrimento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Campi di input](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Elenchi a discesa e caselle combinate](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Caselle di controllo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Pulsanti di opzione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Frame di gruppo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Controlli testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Visualizzazioni ad albero](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### Stile di visualizzazione  
 La prima cosa da considerare durante i controlli di stile è se i controlli verranno utilizzati nell'interfaccia utente a tema. Controlli dell'interfaccia utente standard sono non tema dell'interfaccia utente e deve seguire [stile Desktop di Windows normale](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), vale a dire che non sono basati su modelli re e verrà visualizzato il relativo aspetto del controllo predefinito.  
  
-   **Le finestre di dialogo standard \(utilità\):** non temi. Eseguire l'operazione non re\-template. Utilizza impostazioni predefinite di stile di controllo di base.  
  
-   **Strumento windows, editor di documenti, aree di progettazione e finestre di dialogo con tema:** utilizzare aspetto con tema specifico tramite il servizio di colore.  
  
###  <a name="BKMK_Scrollbars"></a> Barre di scorrimento  
 Barre di scorrimento devono seguire [modelli comuni di interazione per le barre di scorrimento di Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) a meno che non sono sono dotati di informazioni sul contenuto, ad esempio nell'editor di codice.  
  
###  <a name="BKMK_InputFields"></a> Campi di input  
 Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per le caselle di testo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### Stile di visualizzazione  
  
-   I campi di input non devono essere concepiti nelle finestre di dialogo utilità. Utilizzare lo stile di base intrinseco al controllo.  
  
-   I campi di input con tema utilizzare solo nelle finestre di dialogo temi e le finestre degli strumenti.  
  
#### Interazioni specializzate  
  
-   Campi di sola lettura avrà uno sfondo grigio \(disattivato\) ma di primo piano predefinito \(attivo\).  
  
-   Necessario campi devono avere **\< necessari \>** come filigrane al loro interno. Non è necessario modificare il colore dello sfondo tranne in rari casi.  
  
-   Convalida di errore: vedere [Le notifiche e l'avanzamento di Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   I campi di input devono essere dimensionati per adattarle al contenuto, non alla larghezza della finestra in cui vengono visualizzati né arbitrariamente corrisponde alla lunghezza di un campo lungo, ad esempio un percorso. Lunghezza potrebbe essere un'indicazione all'utente di limitazioni per quanto riguarda il numero di caratteri consentito nel campo.  
  
     ![Incorrect input field control width](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707\-01\_IncorrectInputFieldControl")   
     **Lunghezza del campo di input non corretto: è improbabile che il nome sarà questa lunghezza.**  
  
     ![Correct input field control width](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707\-02\_CorrectInputFieldControl")   
     **Correggere la lunghezza del campo di input: il campo di input è una ragionevole larghezza per il contenuto previsto.**  
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Elenchi a discesa e caselle combinate  
 Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per elenchi a discesa e caselle combinate](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### Stile di visualizzazione  
  
-   Nelle finestre di dialogo utilità, eseguire non re\-modello di controllo. Utilizzare lo stile di base intrinseco al controllo.  
  
-   Seguire i temi standard per i controlli a tema dell'interfaccia utente, le caselle combinate e elenchi a discesa.  
  
#### Layout  
 Elenchi a discesa e caselle combinate deve essere dimensionati per adattarle al contenuto, non alla larghezza della finestra in cui vengono visualizzati né arbitrariamente corrisponde alla lunghezza di un campo lungo, ad esempio un percorso.  
  
 ![Incorrect drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707\-03\_IncorrectDropDownLayout")  
  
 **Lunghezza del campo non corretto per un controllo elenco a discesa**  
  
 ![Correct drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707\-04\_CorrectDropDownLayout")  
  
 **Lunghezza del campo corretto per un controllo elenco a discesa**  
  
###  <a name="BKMK_CheckBoxes"></a> Caselle di controllo  
 Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per le caselle di controllo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### Stile di visualizzazione  
  
-   Nelle finestre di dialogo utilità, eseguire non re\-modello di controllo. Utilizzare lo stile di base intrinseco al controllo.  
  
-   Nell'interfaccia utente di temi, caselle di controllo seguire i temi standard per i controlli.  
  
#### Interazioni specializzate  
  
-   L'interazione con una casella di controllo non deve mai visualizzata una finestra di dialogo o passare a un'altra area.  
  
-   Allinea le caselle di controllo con la linea di base della prima riga di testo.  
  
     ![Incorrect check box alignment](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707\-05\_IncorrectCheckBoxAlign")   
     **Allineamento non corretto della casella di controllo: casella di controllo è allineata al centro il testo.**  
  
     ![Correct check box alignment](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707\-06\_CorrectCheckBoxAlign")   
     **Correggere l'allineamento della casella di controllo: casella di controllo è allineata alla linea di base della prima riga di testo.**  
  
###  <a name="BKMK_RadioButtons"></a> Pulsanti di opzione  
 Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per i pulsanti di opzione](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### Stile di visualizzazione  
 Nelle finestre di dialogo utilità, eseguire non pulsanti di opzione di stile. Utilizzare lo stile di base intrinseco al controllo.  
  
#### Interazioni specializzate  
 Non è necessario utilizzare una cornice di gruppo per racchiudere le scelte di opzione.  
  
###  <a name="BKMK_GroupFrames"></a> Frame di gruppo  
 Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per frame gruppo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### Stile di visualizzazione  
 Nelle finestre di dialogo utilità, eseguire non frame di gruppo di stile. Utilizzare lo stile di base intrinseco al controllo.  
  
#### Layout  
  
-   Non è necessario utilizzare una cornice di gruppo per racchiudere le scelte di opzione, a meno che non è necessario mantenere la distinzione di gruppo in un layout limitato.  
  
-   Non utilizzare mai una cornice di gruppo per un singolo controllo.  
  
-   Talvolta è possibile utilizzare una regola orizzontale anziché un contenitore di frame di gruppo.  
  
##  <a name="BKMK_TextControls"></a> Controlli testo  
  
### Etichette  
  
#### Stato attivo etichetta  
  
##### Utilità \(standard\) le finestre di dialogo\)  
  
-   In generale, seguire le linee guida di Windows Desktop per etichette del controllo.  
  
-   Nelle finestre di dialogo utilità, etichette risulterà non in grassetto, il colore del carattere e testo di ambiente standard. Vedere [I tipi di carattere e la formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
-   Puntini di sospensione è opportuno seguire sempre le etichette.  
  
##### Firma \(tema\) le finestre di dialogo\)  
 Controlli etichetta possono essere grigio chiaro o grassetto.  
  
#### Stato disabilitato etichetta  
 Le etichette devono riflettere l'aspetto del controllo che cui sono associati. Ad esempio, se il controllo associato è disabilitato, l'etichetta verrà visualizzato grigio e disabilitati. Questo in genere viene eseguito dal sistema operativo e richiede un trattamento speciale.  
  
#### Etichette dinamiche  
 Modifica di etichette dinamico in base alla selezione corrente. Laddove possibile, utilizzare le etichette dinamiche nei layout master\-Details per consentire all'utente di comprendere che le informazioni visualizzate sono rilevanti per una specifica selezione e le informazioni non generali.  
  
 ![Dynamic label used with dynamic content](../../extensibility/ux-guidelines/media/070702-01_dynamiclabel.png "070702\-01\_DynamicLabel")  
  
 **Esempio di un'etichetta dinamica usata con contenuto dinamico**  
  
#### Testo esplicativo  
 Alcuni elementi dell'interfaccia possono beneficiare del testo esplicativo per consentire all'utente di comprendere lo scopo dell'interfaccia utente o per indicare l'azione da intraprendere.  
  
-   Testo esplicativo è più comune nella parte superiore delle finestre di dialogo, ma può essere visualizzati in altre aree per dare istruzioni a un raggruppamento di controllo complesso.  
  
-   Testo esplicativo non è interattivo, ma può contenere collegamenti ipertestuali agli argomenti della Guida.  
  
-   Utilizzare testo esplicativo sporadicamente e solo quando necessario.  
  
##### Formattazione  
 Testo esplicativo deve essere di tipo di carattere ambiente, il testo di controllo standard \(non temi\). Vedere [I tipi di carattere e la formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
 Per ulteriori informazioni sulla scrittura di testo esplicativo, vedere [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
 ![Instructional text formatting](../../extensibility/ux-guidelines/media/070702-02_instructionaltextformatting.png "070702\-02\_InstructionalTextFormatting")  
  
 **Testo esplicativo in una finestra di dialogo di Visual Studio**  
  
#### Testo informativo  
 Testo informativo è testo che fornisce all'utente informazioni aggiuntive. È possibile statico o dinamico o utilizzato come una notifica. È sempre di sola lettura, ma se è utile per l'utente abbia la possibilità di copiare le informazioni, testo dinamico deve essere inserito in un contenitore di controlli, ad esempio un campo di testo di sola lettura.  
  
##### Testo dinamico \(specifici del contesto\)  
 Testo delle informazioni dinamiche cambia a seconda del contesto, ad esempio quando l'utente passa lo stato attivo. Spesso, ma non sempre, contenuto dinamico è associato a un'etichetta dinamica.  
  
 ![Dynamic information text](../../extensibility/ux-guidelines/media/070702-03_informationaldynamictext.png "070702\-03\_InformationalDynamicText")  
  
 **Testo informativo dinamico cambia a seconda del contesto.**  
  
##### Formattazione  
 Esistono due modi per visualizzare i campi di testo di sola lettura: direttamente nell'interfaccia utente della superficie di attacco \(vedere sopra\) o contenuti all'interno di un altro controllo, ad esempio una casella di testo o frame di gruppo. Entrambi sono corretto a seconda della situazione. Spetta la progettazione di funzionalità per determinare la modalità presentare le informazioni di sola lettura.  
  
 Testo può essere una casella di testo di sola lettura. In genere indica che il contenuto può essere selezionato e copiato, sebbene non possa essere modificato.  
  
 ![Informational text formatting for read&#45;only fields](../../extensibility/ux-guidelines/media/070702-04_informationalformatting.png "070702\-04\_InformationalFormatting")  
  
 **Formattazione del testo informativo per campi di sola lettura**  
  
#### Filigrane  
 Mentre il testo potrebbe essere lo stesso, la differenza tra le soglie e testo esplicativo è che le filigrane vengono sostituite con il contenuto quando il controllo o finestra non è vuota e testo esplicativo rimane visibile in qualsiasi momento.  
  
 Le filigrane devono essere utilizzate quando un controllo o finestra è vuota. Essi indicano ciò che deve essere eseguita per popolare l'area e possono includere collegamenti di azione per aprire finestre correlate, ad esempio un'origine di trascinamento.  
  
##### Stile di visualizzazione  
  
-   Le filigrane devono essere centrate orizzontalmente all'interno della finestra.  
  
-   Le filigrane devono essere allineato al centro, non allineato a sinistra.  
  
-   Filigrane possono essere centrate verticalmente o posizionate nella parte superiore dell'area. Se nella parte superiore dell'area, è necessario sufficiente spazio di sopra in modo da evidenziare la filigrana.  
  
-   Utilizzare il `Environment.GrayText` il tipo di carattere di colore ambiente standard e token. Collegamenti ipertestuali devono utilizzare i token standard del collegamento ipertestuale condivisa: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, e `Environment.PanelHyperlinkDisabled`.  
  
-   Le filigrane non possono essere selezionate per lo sfondo  
  
-   Se possibile, includere i collegamenti della filigrana per consentire all'utente di iniziare.  
  
 ![Watermark text in a designer window](../../extensibility/ux-guidelines/media/070702-05_watermark1.png "070702\-05\_Watermark1")  
  
 ![Watermark text in a tool window](../../extensibility/ux-guidelines/media/070702-06_watermark2.png "070702\-06\_Watermark2")  
  
 **Esempi di testo della filigrana in Visual Studio**  
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> Pulsanti e collegamenti ipertestuali  
  
### Panoramica  
 Controlli di pulsanti e link \(collegamenti ipertestuali\) devono seguire [linee guida di Windows Desktop base dei collegamenti ipertestuali](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) di utilizzo, testo, ridimensionamento e la spaziatura.  
  
### Scelta tra i pulsanti e collegamenti  
 Tradizionalmente, i pulsanti sono stati utilizzati per le azioni e i collegamenti ipertestuali sono stati riservati per la navigazione. I pulsanti possono essere utilizzati in tutti i casi, ma il ruolo dei collegamenti è stata espansa in Visual Studio in modo che i pulsanti e i collegamenti sono più intercambiabili in alcune condizioni.  
  
 Quando utilizzare i pulsanti di comando:  
  
-   Comandi principali  
  
-   Visualizzazione di windows utilizzato per raccogliere l'input o scelte, anche se sono comandi secondari  
  
-   Azioni distruttive o irreversibili  
  
-   Pulsanti di impegno all'interno di procedure guidate e flussi di pagina  
  
 Evitare di pulsanti di comando nelle finestre degli strumenti, o se è necessario più di due parole per l'etichetta. Collegamenti possono avere più etichette.  
  
 Quando utilizzare i collegamenti:  
  
-   Spostamento di un'altra finestra, un documento o pagina web  
  
-   Situazioni che richiedono un'etichetta più lungo o breve frase per descrivere lo scopo dell'azione  
  
-   Una stretta spazi in cui un pulsante potrebbe sovraccaricare l'interfaccia utente, purché l'azione non distruttiva o irreversibili  
  
-   Ridimensionando comandi secondari in situazioni in cui sono presenti molti comandi  
  
#### Esempi  
 ![Infobar command links following a status message](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703\-01\_CommandLinkInfobar")  
  
 **Comandi collegamenti utilizzati in seguito a un messaggio di stato sulla barra informazioni**  
  
 ![Links used in the CodeLens popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703\-02\_LinksInCodeLens")  
  
 **Collegamenti usati nel popup CodeLens**  
  
 ![Links used as secondary commands](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703\-03\_LinksAsSecondaryCommands")  
  
 **Collegamenti usati per i comandi secondari in cui è opportuno considerare troppa attenzione pulsanti**  
  
### Pulsanti comuni  
  
#### Testo  
 Seguire le istruzioni di scrittura in [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### Stile di visualizzazione  
  
##### Finestre di dialogo standard  
 La maggior parte dei pulsanti in Visual Studio verranno visualizzato nelle finestre di dialogo standard e non devono essere applicato uno stile. Riflettono l'aspetto dei pulsanti standard dettato dal sistema operativo.  
  
##### Con tema  
 In alcuni casi, i pulsanti possono essere utilizzati all'interno dell'interfaccia con stile e questi pulsanti devono essere applicato uno stile in modo appropriato. Vedere [Finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) per informazioni sui controlli a tema.  
  
### Pulsanti speciali  
  
#### Sfoglia... pulsanti  
 **\[Sfoglia...\]** pulsanti vengono utilizzati in griglie, finestre di dialogo e finestre degli strumenti e altri elementi dell'interfaccia utente non modale. Viene visualizzato un controllo di selezione che assiste l'utente durante la compilazione di un valore in un controllo. Esistono due varianti di questo pulsante, lunga e breve.  
  
 ![Long &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703\-04\_BrowseLong")  
  
 **Il valore long \[Sfoglia...\] button**  
  
 ![Short ellipsis&#45;only &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703\-05\_BrowseShort")  
  
 **Pulsante breve soli puntini di sospensione \[...\]**  
  
 Quando utilizzare il pulsante soli puntini di sospensione breve:  
  
-   Se è presente più di un long **\[Sfoglia...\]** pulsante in una finestra di dialogo, ad esempio quando consentono ai diversi campi per l'esplorazione. Utilizzare la breve **\[…\]** per ognuno evitare la confusione chiavi di accesso create da questa situazione \(**& Sfoglia** e **B & digita** nella finestra di dialogo stessa\).  
  
-   In una finestra di dialogo stretta o quando non è ragionevole per inserire il pulsante esteso.  
  
-   Se il pulsante verrà visualizzato in un controllo griglia.  
  
 Linee guida per il pulsante:  
  
-   Non utilizzare una chiave di accesso. Per accedervi utilizzando la tastiera, l'utente deve spostarsi dal controllo adiacente. Assicurarsi che l'ordine di tabulazione è tale che qualsiasi pulsante Sfoglia si immediatamente dopo il campo che occuperà. Non utilizzare mai un carattere di sottolineatura seguito dal primo periodo.  
  
-   Impostare Microsoft Active Accessibility \(MSAA\) **nome** proprietà **Sfoglia** \(compresi i puntini di sospensione\) in modo che sullo schermo verrà letto e come "Sfoglia" e non "punto\-punto\-punto" o "periodo\-periodo\-periodo". Per i controlli gestiti, vale a dire impostazione di **AccessibleName** proprietà.  
  
-   Non utilizzare mai i puntini di sospensione **\[…\]** pulsante per qualsiasi valore ad eccezione di un'azione di esplorazione. Ad esempio, se è necessario un **\[novità\]** pulsante ma non è disponibile spazio sufficiente per il testo, quindi la finestra di dialogo debba essere riprogettata.  
  
##### Ridimensionamento e la spaziatura  
 ![Sizing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703\-06\_BrowseSizing")  
  
 **Ridimensionamento \[Sfoglia...\] pulsanti**  
  
 ![Spacing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703\-07\_BrowseSpacing")  
  
 **Spaziatura \[Sfoglia...\] pulsanti**  
  
#### Pulsanti grafici  
 Alcuni pulsanti devono sempre utilizzare un'immagine grafica e testo per risparmiare spazio e per evitare problemi di localizzazione non includere mai. Questi vengono spesso utilizzati in altri elenchi ordinabile e selezioni di campo.  
  
> [!NOTE]
>  Gli utenti devono premere tab per questi pulsanti \(non sono presenti chiavi di accesso\), quindi inserirli in un ordine intelligente. Mappare la proprietà name del pulsante per l'azione che richiede in modo che gli screen reader interpretare correttamente l'azione del pulsante.  
  
|||  
|-|-|  
|Add|![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703\-08\_ButtonAdd")|  
|Rimuovi|![Graphical "Remove" button](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703\-09\_ButtonRemove")|  
|Aggiungi tutto|![Graphical "Add All" button](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703\-10\_ButtonAddAll")|  
|Rimuovi tutto|![Graphical "Remove All" button](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703\-11\_ButtonRemoveAll")|  
|Sposta su|![Graphical "Move Up" button](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703\-12\_ButtonMoveUp")|  
|Sposta giù|![Graphical "Move Down" button](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703\-13\_ButtonMoveDown")|  
|Delete|![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703\-14\_ButtonDelete")|  
  
##### Ridimensionamento e la spaziatura  
 Ridimensionamento di pulsanti grafici sono identico a quello della versione breve del **\[Sfoglia...\]** pulsante \(26 x 23 pixel\):  
  
 ![Button with and without transparent color showing](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703\-15\_GraphicalButtonSpacing")  
  
 **Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente visualizzato**  
  
### Collegamenti ipertestuali  
 I collegamenti ipertestuali sono particolarmente adatti per azioni basate sulla navigazione, ad esempio apertura di un argomento della Guida, finestra di dialogo modale o procedura guidata. Se viene utilizzato un collegamento ipertestuale per un comando, è necessario visualizzare sempre una modifica visibile ed evidente all'interfaccia utente. In generale, le azioni che eseguono il commit di un'azione \(ad esempio salvare, annullamento ed eliminazione\) meglio vengono comunicate tramite un pulsante.  
  
#### Stile di scrittura  
 Seguire il [linee guida per il Desktop di Windows per il testo dell'interfaccia utente](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). Non utilizzare "Ulteriori informazioni," "Indicare me ulteriori su" o "Assistenza con questo" formulazione. Al contrario, una frase di testo del collegamento della Guida in linea in termini di domande primario per il contenuto della Guida. Ad esempio, "**come aggiungere un server in Esplora Server?**"  
  
#### Stile di visualizzazione  
  
-   Utilizzano sempre i collegamenti ipertestuali [Il servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se un collegamento ipertestuale non viene applicato lo stile corretto, lampeggia rosso quando è attivo o Mostra un colore diverso dopo visitata.  
  
-   Non includere le sottolineature ondulate il controllo posizionato lo stato, a meno che il collegamento è un frammento di frase all'interno di una frase completa, ad esempio una filigrana.  
  
-   Le sottolineature ondulate non devono essere visualizzati al passaggio del mouse. Al contrario, il feedback all'utente che il collegamento è attivo è una lieve modifica e il cursore di collegamento appropriato.  
  
##  <a name="BKMK_TreeViews"></a> Visualizzazioni ad albero  
  
### Panoramica  
 Le visualizzazioni albero forniscono un modo per organizzare complessi sono elencati in gruppi padre\-figlio. Un utente è possibile espandere o comprimere i gruppi padre per mostrare o nascondere gli elementi figlio sottostante. Ogni elemento all'interno di una visualizzazione albero può essere selezionata per fornire un'ulteriore azione.  
  
 Questo argomento vengono illustrate funzionalità delle visualizzazioni di struttura ad albero, progettare in modo corretto e utilizzo.  
  
#### Contenuto dell'argomento  
  
-   [Stile di visualizzazione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [Interazioni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Stile di visualizzazione  
  
#### Pulsanti di espansione  
 Controlli visualizzazione struttura ad albero devono essere conforme alla progettazione espansore utilizzata da Windows e Visual Studio. Ogni nodo utilizza un controllo pulsante di espansione per visualizzare o nascondere elementi sottostanti. Utilizzo di un controllo expander offre una coerenza per gli utenti che potrebbero verificarsi visualizzazioni ad albero all'interno di Windows e Visual Studio.  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **Corretto: stile appropriato del nodo di visualizzazione albero utilizzando un controllo expander**  
  
 ![Incorrect tree view nodes](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705\-2\_TreeViewIncorrect1")  
  
 **Non corretta: stile non corretto del nodo della visualizzazione albero**  
  
#### Selection  
 Quando si seleziona un nodo all'interno della visualizzazione struttura ad albero, è necessario espandere l'evidenziazione per l'intera larghezza del controllo di visualizzazione albero. Questo consente agli utenti di identificare chiaramente quale elemento è stato selezionato. Selezione colori devono riflettere il tema corrente di Visual Studio.  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **Corretto: evidenziazione del nodo selezionato appropriato per l'intera larghezza del controllo di visualizzazione albero.**  
  
 ![Incorrect tree view highlighting](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705\-3\_TreeViewIncorrect2")  
  
 **Non corretta: evidenziazione del nodo selezionato non è indicato l'intera larghezza del controllo di visualizzazione albero.**  
  
#### Icone  
 Le icone devono essere utilizzate in controlli di visualizzazione albero solo se è aiutare a identificare visivamente le differenze tra gli elementi. In generale, le icone devono essere utilizzate solo in elenchi eterogenei in cui le icone contengono informazioni per distinguere i tipi di elementi. In un elenco omogeneo mediante icone di frequente possono essere considerate come rumore e deve essere evitato. In questo caso l'icona di gruppo \(padre\) può indicare il tipo di elementi in esso contenuti. L'eccezione a questa regola sono se l'icona è dinamica e viene utilizzato per indicare lo stato.  
  
#### Barre di scorrimento  
 Barre di scorrimento devono sempre essere nascosto se il contenuto si adatta all'interno del controllo di visualizzazione albero. È accettabile per le barre di scorrimento per essere nascoste o semi\-trasparente in una finestra scorrevole e vengono visualizzati quando la finestra contenente la visualizzazione albero è attiva o al momento del passaggio del mouse dell'albero visualizzare stesso.  
  
 ![Tree view with scroll bars](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705\-4\_Scrollbars")  
  
 **Entrambe le barre di scorrimento orizzontale e verticale vengono visualizzate perché il contenuto ha superato i limiti del controllo di visualizzazione albero.**  
  
###  <a name="BKMK_TreeViewInteractions"></a> Interazioni  
  
#### Menu di scelta rapida  
 Un nodo della visualizzazione struttura ad albero può rivelare le opzioni di sottomenu in un menu di scelta rapida. In genere, ciò si verifica quando un utente ha complessiva di un elemento o premuto il tasto Menu su una tastiera di Windows con l'elemento selezionato. È importante che il nodo riceve lo stato attivo e che sia selezionato. Ciò consente all'utente di identificare quale elemento a cui appartiene il sottomenu.  
  
 ![Selected tree node and context menu](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705\-5\_ContextMenu")  
  
 **L'elemento che ha generato il contesto menu riceve lo stato attivo per notificare all'utente quale elemento selezionato.**  
  
#### Tastiera  
 Visualizzazione albero deve offrire la possibilità di selezionare gli elementi e di espansione\/compressione di nodi utilizzando la tastiera. Ciò garantisce che navigazione soddisfi i requisiti di accessibilità.  
  
##### Controllo di visualizzazione albero  
 Controlli struttura ad albero di Visual Studio devono seguire la navigazione da tastiera comuni:  
  
-   **Freccia:** selezionare elementi spostando la struttura ad albero  
  
-   **Freccia verso il basso:** spostando verso il basso l'albero per selezionare elementi  
  
-   **Freccia destra:** espandere un nodo dell'albero  
  
-   **Freccia sinistra:** comprimere un nodo dell'albero  
  
-   **Tasto INVIO:** avviare, caricare, eseguire l'elemento selezionato  
  
##### Albero \(visualizzazione struttura ad albero e visualizzazione griglia\)  
 Un controllo albero è un controllo complesso che contiene una visualizzazione albero all'interno di una griglia. Espansione, compressione ed esplorare l'albero deve rispettare gli stessi comandi da tastiera in una visualizzazione ad albero, con le seguenti aggiunte:  
  
-   **Freccia destra:** espandere un nodo. Dopo aver espanso il nodo, deve continuare passando alla colonna più vicino a destra. Spostamento deve essere interrotta alla fine della riga.  
  
-   **Scheda:** consente di passare alla cella più vicino a destra.  Alla fine della riga, navigazione continua alla riga successiva.  
  
-   **MAIUSC \+ Tab:** consente di passare alla cella più vicino a sinistra.  All'inizio della riga, navigazione continua per la cella più a destra nella riga precedente.  
  
 ![Trid control in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705\-6\_Trid")  
  
 **Un controllo albero in Visual Studio**