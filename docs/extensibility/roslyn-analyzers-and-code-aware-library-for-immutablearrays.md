---
title: "Gli analizzatori di Roslyn e la libreria con riconoscimento del codice ImmutableArrays | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Gli analizzatori di Roslyn e la libreria con riconoscimento del codice ImmutableArrays
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il [.NET Compiler Platform](https://github.com/dotnet/roslyn) \("Roslyn"\) consente di creare librerie con riconoscimento del codice.  Una libreria di codice fornisce funzionalità che è possibile utilizzare e strumenti \(Roslyn analizzatori\) che consentono di utilizzare la libreria nel miglior modo o per evitare errori.  In questo argomento viene illustrato come compilare un analizzatore Roslyn reale per rilevare gli errori comuni quando si utilizza il [Raccolte non modificabili](../Topic/NIB:%20Immutable%20Collections.md) pacchetto NuGet.  Nell'esempio viene inoltre illustrato come fornire una correzione del codice per un problema di codice trovato dall'analizzatore di.  Gli utenti visualizzano correzioni del codice in Visual Studio lampadina dell'interfaccia utente e possono applicare una correzione per il codice automaticamente.  
  
## In questo argomento  
 In questo argomento include le sezioni seguenti:  
  
-   Introduzione  
  
-   Che cos'è il problema?  
  
-   Ricerca dei tipi di modello codice rilevante per attivare l'analisi  
  
-   Creazione del progetto Analyzer  
  
-   Inizializzare l'analizzatore  
  
-   Proprietà delle impostazione per gli utenti dell'analizzatore  
  
-   L'analisi di un'espressione di creazione oggetto  
  
-   All'avvio di Visual Studio con la prima volta che l'analizzatore  
  
-   Portare a termine utilizzando l'analizzatore di modifica e continuazione  
  
-   Aggiunta di una "correzione del codice" per il problema di codice  
  
-   Tentativo di correzione del codice  
  
-   Contattare il progetto di codice Video e completate  
  
## Introduzione  
 È necessario quanto segue per compilare questo esempio:  
  
-   Visual Studio 2015 \(non una versione Express Edition\) o versione successiva.  È possibile utilizzare il libero [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  È inoltre possibile, quando si installa Visual Studio, controllare gli strumenti di estendibilità di Visual Studio in strumenti comuni per installare il SDK allo stesso tempo.  Se è già installato Visual Studio, è inoltre possibile installare questo SDK, accedere al menu principale **File &#124; Nuovo &#124; Progetto**, scegliendo c\# nel riquadro di spostamento a sinistra e quindi estendibilità.  Quando si sceglie il "**installare gli strumenti di Visual Studio Extensibility**" modello di progetto di navigazione, viene richiesto di scaricare e installare il SDK.  
  
-   [.NET compiler Platform \("Roslyn"\) SDK](http://aka.ms/roslynsdktemplates).  È inoltre possibile installare questo SDK, accedere al menu principale **File &#124; Nuovo &#124; Progetto**, scegliere **c\#** nel riquadro di spostamento a sinistra e scegliendo **estendibilità**.  Quando si sceglie "**scaricare il SDK di piattaforma del compilatore .NET**" modello di progetto di navigazione, viene richiesto di scaricare e installare il SDK.  Questo SDK include il [Visualizzatore di sintassi Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  In questo modo, strumento estremamente utile capire quali tipi di modello di codice individuare l'analizzatore di.  Le chiamate di infrastruttura analyzer nel codice per tipi di modello di codice specifico, in modo che il codice viene eseguito quando è necessario solo e concentrarsi solo sull'analisi codice pertinente.  
  
## Che cos'è il problema?  
 Immaginiamo è fornire una libreria con ImmutableArray \(ad esempio, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>\) supportano.  Gli sviluppatori c\# hanno molta esperienza con le matrici .NET.  Tuttavia, a causa della natura delle tecniche di ImmutableArrays e ottimizzazione utilizzata nell'implementazione, intuitions per gli sviluppatori c\# che gli utenti della libreria di scrivere codice interrotto, come illustrato di seguito.  Inoltre, gli utenti non vengono visualizzati gli errori in fase di esecuzione, non è l'esperienza di qualità che vengono utilizzati per Visual Studio con .NET.  
  
 Gli utenti hanno familiarità con la scrittura di codice simile al seguente:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Creazione di matrici vuote da riempire con le successive righe di codice e utilizzando la sintassi dell'inizializzatore di raccolta sono molto familiare per gli sviluppatori c\#.  Tuttavia, il codice per un ImmutableArray scrivere lo stesso arresto anomalo in fase di esecuzione:  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Il primo errore è dovuto a ImmutableArray implementazione utilizzando una struttura per eseguire il wrapping dell'archivio dati sottostante.  Le strutture devono avere costruttori senza parametri in modo che `default(T)` le espressioni possono restituire struct con tutti i membri null o zero.  Quando il codice accede `b1.Length`, esiste un valore null alla fase di esecuzione di dereferenziazione errore poiché non sussiste alcun array di archiviazione sottostante nella struttura ImmutableArray.  Il modo corretto per creare un ImmutableArray vuoto è `ImmutableArray<int>.Empty`.  
  
 L'errore con gli inizializzatori di raccolta si verifica poiché il metodo ImmutableArray.Add restituisce nuove istanze ogni volta che viene chiamata.  Poiché ImmutableArrays non cambiano mai, quando si aggiunge un nuovo elemento, si ottiene un nuovo oggetto ImmutableArray \(che può condividere l'archiviazione per motivi di prestazioni con un ImmutableArray già esistente\).  Poiché `b2` punta per il primo ImmutableArray prima di chiamare `Add()` cinque volte, `b2` è ImmutableArray predefinito.  La chiamata lunghezza su tale anche arresti anomali del sistema con un valore null dereferenziazione errore.  Il modo corretto per inizializzare un ImmutableArray senza manualmente chiamata di Add consiste nell'utilizzare `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.  
  
## Ricerca dei tipi di nodo sintassi pertinente per attivare l'analisi  
 Per iniziare a compilare l'analizzatore, innanzitutto determinare il tipo di SyntaxNode si desidera cercare.    Avviare il Visualizzatore di sintassi nel menu **Visualizza &#124; Altre finestre &#124; Visualizzatore di sintassi Roslyn**.  
  
 Posizionare il cursore dell'editor sulla riga che dichiara `b1`.  Si noterà che mostra il Visualizzatore di sintassi è un `LocalDeclarationStatement` nodo della struttura di sintassi.  Questo nodo ha un `VariableDeclaration`, che a sua volta ha un `VariableDeclarator`, che a sua volta ha un `EqualsValueClause`, e infine è disponibile un `ObjectCreationExpression`.  Quando si fa clic nella struttura della sintassi del Visualizzatore di nodi, la sintassi nella finestra dell'editor evidenzia per visualizzare il codice rappresentato da tale nodo.  I nomi dei tipi di sub SyntaxNode corrispondere i nomi usati nella grammatica del linguaggio c\#.  
  
## Creazione del progetto Analyzer  
 Dal menu principale scegliere **File &#124; Nuovo &#124; Progetto**.  Nel **Nuovo progetto** finestra di dialogo, in **c\#** progetti nella barra di spostamento a sinistra, scegliere estensibilità e nel riquadro destro scegliere il **Analyzer con codice correggere** modello di progetto.  Immettere un nome e la finestra di dialogo di conferma.  
  
 Il modello verrà aperto un file DiagnosticAnalyzer.cs.  Scegliere tale editor scheda buffer.  Questo file contiene una classe analyzer \(formata dal nome assegnato al progetto\) che deriva da `DiagnosticAnalyzer` \(un tipo di API Roslyn\).  La nuova classe ha un `DiagnosticAnalyzerAttribute` dichiarazione l'analizzatore è pertinente per il linguaggio c\# in modo che il compilatore individua e carica l'analizzatore.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 È possibile implementare un analizzatore utilizzando Visual Basic destinata a codice c\#, e viceversa.  È più importante in DiagnosticAnalyzerAttribute di scegliere se l'analizzatore è destinato a una lingua o entrambi.  Gli analizzatori più sofisticati che richiedono dettagliata modellazione del linguaggio possono avere come destinazione solo una sola lingua.  Se l'analizzatore, controlli, ad esempio, solo i nomi dei tipi o i nomi dei membri pubblici, è possibile utilizzare il modello di linguaggio comuni che roslyn offre in Visual Basic e c\#.  Ad esempio, FxCop avverte che una classe implementa <xref:System.Runtime.Serialization.ISerializable>, ma la classe non dispone di <xref:System.SerializableAttribute> l'attributo è indipendente dal linguaggio e funziona per il codice Visual Basic e c\#.  
  
## L'analizzatore di inizializzazione  
 Scorrere verso il basso un po' la `DiagnosticAnalyzer` classe per visualizzare il `Initialize` metodo.  Il compilatore chiama questo metodo quando si attiva un analizzatore.  Il metodo accetta un `AnalysisContext` oggetto che consente l'analizzatore per ottenere informazioni di contesto e per registrare i callback per gli eventi per i tipi di codice che si desidera analizzare.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Aprire una nuova riga in questo metodo e il tipo "contesto". Per visualizzare un elenco di completamento Intellisense.  È possibile visualizzare nell'elenco di completamento sono disponibili molti `Register…` metodi per gestire vari tipi di eventi.  Ad esempio, il primo, `RegisterCodeBlockAction`, richiama il codice per un blocco, ovvero in genere codice tra parentesi graffe.  Registrazione di un blocco anche richiama il codice per l'inizializzatore di un campo, il valore assegnato a un attributo o il valore di un parametro facoltativo.  
  
 Se ad esempio `RegisterCompilationStartAction`, richiama il codice all'inizio di una compilazione, che risulta utile quando è necessario raccogliere i dati dello stato su molte posizioni.  È possibile creare una struttura di dati, ad esempio, per raccogliere tutti i simboli utilizzati, e ogni volta che viene richiamato l'analizzatore per alcune sintassi o al simbolo, è possibile salvare informazioni su ciascuna posizione nella struttura di dati.  Quando sta richiamata a causa la chiusura di compilazione, è possibile analizzare tutti i percorsi di salvataggio, ad esempio, per segnalare i simboli nel codice viene utilizzato da ogni `using` istruzione.  
  
 Utilizzo di **sintassi Visualizzatore**, si è appreso che si desidera essere chiamato quando il compilatore elabora un ObjectCreationExpression.  Utilizzare questo codice per impostare il callback:  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 Registrare un nodo di sintassi e filtrare per solo nodi di sintassi creazione oggetto.  Per convenzione, gli autori di Analizzatore utilizzare un'espressione lambda quando si registra azioni, che consente di mantenere gli analizzatori senza stato.  È possibile utilizzare la funzionalità di Visual Studio **generazione dall'utilizzo** per creare il `AnalyzeObjectCreation` metodo.  Questo genera il tipo di parametro di contesto corretto troppo.  
  
## Proprietà delle impostazione per gli utenti dell'analizzatore  
 In modo che l'analizzatore viene visualizzato nell'interfaccia utente di Visual Studio in modo appropriato, cercare e modificare la riga di codice per identificare l'analizzatore seguente:  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Modifica `"Naming"` a `"API Guidance"`.  
  
 Successivamente individuare e aprire il file resources. resx in un progetto utilizzando il **Esplora**.  È possibile inserire una descrizione per l'analizzatore, titolo e così via.  È possibile modificare il valore per tutti i componenti su `“Don’t use ImmutableArray<T> constructor”` per ora.  È possibile inserire gli argomenti della stringa di formattazione delle stringhe \({0}, \\{1\\}, e così via\) e versioni successive, quando si chiama `Diagnostic.Create()`, è possibile fornire una matrice di parametri di argomenti da passare.  
  
## L'analisi di un'espressione di creazione oggetto  
 Il `AnalyzeObjectCreation` metodo accetta un tipo diverso di contesto fornito dal framework di analizzatore di codice.  Il metodo Initialize `AnalysisContext` consente di registrare i callback di azione per impostare l'analizzatore.  Il `SyntaxNodeAnalysisContext`, ad esempio, ha un `CancellationToken` che è possibile passare intorno.  Se un utente avvia l'editor, Roslyn annullerà analizzatori in esecuzione per risparmiare lavoro e migliorare le prestazioni.  Un altro esempio, questo contesto dispone di una proprietà di nodo che restituisce il nodo di sintassi di creazione di oggetti.  
  
 Ottenere il nodo, che è possibile presupporre il tipo per cui è applicato l'azione di nodo di sintassi:  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
### All'avvio di Visual Studio con la prima volta che l'analizzatore  
 Avviare Visual Studio per creare ed eseguire l'analizzatore \(premere **F5**\).  Poiché nel progetto di avvio di **Esplora soluzioni** è il progetto VSIX, che esegue le compilazioni di codice, il codice e un progetto VSIX e quindi avvia Visual Studio con tale estensione VSIX installato.  Quando si avvia Visual Studio in questo modo, viene avviato con un hive del Registro di sistema distinte in modo che l'utilizzo principale di Visual Studio non verrà influenzato da istanze del test durante la compilazione di analizzatori.  La prima volta che si avvia in questo modo, Visual Studio esegue le inizializzazioni più simile a quando primo avvio di Visual Studio dopo l'installazione.  
  
 Creare un progetto console e quindi immettere il codice di matrice nel metodo Main applicazioni console:  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 Le righe di codice con `ImmutableArray` avere linee a zigzag perché è necessario ottenere il pacchetto NuGet non modificabile e aggiungere un `using` istruzione al codice.  Premere il pulsante destro del puntatore sul nodo del progetto nel **Esplora** e scegliere **Gestisci pacchetti NuGet**.  Nella finestra NuGet, digitare "Immutabile" nella casella di ricerca e scegliere l'elemento "System.Collections.Immutable" \(non si sceglie "Microsoft.Bcl.Immutable"\) nel riquadro sinistro e premere il pulsante installa nel riquadro di destra.  L'installazione del pacchetto viene aggiunto un riferimento ai riferimenti del progetto.  
  
 Vengono ancora visualizzate sottolineature rosse in `ImmutableArray`, quindi posizionare il cursore in tale identificatore e premere **CTRL \+.** \(punto\) per visualizzare il menu di correzione suggerita e scegliere di aggiungere le istruzioni `using` istruzione.  
  
 **Salvare e chiudere** la seconda istanza di Visual Studio per il momento di inserire in uno stato pulito per continuare.  
  
## Portare a termine utilizzando l'analizzatore di modifica e continuazione  
 Nella prima istanza di Visual Studio, impostare un punto di interruzione all'inizio di `AnalyzeObjectCreation` metodo premendo **F9** con il cursore sulla prima riga.  
  
 Avviare l'analizzatore con **F5**, e nella seconda istanza di Visual Studio, aprire nuovamente l'applicazione console è creata l'ultima volta.  
  
 Tornare alla prima istanza di Visual Studio nel punto di interruzione perché il compilatore Roslyn visto un'espressione di creazione di oggetti e ha l'analizzatore.  
  
 **Ottenere il nodo di creazione oggetto.** Passare alla riga che imposta il `objectCreation` variabile premendo **F10**, e il **finestra controllo immediato** valutare l'espressione `“objectCreation.ToString()”`.  Noterete che il nodo di sintassi a cui fa riferimento la variabile è il codice `"new ImmutableArray<int>()"`, solo ciò che sta cercando.  
  
 **Ottenere l'oggetto di tipo ImmutableArray \< T \>.** È necessario verificare se il tipo creato è ImmutableArray.  In primo luogo, ottenere l'oggetto che rappresenta questo tipo.  Controllare i tipi di utilizzo del modello semantico per assicurarsi di avere esattamente il tipo appropriato, e non si confronta la stringa da ToString \(\).  Immettere la seguente riga di codice alla fine della funzione:  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Specificare i tipi generici in metadati con backquotes \('\) e il numero di parametri generici.  Ecco perché non è presente... ImmutableArray \< T \> "nel nome dei metadati.  
  
 Il modello semantico presenta molte operazioni utili che consentono di porre domande sui simboli, il flusso di dati, della durata della variabile e così via.  Roslyn separa nodi sintassi dal modello semantico per vari motivi tecnici \(prestazioni, modellazione codice errato e così via\).  Si desidera il modello di compilazione per la ricerca di informazioni contenute nei riferimenti per il confronto accurato.  
  
 È possibile trascinare il puntatore di esecuzione giallo sul lato sinistro della finestra dell'editor.  Trascinarlo fino alla riga che imposta il `objectCreation` variabile e routine di nuova riga di codice utilizzando **F10**.  Se si posiziona il puntatore del mouse sulla variabile `immutableArrayOfType`, noterete che sono stati trovati il tipo esatto nel modello semantico.  
  
 **Ottiene il tipo dell'espressione di creazione oggetto.** In alcuni modi in questo articolo viene utilizzato "Type", ma se è necessario quindi "nuovo Foo" espressione, è necessario ottenere un modello di Foo.  È necessario ottenere il tipo dell'espressione di creazione oggetto per verificare se il tipo di ImmutableArray \< T \>.  Utilizzare il modello semantico nuovamente per ottenere informazioni sui simboli per il simbolo di tipo \(ImmutableArray\) nell'espressione di creazione oggetto.  Immettere la seguente riga di codice alla fine della funzione:  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Perché l'analizzatore deve gestire codice incompleti o errati nel buffer dell'editor \(ad esempio, manca un `using` istruzione\), verificare la presenza di `symbolInfo` da `null`.  È necessario ottenere un tipo denominato \(INamedTypeSymbol\) dall'oggetto di informazioni \(simbolo\) per completare l'analisi.  
  
 **Confrontare i tipi.** Poiché è un tipo generico aperto di T che stiamo cercando e il tipo nel codice è un tipo generico concreto, si eseguono query le informazioni sui simboli per il tipo è costituito da \(un tipo generico aperto\) e confrontare tale risultato con `immutableArrayOfTType`.  Immettere quanto segue alla fine del metodo:  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 **La diagnostica del report.** La diagnostica di Reporting è piuttosto semplice.  Utilizzare la regola creata nel modello di progetto, ovvero prima del metodo Initialize.  Poiché questa situazione nel codice è un errore, è possibile modificare la riga di inizializzazione regola sostituire `DiagnosticSeverity.Warning` \(verde brillante a zigzag\) con `DiagnosticSeverity.Error` \(sottolineatura ondulata rossa\).  Il resto della regola Inizializza dalle risorse che è stato modificato nella parte iniziale della procedura dettagliata.  È necessario anche il percorso per le linee a zigzag, ovvero il percorso della specifica del tipo dell'espressione di creazione oggetto del report.  Immettere il codice di `if` blocco:  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 La funzione dovrebbe essere simile al seguente \(forse formattati in modo diverso\):  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 Rimuovere il punto di interruzione in modo che è possibile vedere il funzionamento di analizzatore \(e restituisce la prima istanza di Visual Studio\).  Trascinare il puntatore di esecuzione all'inizio del metodo e premere **F5** per continuare l'esecuzione.  Quando torna alla seconda istanza di Visual Studio, il compilatore inizieranno ad esaminare di nuovo il codice e verrà eseguita una chiamata nell'analizzatore.  È possibile visualizzare una sottolineatura ondulata sotto `ImmutableType<int>`.  
  
## Aggiunta di una "correzione del codice" per il problema di codice  
 Prima di iniziare, chiudere la seconda istanza di Visual Studio e interrompere il debug nella prima istanza di Visual Studio \(in cui si sta sviluppando l'analizzatore\).  
  
 **Aggiungere una nuova classe.** Utilizzare il menu di scelta rapida \(pulsante destro del puntatore\) sul nodo del progetto in Esplora soluzioni e scegliere di aggiungere un nuovo elemento.  Aggiungere una classe denominata `BuildCodeFixProvider`.  Questa classe deve derivare da `CodeFixProvider`, e sarà necessario utilizzare **CTRL \+.** \(punto\) per richiamare la correzione del codice che aggiunge il corretto `using` istruzione.  Questa classe deve inoltre essere annotata con `ExportCodeFixProvider` attributo e sarà necessario aggiungere un `using` istruzione per risolvere il `LanguageNames` enum.  È necessario disporre di un file di classe con il codice seguente:  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 **Lo stub dei membri derivati.** A questo punto, posizionare il cursore dell'editor dell'identificatore `CodeFixProvider` e premere **CTRL \+.** \(punto\) per lo stub l'implementazione per questa classe base astratta.  Questo genera una proprietà e un metodo.  
  
 **Implementare la proprietà.** Compilare il `FixableDiagnosticIds` della proprietà `get` corpo con il codice seguente:  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
 Roslyn riunisce diagnostica e corregge creando una corrispondenza tra questi identificatori, che sono semplicemente delle stringhe.  Il modello di progetto generato un ID di diagnostica e hanno la possibilità di modificarlo.  Il codice nella proprietà restituisce solo l'ID della classe analyzer.  
  
 **Il metodo RegisterCodeFixAsync accetta un contesto.** Il contesto è importante perché per la diagnostica più possibile applicare una correzione del codice, o che sia presente più di un problema su una riga di codice.  Se si digita "contesto". nel corpo del metodo, l'elenco di completamento Intellisense illustrerà alcuni membri utili.  È un membro CancellationToken che è possibile verificare se si desidera annullare la correzione.  È un membro di documento che dispone di molti membri utili e consente di ottenere gli oggetti modello di progetto e soluzione.  È un membro di intervallo che corrisponde all'inizio e fine del percorso del codice specificata quando è stato segnalato lo strumento di diagnostica.  
  
 **Impostare il metodo di essere asincrono.** La prima cosa è necessario eseguire è correggere la dichiarazione di metodo generato da un `async` metodo.  Non include la correzione del codice per l'implementazione di una classe astratta venivano il `async` parola chiave anche se il metodo restituisce un `Task`.  
  
 **Ottenere la radice della struttura di sintassi.** Per modificare il codice che è necessario creare una nuova struttura di sintassi in base alle modifiche rende la correzione del codice.  È necessario il `Document` dal contesto per chiamare `GetSyntaxRootAsync`.  In questo modo un metodo asincrono lavoro sconosciuto per ottenere l'albero della sintassi, magari con recupero il file dal disco, analizzarlo e compilazione del modello di codice Roslyn per esso.  Durante questo periodo, utilizzare l'interfaccia utente di Visual Studio deve essere reattiva `async` attiva.  Sostituire la riga di codice nel metodo con il codice seguente:  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
 **Trovare il nodo con il problema.** Passare nel periodo del contesto, ma il nodo che è trovare potrebbe non essere il codice che si desidera modificare.  La diagnostica segnalata fornito solo l'intervallo per l'identificatore di tipo \(in cui apparteneva linee a zigzag\), ma è necessario sostituire l'espressione di creazione oggetto intero, inclusi il `new` keywoard all'inizio e la parentesi alla fine.  Aggiungere il codice seguente al metodo \(e utilizzare **CTRL \+.** per aggiungere un `using` istruzione per `ObjectCreationExpressionSyntax`\):  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
 **Registrare la correzione del codice per la lampadina dell'interfaccia utente.** Quando si registra la correzione del codice, Roslyn viene inserito automaticamente nella lampadina Visual Studio dell'interfaccia utente.  Verrà visualizzato agli utenti finali possono utilizzare **CTRL \+.** \(punto\) quando l'analizzatore zigzag un bad `ImmutableArray<T>` Usa costruttore.  Poiché il provider di correzione di codice viene eseguito solo quando si verifica un problema, è possibile si presuppone l'espressione di creazione oggetto desiderato.  Dal parametro di contesto, è possibile registrare la correzione del codice nuovo aggiungendo il codice seguente alla fine di `RegisterCodeFixAsync` metodo:  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
 È necessario inserire il cursore dell'editor dell'identificatore `CodeAction`, quindi utilizzare **CTRL \+.** \(punto\) per aggiungere le istruzioni `using` per questo tipo di istruzione.  
  
 Quindi posizionare il cursore dell'editor nel `ChangeToImmutableArrayEmpty` identificatore e utilizzare **CTRL \+.** per generare automaticamente stub di metodo.  
  
 Questo ultimo frammento di codice è stato aggiunto registra la correzione del codice mediante il passaggio di un `CodeAction` e l'ID di diagnostica per il tipo di problema rilevato.  In questo esempio è disponibile un solo ID diagnostica che fornisce questo codice consente di correggere, pertanto è possibile passare solo il primo elemento della matrice ID di diagnostica.  Quando si crea il `CodeAction`, si passa il testo che la lampadina dell'interfaccia utente deve utilizzare come una descrizione della correzione del codice.  È anche possibile passare in una funzione che accetta un oggetto CancellationToken e restituisce un nuovo documento.  Il nuovo documento contiene una nuova struttura di sintassi che include il codice corretto che chiama `ImmutableArray.Empty`.  Questo frammento di codice utilizza un'espressione lambda in modo che è possibile chiudere il documento del contesto e il nodo objectCreation.  
  
 **Creare la nuova struttura di sintassi.** Nel `ChangeToImmutableArrayEmpty` metodo il cui stub generato in precedenza, immettere la riga di codice: `ImmutableArray<int>.Empty;`.  Se si visualizza nuovamente la finestra degli strumenti del Visualizzatore di sintassi, è possibile visualizzare che questa sintassi è un nodo SimpleMemberAccessExpression.  Questo è ciò che questo metodo deve creare e restituire un nuovo documento.  
  
 La prima modifica a `ChangeToImmutableArrayEmpty` consiste nell'aggiungere `async` prima `Task<Document>` perché i generatori di codice è possono presupporre il metodo deve essere asincrono.  
  
 Inserire il corpo con il codice seguente in modo che il metodo è simile al seguente:  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
 È necessario inserire il cursore dell'editor nel `SyntaxGenerator` identificatore e utilizzare **CTRL \+.** \(punto\) per aggiungere le istruzioni `using` per questo tipo di istruzione.  
  
 Questo codice utilizza `SyntaxGenerator`, ovvero un tipo particolarmente utile per la creazione di nuovo codice.  Dopo il recupero di un generatore per il documento che presenta il problema di codice, `ChangeToImmutableArrayEmpty` chiamate `MemberAccessExpression`, passando il tipo che include il membro che si desidera accedere e passando il nome del membro come una stringa.  
  
 Successivamente, il metodo recupera la radice del documento e, poiché ciò può implicare lavoro arbitrario nel caso generale, il codice attende la chiamata e passa il token di annullamento.  Modelli di codice Roslyn non sono modificabili, all'utilizzo di una stringa .NET. Quando si aggiorna la stringa, si ottiene in cambio un nuovo oggetto stringa.  Quando si chiama `ReplaceNode`, verrà restituito un nuovo nodo radice.  La maggior parte della struttura di sintassi è condiviso \(poiché non è modificabile\), ma il `objectCreation` nodo viene sostituito con il `memberAccess` nodo, nonché tutti i nodi padre fino alla radice della struttura di sintassi.  
  
## Tentativo di correzione del codice  
 È ora possibile premere **F5** per eseguire l'analizzatore in una seconda istanza di Visual Studio.  Aprire il progetto di console usata in precedenza.  A questo punto dovrebbe essere la lampadina viene visualizzata in cui la nuova espressione di creazione oggetto per `ImmutableArray<int>`.  Se si preme **CTRL \+.** \(periodo\), quindi verrà visualizzato il codice correggere, per visualizzare un'anteprima della differenza di codice generato automaticamente nella lampadina dell'interfaccia utente.  Roslyn viene creato questo.  
  
 Suggerimento Pro: Se si avvia la seconda istanza di Visual Studio e non viene visualizzata la lampadina con la correzione del codice, quindi si potrebbe essere necessario cancellare la cache dei componenti di Visual Studio.  La cancellazione della cache impone Visual Studio per riesaminare i componenti, in modo da Visual Studio deve selezionare il componente più recente.  In primo luogo, arrestare la seconda istanza di Visual Studio.  In Esplora risorse, quindi passare alla directory dell'utente \(c:\\users\\ \< userid \>\) e trovare AppData\\Local\\Microsoft\\VisualStudio\\14.0Roslyn\\.  In questa directory, eliminare la directory sub ComponentModelCache.  Le modifiche una versione a altra con Visual Studio "14".  
  
## Video di parlare e fine codice progetto  
 È possibile visualizzare in questo esempio viene sviluppato e illustrate ulteriormente in [questo talk](http://channel9.msdn.com/events/Build/2015/3-725).  La discussione illustra l'analizzatore di lavoro e vengono descritte la creazione.  
  
 È possibile visualizzare tutto il codice [qui](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Le sottocartelle DoNotUseImmutableArrayCollectionInitializer e DoNotUseImmutableArrayCtor dispongano di un file c\# per la ricerca di problemi e un file c\# che implementa le correzioni del codice che compaiono nella lampadina Visual Studio dell'interfaccia utente.  Si noti il codice è un po' più astrazione per evitare il recupero dell'oggetto di tipo ImmutableArray \< T \> più volte.  Usa nidificate azioni registrate per salvare l'oggetto di tipo in un contesto che è disponibile ogni volta che le azioni sub \(analizzare la creazione di oggetti e analizzare le inizializzazioni di raccolta\) eseguire.  
  
## Vedere anche  
 [Parlare \\\\Build 2015](http://channel9.msdn.com/events/Build/2015/3-725)   
 [Codice completato su github](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)   
 [Alcuni esempi su github, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)   
 [Altri documenti nel sito Web github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)   
 [Regole FxCop implementate con gli analizzatori di Roslyn su github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)