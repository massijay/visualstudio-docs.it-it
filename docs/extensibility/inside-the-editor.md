---
title: "All&#39;interno dell&#39;Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], nuovo - architettura"
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 31
---
# All&#39;interno dell&#39;Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor è composto da un numero di sottosistemi diversi, che consentono di mantenere l'editor di testo modello separato dalla visualizzazione di testo e l'interfaccia utente.  
  
 Queste sezioni vengono descritti diversi aspetti dell'editor:  
  
-   [Panoramica dei sottosistemi](../extensibility/inside-the-editor.md#overview)  
  
-   [Il modello di testo](../extensibility/inside-the-editor.md#textmodel)  
  
-   [Visualizzazione di testo.](../extensibility/inside-the-editor.md#textview)  
  
 Queste sezioni vengono descritte le funzionalità dell'editor:  
  
-   [Tag e classificatori](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [Aree di controllo](../extensibility/inside-the-editor.md#adornments)  
  
-   [Proiezione](../extensibility/inside-the-editor.md#projection)  
  
-   [Struttura](../extensibility/inside-the-editor.md#outlining)  
  
-   [Associazioni del mouse](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [Operazioni di editor](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> Panoramica dei sottosistemi  
  
### Sottosistema di modello di testo  
 Il sottosistema di modello di testo è responsabile per la rappresentazione di testo e consentendo la modifica. Il sottosistema di modello di testo contiene il <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia, che descrive la sequenza di caratteri che deve essere visualizzato dall'editor. Questo testo può essere modificato, rilevato e manipolazione in molti modi. Il modello di testo fornisce inoltre tipi per i seguenti aspetti:  
  
-   Un servizio che gestisce la lettura e scrittura nel file system e associa file di testo.  
  
-   Servizio differenze che consente di individuare le differenze minime tra due sequenze di oggetti.  
  
-   Un sistema per descrivere il testo in un buffer in termini di subset del testo in altri buffer.  
  
 Il sottosistema di modello di testo è libero di concetti di interfaccia utente. Ad esempio, non è responsabile per la formattazione del testo o il layout del testo e ha alcuna conoscenza del visuali che può essere associata con il testo.  
  
 I tipi pubblici del sottosistema di modello di testo sono contenuti in Microsoft.VisualStudio.Text.Data.dll e Microsoft.VisualStudio.CoreUtilitiy.dll, che dipendono solo dalla libreria di classi base .NET Framework e Managed Extensibility Framework \(MEF\).  
  
### Sottosistema di visualizzazione di testo  
 Il sottosistema di visualizzazione testo è responsabile per la formattazione e visualizzazione di testo. I tipi di questo sottosistema sono suddivise in due livelli, a seconda se i tipi si basano su Windows Presentation Foundation \(WPF\). I tipi più importanti sono <xref:Microsoft.VisualStudio.Text.Editor.ITextView> e <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, che controllano il set di righe di testo da visualizzare, e anche il punto di inserimento, la selezione e le funzionalità per la decorazione di testo, utilizzando gli elementi UI WPF. Questo sottosistema fornisce anche i margini intorno al testo dell'area di visualizzazione. Questi margini possono essere esteso e possono contenere diversi tipi di contenuto e visual effetti. Esempi di margini sono riga numero consente di visualizzare e barre di scorrimento.  
  
 I tipi pubblici del sottosistema di visualizzazione di testo sono contenuti in Microsoft.VisualStudio.Text.UI.dll e Microsoft.VisualStudio.Text.UI.Wpf.dll. Il primo assembly contiene gli elementi indipendenti dalla piattaforma e il secondo contiene gli elementi di specifiche di WPF.  
  
### Sottosistema di classificazione  
 Il sottosistema di classificazione è responsabile di determinare le proprietà del carattere del testo. Un classificatore suddivide il testo in diverse classi, ad esempio, "parola chiave" o "commenti". La mappa di formato di classificazione si riferisce queste classi per le proprietà del carattere effettivo, ad esempio, "blu Consolas 10 pt". Queste informazioni vengono utilizzate per la visualizzazione di testo quando viene formattato e si esegue il rendering di testo. L'assegnazione di tag, che è descritta in dettaglio più avanti in questo argomento, permette di dati da associare a intervalli di testo.  
  
 I tipi pubblici del sottosistema di classificazione sono contenuti in Microsoft.VisualStudio.Text.Logic.dll e interagiscono con gli aspetti visivi di classificazione, contenute in Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### Sottosistema di operazioni  
 Il sottosistema di operazioni definisce il comportamento dell'editor. Fornisce l'implementazione per i comandi dell'editor di Visual Studio e il sistema di annullamento.  
  
## Informazioni dettagliate sul modello di testo e la visualizzazione di testo  
  
###  <a name="textmodel"></a> Il modello di testo  
 Il sottosistema di modello di testo è costituito da diversi gruppi di tipi di testo. Questi includono il buffer di testo, gli snapshot di testo e intervalli di testo.  
  
#### Buffer di testo e gli snapshot di testo  
 Il <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia rappresenta una sequenza di caratteri Unicode codificati con UTF\-16, che è la codifica utilizzata per il `String` tipo in .NET Framework. Un buffer di testo può essere reso persistente come un documento di file system, ma non è obbligatorio.  
  
 Il <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> viene utilizzato per creare un buffer di testo vuoto o un buffer di testo che viene inizializzato da una stringa o da <xref:System.IO.TextReader>. Buffer di testo può essere reso persistente nel file System come un <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 Buffer di testo può essere modificato da qualsiasi thread fino a quando un thread acquisisce la proprietà del buffer di testo chiamando <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Successivamente, solo il thread può eseguire modifiche.  
  
 Un buffer di testo può essere eseguita per molte versioni durante la relativa durata. Una nuova versione viene generata ogni volta che il buffer viene modificato, mentre l'oggetto non modificabile <xref:Microsoft.VisualStudio.Text.ITextSnapshot> rappresenta il contenuto di tale versione del buffer. Poiché gli snapshot di testo sono modificabili, è possibile accedere uno snapshot di testo in qualsiasi thread, senza restrizioni, anche se il buffer di testo che rappresenta continua a cambiare.  
  
#### Gli snapshot di testo e righe di testo dello Snapshot  
 È possibile visualizzare il contenuto di uno snapshot di testo come una sequenza di caratteri o come una sequenza di righe. Caratteri e le linee sono che entrambi indicizzate a partire da zero. Uno snapshot di testo vuoto contiene zero caratteri e una riga vuota. Una riga è delimitata da una sequenza di caratteri di interruzione di riga Unicode valida, o dall'inizio o alla fine del buffer. Caratteri di interruzione di riga sono rappresentati in modo esplicito nello snapshot di testo e le interruzioni di riga in uno snapshot di testo non deve essere lo stesso.  
  
> [!NOTE]
>  Per ulteriori informazioni sui caratteri di interruzione di riga nell'editor di Visual Studio, vedere [Codifiche e interruzioni di riga](../ide/encodings-and-line-breaks.md).  
  
 Una riga di testo è rappresentata da un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> oggetto, che può essere ottenuto da uno snapshot di testo per un numero di riga specifico o per una particolare posizione di carattere.  
  
#### SnapshotPoints, SnapshotSpans e NormalizedSnapshotSpanCollections  
 Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotPoint> rappresenta una posizione del carattere in uno snapshot. La posizione è garantita per essere compreso tra zero e la lunghezza dello snapshot. Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotSpan> rappresenta un intervallo di testo in uno snapshot. Posizione finale è garantita per essere compreso tra zero e la lunghezza dello snapshot. Il <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> è costituito da un set di <xref:Microsoft.VisualStudio.Text.SnapshotSpan> oggetti dello stesso snapshot.  
  
#### NormalizedSpanCollections e intervalli  
 Oggetto <xref:Microsoft.VisualStudio.Text.Span> rappresenta un intervallo che può essere applicato a un intervallo di testo in uno snapshot di testo. Posizioni di snapshot sono a base zero, intervalli possono iniziare in qualsiasi posizione compreso lo zero. Il `End` proprietà di un intervallo è uguale alla somma dei relativi `Start` proprietà e il relativo `Length` proprietà. Oggetto `Span` non include il carattere che verrà indicizzato per la `End` proprietà. Ad esempio, un intervallo che ha inizio \= 5 e lunghezza \= 3 ha fine \= 8, e include i caratteri in corrispondenza delle posizioni 5, 6 e 7. La notazione per questo intervallo è 5..8\).  
  
 Due intervalli si intersecano se hanno le posizioni in comune, tra cui la posizione finale. Pertanto, l'intersezione di \[3, 5\) e \[2, 7\) è \[3, 5\) e l'intersezione di \[3, 5\) e \[5, 7\) è \[5, 5\). \(Si noti che \[5, 5\) è un intervallo vuoto.\)  
  
 Due intervalli si sovrappongono se dispongono di posizioni in comune, tranne la posizione finale. Un intervallo vuoto mai si sovrappone a qualsiasi altro intervallo e la sovrapposizione di due intervalli non è mai vuota.  
  
 Oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> è un elenco di intervalli nell'ordine le proprietà di inizio degli intervalli. Nell'elenco, vengono uniti intervalli sovrapposti o adiacenti. Si consideri ad esempio il set di intervalli \[5..9\), \[0..1\), \[3..6\), e \[9..10\), l'elenco normalizzato di intervalli è \[0..1\), \[3..10\).  
  
#### ITextEdit, TextVersion e notifiche di modifica testo  
 Il contenuto di un buffer di testo può essere modificato utilizzando un <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto. Creazione di tale tipo di oggetto \(utilizzando uno del `CreateEdit()` i metodi di <xref:Microsoft.VisualStudio.Text.ITextBuffer>\) avvia una transazione di testo costituito da modifiche di testo. Ogni modifica è una sostituzione di un intervallo di testo nel buffer da una stringa. Le coordinate e il contenuto di ogni modifica sono espresse in relazione l'istantanea del buffer quando la transazione è stata avviata. Il <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto regola le coordinate di modifiche che sono interessate da altre modifiche nella stessa transazione.  
  
 Si consideri ad esempio un buffer di testo che contiene la stringa:  
  
```  
abcdefghij  
```  
  
 Applicare una transazione che contiene due modifiche, una modifica che sostituisce l'intervallo di \[2..4\) utilizzando il carattere `X` e una seconda modifica che sostituisce l'intervallo di \[6..9\) utilizzando il carattere `Y`. Il risultato è il buffer:  
  
```  
abXefYj  
```  
  
 Le coordinate per la seconda modifica sono state calcolate per quanto riguarda il contenuto del buffer all'inizio della transazione, prima è stata applicata la prima modifica apportata.  
  
 Rendere effettive le modifiche nel buffer quando il <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto commit viene eseguito chiamando il relativo `Apply()` metodo. Se si è verificato almeno una modifica non vuoto, un nuovo <xref:Microsoft.VisualStudio.Text.ITextVersion> viene creato un nuovo <xref:Microsoft.VisualStudio.Text.ITextSnapshot> viene creato un `Changed` viene generato l'evento. Ogni versione di testo ha un altro snapshot di testo. Uno snapshot di testo rappresenta lo stato del buffer di testo completo dopo una transazione di modifica, ma una versione di testo vengono descritte solo le modifiche da uno snapshot alla successiva. In generale, snapshot di testo deve essere utilizzata una sola volta e quindi ignorate, mentre le versioni di testo devono rimanere attive per un certo tempo.  
  
 Una versione di testo contiene un <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Questa raccolta vengono descritte le modifiche che, quando applicato a snapshot, verrà generato lo snapshot successivo. Ogni <xref:Microsoft.VisualStudio.Text.ITextChange> nella raccolta contiene la posizione del carattere di modifica, la stringa sostituita e la stringa di sostituzione. Stringa sostituita è vuota per un inserimento di base e la stringa di sostituzione è vuota per l'eliminazione di una base. La raccolta normalizzata è sempre `null` per la versione più recente del buffer di testo.  
  
 Un solo <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto può essere creata un'istanza di un buffer di testo in qualsiasi momento e tutte le modifiche di testo devono essere eseguite nel thread proprietario del buffer di testo \(se la proprietà è stato richiesto\). Una modifica di testo può essere abbandonata chiamando il relativo `Cancel` metodo o il relativo `Dispose` metodo.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> fornisce inoltre `Insert()`, `Delete()`, e `Replace()` metodi simili a quelle disponibili nel <xref:Microsoft.VisualStudio.Text.ITextEdit> interfaccia. La chiamata a questi ha lo stesso effetto di creazione di un <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto, eseguire la chiamata simile e quindi applicare la modifica.  
  
#### Punti di rilevamento e rilevamento  
 Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> rappresenta una posizione del carattere in un buffer di testo. Se il buffer viene modificato in modo che la posizione del carattere da spostare, il punto di rilevamento si sposta con esso. Ad esempio, se un punto di rilevamento si riferisce alla posizione 10 in un buffer e vengono inseriti cinque caratteri all'inizio del buffer, il punto di rilevamento quindi fa riferimento alla posizione 15. Se si verifica un inserimento con precisione la posizione indicata dal punto di rilevamento, il relativo comportamento è determinato dal relativo <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, che può essere `Positive` o `Negative`. Se la modalità di verifica è positiva, il punto di rilevamento si riferisce allo stesso carattere, che però corrisponde ora alla fine della stringa; Se la modalità di rilevamento è negativa, il punto di rilevamento si riferisce al primo carattere inserito nella posizione originale. Se il carattere in corrispondenza della posizione che è rappresentato da un punto di rilevamento viene eliminato, il punto di rilevamento si sposta al primo carattere che segue l'intervallo di eliminazione. Ad esempio, se un punto di rilevamento si intende il carattere alla posizione 5 e vengono eliminati i caratteri in corrispondenza delle posizioni 3 a 6, il punto di rilevamento si intende il carattere alla posizione 3.  
  
 Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> rappresenta un intervallo di caratteri anziché una sola posizione. Il comportamento è determinato dal relativo <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Se la modalità di rilevamento span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, dell'intervallo di rilevamento si espanda per incorporare il testo inserito in corrispondenza dei limiti; se è la modalità di rilevamento span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, dell'intervallo di rilevamento non include il testo inserito nei suoi bordi. Tuttavia, se è la modalità di rilevamento span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, un inserimento inserisce la posizione corrente verso l'inizio e se la modalità di rilevamento span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, un inserimento inserisce la posizione corrente verso la fine.  
  
 È possibile ottenere la posizione di un punto di rilevamento o l'intervallo di un intervallo di rilevamento per ogni snapshot del buffer di testo a cui appartengono. Rilevamento di punti e intervalli di rilevamento può fare riferimento in modo sicuro da qualsiasi thread.  
  
#### Tipi di contenuto  
 Tipi di contenuto sono un meccanismo per definire tipi diversi di contenuto. Tipo di contenuto può essere un tipo di file, ad esempio "text", "code" o "binary" o un tipo di tecnologia, ad esempio "xml", "vb" o "c\#". Ad esempio, la parola "using" è una parola chiave in c\# e Visual Basic, ma non in altri linguaggi di programmazione. Pertanto, la definizione di questa parola chiave sarà limitata ai tipi di contenuto "c\#" e "vb".  
  
 Tipi di contenuto vengono utilizzati come filtro per le aree di controllo e altri elementi dell'editor. Molte funzionalità dell'editor e punti di estensione definiti per il tipo di contenuto; colorazione del testo, ad esempio, è diversa per i file di testo normale, i file XML e file di codice sorgente di Visual Basic. Buffer di testo sono in genere assegnato un tipo di contenuto quando vengono creati e il tipo di contenuto di un buffer di testo può essere modificato.  
  
 Tipi di contenuto possono più\-ereditare da altri tipi di contenuto. Il <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> consente di specificare più tipi di base come elementi padre di un tipo di contenuto specificato.  
  
 Gli sviluppatori possono definire i propri tipi di contenuto e registrarli utilizzando il <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Molte funzionalità dell'editor possono essere definite rispetto a un tipo di contenuto specifico tramite il <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Editor margini, grafici e i gestori del mouse, ad esempio, possono essere definiti in modo che si applicano solo agli editor che consentono di visualizzare determinati tipi di contenuto.  
  
###  <a name="textview"></a> Visualizzazione di testo.  
 La parte di visualizzare il modello model view controller \(MVC\) definisce la visualizzazione di testo, la formattazione della visualizzazione, gli elementi grafici, ad esempio la barra di scorrimento e il punto di inserimento. Tutti gli elementi di presentazione dell'editor di Visual Studio sono basati su WPF.  
  
#### Visualizzazioni di testo  
 Il <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interfaccia è una rappresentazione indipendente dalla piattaforma di una visualizzazione di testo. Viene utilizzato principalmente per visualizzare i documenti di testo in una finestra, ma può anche essere utilizzato per altri scopi, ad esempio, in una descrizione comando.  
  
 Visualizzazione di testo fa riferimento a diversi tipi di buffer di testo. Il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> proprietà fa riferimento a un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> oggetto che fa riferimento a questi tre buffer di testo diversi: il buffer di dati, è il buffer di dati a livello superiore, il buffer di modifica, le funzioni di modifica si verifica, che nel buffer visual, ovvero il buffer che viene visualizzato nella visualizzazione del testo.  
  
 Il testo viene formattato in base i classificatori collegati al buffer di testo sottostante e decorare tramite il provider adornment collegate alla visualizzazione di testo stesso.  
  
#### Il sistema di Coordinate di visualizzazione di testo  
 Il sistema di coordinate di visualizzazione di testo specifica le posizioni nella visualizzazione del testo. In questo sistema di coordinate, il x valore 0,0 corrisponde al bordo sinistro del testo visualizzato e y valore 0,0 corrisponde al bordo superiore del testo viene visualizzato. Il x coordinare aumenta da sinistra a destra e y coordinare aumenta dall'alto verso il basso.  
  
 Un viewport \(la parte del testo visibile nella finestra di testo\) non è possibile scorrere orizzontalmente nello stesso modo, è necessario scorrere verticalmente. Un riquadro di visualizzazione è necessario scorrere orizzontalmente modificando la coordinata sinistra in modo da spostarla rispetto alla superficie di disegno. Tuttavia, un riquadro di visualizzazione è possibile scorrere verticalmente solo modificando il testo sottoposto a rendering, provocando un <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> dell'evento.  
  
 Distanze nel sistema di coordinate corrispondono ai pixel logici. Se la superficie di rendering di testo viene visualizzata senza una trasformazione in scala, un'unità di sistema di coordinate del rendering del testo corrisponde a un pixel sullo schermo.  
  
#### Margini  
 Il <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interfaccia rappresenta un margine e i controlli di visibilità di dimensioni e il margine. Vi sono quattro i margini predefiniti, che sono denominati "Top", "Left", "Right" e "Basso" e sono collegati alla parte superiore, inferiore, sinistro o bordo destro di una vista. I margini sono contenitori in cui possono essere inseriti altri margini. L'interfaccia definisce i metodi che restituiscono le dimensioni del margine e la visibilità di un margine. I margini sono elementi visivi che forniscono informazioni aggiuntive sulla visualizzazione di testo a cui sono collegate. Ad esempio, il margine del numero di riga consente di visualizzare i numeri di riga per la visualizzazione di testo. Il margine del glifo Visualizza gli elementi dell'interfaccia utente.  
  
 Il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaccia gestisce la creazione e la posizione dei margini. Margini possono essere ordinati per quanto riguarda altri margini. I margini di priorità più elevata si trovano più vicini alla visualizzazione di testo. Ad esempio, se vi sono due i margini sinistro, margine e margine B e margine B ha una priorità inferiore rispetto a margine, margine B viene visualizzata a sinistra del margine A.  
  
#### L'Host di visualizzazione di testo  
 Il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interfaccia contiene eventuali effetti adiacenti che accompagnano la visualizzazione, ad esempio, le barre di scorrimento e la visualizzazione di testo. L'host di visualizzazione di testo contiene inoltre i margini che sono associati a un bordo della visualizzazione.  
  
#### Testo formattato  
 Il testo che viene visualizzato in una visualizzazione testo è composta da <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> oggetti. Ogni riga di visualizzazione di testo corrisponde a una riga di testo nella visualizzazione del testo. Righe lunghe nel buffer di testo sottostante possono essere parzialmente nascosto \(se non è abilitato il ritorno a capo\) o suddivisi su più righe di visualizzazione di testo. Il <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interfaccia contiene metodi e proprietà per il mapping tra i caratteri e le coordinate e per le aree di controllo che può essere associati alla riga.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> gli oggetti vengono creati utilizzando un <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interfaccia. Se si teme solo il testo attualmente visualizzato nella vista, è possibile ignorare l'origine della formattazione. Se si è interessati nel formato di testo che non è visualizzato nella visualizzazione \(ad esempio, per supportare un taglio di testo RTF e incollare\), è possibile utilizzare <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> per formattare il testo in un buffer di testo.  
  
 Formati di visualizzazione di testo uno <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> alla volta.  
  
## Funzionalità dell'editor  
 Le funzionalità dell'editor sono progettate in modo che la definizione della funzionalità è separata dalla relativa implementazione. L'editor aggiunge le funzionalità seguenti:  
  
-   Tag e classificatori  
  
-   Aree di controllo  
  
-   Proiezione  
  
-   Struttura  
  
-   Associazioni del mouse e la chiave  
  
-   Operazioni e primitive  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> Tag e classificatori  
 I tag sono gli indicatori sono associati a un intervallo di testo. Possano essere visualizzati in modi diversi, ad esempio, utilizzando i colori di testo, le sottolineature ondulate, grafica o popup. I classificatori sono un tipo di tag.  
  
 Altri tipi di tag sono <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> per l'evidenziazione del testo, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> per la struttura, e <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> per errori di compilazione.  
  
#### Tipi di classificazione  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interfaccia rappresenta una classe di equivalenza, che è una categoria astratta del testo. Tipi di classificazione possono più\-ereditare da altri tipi di classificazione. Ad esempio, le classificazioni del linguaggio di programmazione potrebbe includere "parola chiave", "comment" e "identificatore", che ereditano da "code". Tipi di classificazione di linguaggio naturale potrebbero includere "sostantivo", "verbo" e "aggettivo", che eredita da "lingua".  
  
#### Classificazioni  
 È una classificazione di un'istanza di un determinato tipo di classificazione, in genere in un intervallo di testo. Oggetto <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> viene utilizzata per rappresentare una classificazione. Un intervallo di classificazione può essere considerato come un'etichetta che descrive un determinato intervallo di testo e indica al sistema di questo intervallo di testo di un determinato tipo di classificazione.  
  
#### Classificatori  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> è un meccanismo che suddivide il testo in una serie di classificazioni. Classificatori devono essere definiti per i tipi di contenuto specifici e creare un'istanza per i buffer di testo specifico. I client devono implementare <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> a far parte di classificazione del testo.  
  
#### Classificazione aggregatori  
 Un aggregatore di classificatore è un meccanismo che combina tutti i classificatori di buffer di un testo in un'unica serie di classificazioni. Un classificatore c\# sia un classificatore in lingua inglese, ad esempio, possibile creare le classificazioni su un commento in un file c\#. Considerare questo commento:  
  
```  
// This method produces a classifier  
```  
  
 Un classificatore c\# potrebbe assegnare un'etichetta all'intero intervallo come un commento, e il classificatore di lingua inglese può classificare "produce" come "verbo" e "method" come "nome". L'aggregatore produce un set di classificazioni non sovrapposti e il tipo del set è basato su tutti i contributi.  
  
 Un aggregatore di classificazione è anche un classificatore perché suddivide il testo in una serie di classificazioni. L'aggregatore classificatore garantisce inoltre che non esistono Nessuna classificazione sovrapposta e che le classificazioni sono ordinate. Singoli classificatori sono sovrapposte in alcun modo e può restituire qualsiasi set di classificazioni, in qualsiasi ordine.  
  
#### Formattazione di classificazione e la colorazione del testo  
 Formattazione del testo è riportato un esempio di una funzionalità che è basato sulla classificazione del testo. Utilizzato dal livello di visualizzazione di testo per determinare la visualizzazione del testo in un'applicazione. Area di formattazione di testo è dipendente da WPF, ma non la definizione logica delle classificazioni.  
  
 Un formato di classificazione è un set di proprietà per un tipo specifico di classificazione di formattazione. Questi formati ereditano il formato dell'elemento padre del tipo di classificazione.  
  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> è una mappa da un tipo di classificazione a un set di proprietà di formattazione del testo. L'implementazione della mappa del formato nell'editor gestisce tutte le esportazioni di formati di classificazione.  
  
###  <a name="adornments"></a> Aree di controllo  
 Le aree di controllo sono effetti grafici che non sono direttamente correlati al tipo di carattere e colore dei caratteri nella visualizzazione del testo. Ad esempio, la sottolineatura sottolineatura ondulata rossa che viene utilizzata per contrassegnare il codice non di compilazione in molti linguaggi di programmazione è un'area di controllo incorporato e le descrizioni comandi sono aree di controllo popup. Le aree di controllo sono derivati da <xref:System.Windows.UIElement> e implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Sono due tipi di tag dell'area di controllo di <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, per le aree di controllo che occupano lo stesso spazio del testo in una vista, e il <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, per la sottolineatura sottolineatura ondulata.  
  
 Grafici incorporati sono immagini che fanno parte della visualizzazione di testo formattato. Essi sono organizzati in livelli diversi di Z\-order. Esistono tre livelli predefiniti, come indicato di seguito: testo, il punto di inserimento e la selezione. Tuttavia, gli sviluppatori possono definire più livelli e li inserisce nell'ordine di uno rispetto a altro. I tre tipi di grafici incorporati sono aree di controllo relativo al testo \(quale spostamento quando si sposta il testo e vengono eliminati quando viene eliminato il testo\), grafici relativi alla visualizzazione, che hanno a che fare con parti non di testo della visualizzazione, e grafici controllato proprietario \(lo sviluppatore deve gestire la loro posizione\).  
  
 Le aree di controllo popup sono immagini che vengono visualizzati in una piccola finestra sopra la visualizzazione di testo, ad esempio, descrizioni comandi.  
  
###  <a name="projection"></a> Proiezione  
 Proiezione è una tecnica per la creazione di un tipo diverso di buffer di testo che non vengono effettivamente archiviati testo, ma invece Combina testo da altri buffer di testo. Ad esempio, un buffer di proiezione consente di concatenare il testo da due altri buffer e presentare il risultato come se fosse un solo buffer, o per nascondere parti di testo in un buffer. Un buffer di proiezione può fungere da buffer di origine a un altro buffer di proiezione. È possibile costruire un set di buffer che sono correlati tramite proiezione per ridisporre il testo in molti modi diversi. \(Un set di questo tipo è noto anche come un *grafico buffer*.\) La funzionalità di struttura di testo di Visual Studio viene implementata usando un buffer di proiezione per nascondere il testo compresso e l'editor di Visual Studio per le pagine ASP.NET utilizza proiezione per il supporto incorporati linguaggi quali Visual Basic e c\#.  
  
 Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> viene creato utilizzando <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Un buffer di proiezione è rappresentato da una sequenza ordinata di <xref:Microsoft.VisualStudio.Text.ITrackingSpan> gli oggetti che sono note come *intervalli di origine*. Il contenuto di questi intervalli viene presentato come una sequenza di caratteri. I buffer di testo da cui vengono disegnati gli intervalli di origine vengono denominati *buffer di origine*. Non è necessario che i client di un buffer di proiezione tenere presente che differisce da un buffer di testo normale.  
  
 Buffer di proiezione in ascolto degli eventi di modifica di testo nel buffer di origine. Quando il testo in un'origine comprendono le modifiche, il buffer di proiezione esegue il mapping delle coordinate di testo modificato per il proprio coordinate e genera eventi di modifica di testo appropriato. Si consideri ad esempio i buffer di origine A e B con il contenuto:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Se il buffer di proiezione P è costituito da due intervalli di testo, uno contenente tutti i buffer e cui altri che dispone di tutti i buffer B, P è il seguente contenuto:  
  
```  
P: ABCDEvwxyz  
```  
  
 Se la sottostringa `xy` viene eliminato dal buffer B, il buffer P genera un evento che indica se i caratteri in corrispondenza delle posizioni 7 e 8 sono stati eliminati.  
  
 Buffer di proiezione può essere modificato direttamente. Propaga le modifiche apportate ai buffer di origine appropriato. Ad esempio, se una stringa viene inserita nel buffer P in posizione 6 \(vale a dire la posizione originale del carattere "v"\), l'inserimento viene propagata al buffer B nella posizione 1.  
  
 Esistono restrizioni per gli intervalli di origine che contribuiscono a un buffer di proiezione. Intervalli di origine non possono sovrapporsi; Impossibile eseguire il mapping di una posizione in un buffer di proiezione per più di una posizione in un buffer di origine e una posizione in un buffer di origine non può eseguire il mapping a più di una posizione in un buffer di proiezione. Nessun circularities sono consentite nella relazione di buffer di origine.  
  
 Gli eventi vengono generati quando il set di origine memorizza nel buffer per la modifica di un buffer di proiezione e il set di origine che si estendono su modifiche.  
  
 Un buffer di elision è un tipo speciale di buffer di proiezione. Viene principalmente utilizzato per la struttura e per operazioni di espandono e comprimere blocchi di testo. Un buffer elision si basa su un solo buffer di origine e gli intervalli nel buffer di elision devono essere ordinati lo stesso come vengono ordinati nel buffer di origine.  
  
##### Grafico del Buffer  
 Il <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interfaccia attiva il mapping tra un grafico del buffer di proiezione. Tutti i buffer di testo e i buffer di proiezione vengono raccolti in un grafico aciclico diretto, come l'albero sintattico astratto generato dal compilatore di linguaggio. Il grafico è definito da buffer superiore, che può essere qualsiasi buffer di testo. Grafico del buffer può eseguire il mapping da un punto nel buffer superiore a un punto in un buffer di origine o da un'estensione nel buffer superiore a un set di intervalli in un buffer di origine. Analogamente, può eseguire il mapping di un punto o estendono da un buffer di origine a un punto nel buffer superiore. Grafici di buffer vengono creati utilizzando il <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
##### Eventi e i buffer di proiezione  
 Quando viene modificato un buffer di proiezione, le modifiche vengono inviate dal buffer di proiezione per i buffer che dipendono da esso. Dopo che tutti i buffer vengono modificati, vengono generati gli eventi di modifica nel buffer, a partire da buffer più in basso.  
  
###  <a name="outlining"></a> Struttura  
 La struttura è la possibilità di espandere o comprimere diversi blocchi di testo in una visualizzazione di testo. La struttura viene definita come una specie di <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, nello stesso modo in aree di controllo vengono definiti. Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> è un tag che definisce un'area di testo che può essere espanso o compresso. Per utilizzare la struttura, è necessario importare il <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> per ottenere un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Il gestore della struttura enumera comprime e si espande i diversi blocchi, rappresentati come <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> oggetti e genera eventi di conseguenza.  
  
###  <a name="mousebindings"></a> Associazioni del mouse  
 Le associazioni del mouse consente di collegare i movimenti del mouse comandi diversi. Le associazioni del mouse vengono definite tramite un <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, e tasti di scelta rapida vengono definiti tramite un <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. Il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automaticamente creata un'istanza di tutte le associazioni e li connette agli eventi del mouse nella visualizzazione.  
  
 Il <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interfaccia contiene i gestori di eventi di pre\-elaborazione e post\-elaborazione per gli eventi del mouse differenti. Handle di uno degli eventi, è possibile ignorare alcuni dei metodi in <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Operazioni di editor  
 Editor operazioni possono essere utilizzate per automatizzare l'interazione con l'editor, per la creazione di script o altri scopi. È possibile importare il <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> alle operazioni di accesso in un determinato <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. È quindi possibile utilizzare questi oggetti per modificare la selezione, scorrere la visualizzazione o spostare il punto di inserimento in diverse parti della visualizzazione.  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense supporta il completamento delle istruzioni, supporto firma \(noto anche come informazioni sul parametro\), informazioni rapide e lampadine.  
  
 Completamento delle istruzioni vengono forniti gli elenchi popup dei completamenti potenziali per i nomi dei metodi, gli elementi XML e altri elementi di codice o markup. In generale, un'azione dell'utente richiama una sessione di completamento. La sessione viene visualizzato l'elenco dei completamenti potenziali e l'utente può selezionare uno o chiudere l'elenco. Il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> è responsabile della creazione e attivazione di <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. Il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Calcola il <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> degli elementi di completamento per la sessione.  
  
## Vedere anche  
 [Servizio di linguaggio e punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Editor di importazioni](../extensibility/editor-imports.md)