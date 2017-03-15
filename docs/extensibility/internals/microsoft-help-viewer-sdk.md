---
title: "Microsoft Help Viewer SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 33
---
# Microsoft Help Viewer SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questo articolo contiene le seguenti attività per gli integratori di Visualizzatore della Guida di Visual Studio:  
  
-   Creazione di un argomento \(il tasto F1\)  
  
-   Creazione di un pacchetto di personalizzazione del contenuto del Visualizzatore della Guida  
  
-   Distribuzione di un set di articoli  
  
-   Aggiunta della Guida di Visual Studio shell \(integrato o isolata\)  
  
-   Risorse aggiuntive  
  
### Creazione di un argomento \(il tasto F1\)  
 In questa sezione viene fornita una panoramica dei componenti di un argomento della presentazione, i requisiti di argomento, una breve descrizione di come creare un argomento \(inclusi i requisiti di supporto F1\) e, infine, un argomento di esempio con il risultato del rendering.  
  
 **Visualizzatore argomento Panoramica della Guida**  
  
 Quando viene chiamato un argomento per il rendering, il Visualizzatore della Guida ottiene gli elementi del pacchetto personalizzazione che sono associati con l'argomento relativo al momento dell'ultimo aggiornamento, con l'argomento XHTML, o l'installazione e vengono combinati due per garantire la visualizzazione di contenuto presentata \(dati di personalizzazioni e dati dell'argomento\).  Il pacchetto di personalizzazione contiene logo, il supporto per i comportamenti del contenuto e testo branding \(copyright, ecc.\).  Per ulteriori informazioni sugli elementi di personalizzazione del pacchetto, vedere "Creazione del pacchetto di personalizzazione" di seguito.  Nel caso in cui non è presente alcun pacchetto di personalizzazione associato all'argomento, il Visualizzatore della Guida verrà usato il pacchetto di personalizzazione fallback che si trova nella radice dell'applicazione del Visualizzatore della Guida \(Branding\_en\-US.mshc\).  
  
 **Guida Visualizzatore argomento requisiti**  
  
 Per eseguire il rendering correttamente all'interno del Visualizzatore della Guida, contenuto dell'argomento non elaborato deve essere XHTML 1.1 base di W3C.  
  
 In genere, un argomento contiene due sezioni:  
  
-   Metadati \(vedere riferimento ai metadati del contenuto\): padre dati sull'argomento, ad esempio, l'ID univoco di argomento, valore parola chiave, l'argomento del sommario ID, ID di nodo e così via.  
  
-   Contenuto del corpo: compatibile con XHTML 1.1 base W3C che include supportati comportamenti del contenuto \(area comprimibile, frammento di codice e così via. Un elenco completo è illustrato di seguito\).  
  
 Pacchetto di personalizzazione di Visual Studio supportate controlli:  
  
-   Collegamenti  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Membri ereditati  
  
-   LanguageSpecificText  
  
 Stringhe di linguaggio supportato \(non maiuscole\/minuscole\):  
  
-   JavaScript  
  
-   CSharp o c\#  
  
-   cplusplus o visualc \+ \+ o c \+ \+  
  
-   JScript  
  
-   Visual Basic o Visual Basic  
  
-   f \# o fsharp o ADFS  
  
-   altro: una stringa che rappresenta un nome di lingua  
  
 **Creazione di un argomento del Visualizzatore della Guida**  
  
 Creare un nuovo documento XHTML denominato ContosoTopic4.htm e includere il tag title \(sotto\).  
  
```html  
<html> <head> <title>Contoso Topic 4</title> </head> <body> </body> </html>  
  
```  
  
 Successivamente, aggiungere dati per definire come l'argomento deve essere presentato \(self marchio o No\), come fare riferimento in questo argomento per F1, in cui è presente in questo argomento nel sommario, il relativo ID \(per il riferimento di collegamento da altri argomenti\), e così via.  Vedere la tabella "Contenuto metadati" di seguito per un elenco completo di metadati supportati.  
  
-   In questo caso, utilizzeremo il pacchetto di personalizzazione, una variante del pacchetto di personalizzazione di Visualizzatore della Guida di Visual Studio.  
  
-   Aggiungere il nome di metadati F1 e il valore \("Microsoft.Help.F1" contenuto \= "ContosoTopic4"\) che corrisponderà al valore di F1 fornito nel contenitore di proprietà IDE.  \(Vedere la sezione supporto F1 per ulteriori informazioni\).   Questo è il valore corrispondente a F1 chiamare dall'interno dell'IDE per la visualizzazione di questo argomento quando si seleziona F1 nell'IDE.  
  
-   Aggiungere l'ID di argomento. Questa è la stringa utilizzata da altri argomenti per il collegamento a questo argomento.  È l'ID di Visualizzatore della Guida relativo a questo argomento.  
  
-   Per il sommario, aggiungere il nodo padre di questo argomento per definire in cui verrà visualizzati in questo nodo del sommario di argomento.  
  
-   Per il sommario, aggiungere l'ordine dei nodi di questo argomento. Quando il nodo padre è n. numero di nodi figlio, definire la posizione dell'argomento nell'ordine dei nodi figlio. Ad esempio, in questo argomento è numero 4 di 4 argomenti figlio.\)  
  
 Sezione di metadati di esempio:  
  
```html  
<html> <head> <title>Contoso Topic 4</title> <meta name="SelfBranded" content="false" /> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> </head> <body> </body> </html>  
  
```  
  
 **Corpo dell'argomento**  
  
 Il corpo \(senza includere l'intestazione e piè di pagina\) dell'argomento conterrà i collegamenti alla pagina, una sezione di nota, un'area comprimibile, un frammento di codice e una sezione di testo specifico della lingua.  Vedere la sezione personalizzazione per informazioni su tali aree dell'argomento della presentazione.  
  
1.  Aggiungere un tag title argomento:  `<div class="title">Contoso Topic 4</div>`  
  
2.  Aggiungere una sezione Nota: `<div class="alert"> add your table tag and text </div>`  
  
3.  Aggiungere un'area comprimibile:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Aggiungere un frammento di codice:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Aggiungere testo specifico del linguaggio di codice:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` si noti che devLangnu \= consente di immettere altri linguaggi. Ad esempio, devLangnu \= "Fortran" visualizzerà Fortran quando il frammento di codice DisplayLanguage \= Fortran  
  
6.  Aggiungere i collegamenti alla pagina: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Nota: per non supportate nuovo "lingua di visualizzazione" \(ad esempio, F \#, Cobol, Fortran\) la colorazione del codice nel frammento di codice sarà monocromatico.  
  
 **Argomento visualizzatore della Guida di esempio** nel codice viene illustrato come definire i metadati, un frammento di codice, un'area comprimibile e un testo specifico della lingua.  
  
```  
<?xml version="1.0" encoding="utf-8"?> <html> <head> <title>Contoso Topic 4</title> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> <meta name="SelfBranded" content="false" /> </head> <body> <div class="title">Contoso Topic 4</div> <div id="header"> <table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%"> <tr id="headerTableRow2"><td align="left"> <span id="nsrTitle">Contoso Topic 1</span> </td> <td align="right"> </td></tr> <tr id="headerTableRow1"><td align="left"> <span id="runningHeaderText">Contoso Widgets & Sprockets</span> </td></tr> </table> </div> <h2>Table of Contents</h2> <ul class="toc"> <li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li> <li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li> </ul> <div class="topic"> <div id="mainSection"> <div id="mainBody"> <a name="introduction"></a> <h2>1.0 Introduction</h2> <p>[This documentation is for sample purposes only.]</p> <p>Contoso Topic 1 contains examples of: <ul> <li>Collapsible Area</li> <li>Bookmark ("See also")</li> <li>Code Snippets from Branding Package</li> </ul> </p> <div class="alert"><table><tr><th> <strong>Note </strong></th></tr> <tr><td> <p>This is an example of a <span class="label">Note </span>section. Call out important items for your reader in this <span class="label">Note </span>box. </p></td></tr> </table> </div> </div> <CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> <a id="sectionToggle0"><!----></a> <div> Example of Collapsible Area <br/> Lorem ipsum dolor sit amet... </div> </CollapsibleArea> <div id="snippetGroup" > <CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" > Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip Dim messageBoxVB as New System.Text.StringBuilder() messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds) messageBoxVB.AppendLine() ... MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event") End Sub </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e) { System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder(); messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds ); messageBoxCS.AppendLine(); ... MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" ); } </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" > some F# code </CodeSnippet> </div> <h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" /> <a name="seealso"></a> <h1 class="heading">See Also</h1> <div id="seeAlsoSection" class="section"> <div class="seeAlsoStyle"> <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a> </div> </div> </div> </div> </body> </html>  
  
```  
  
 **Il tasto F1**  
  
 In Visual Studio, selezionando F1 genera i valori forniti dalla posizione del cursore all'interno dell'IDE e popola un "elenco di proprietà" con i valori specificati \(in base alla posizione del cursore. Quando il cursore è posizionato funzionalità x, funzionalità x è attivo o in stato di attivo e popola l'elenco di proprietà con valori.  Quando si seleziona F1 viene popolato l'elenco di proprietà e il codice di Visual Studio F1 cerca di vedere se l'origine della Guida i clienti predefinito è locale o in linea \(online è il valore predefinito\), quindi crea la stringa appropriata basata sugli utenti, l'impostazione \(in linea è il valore predefinito\): esecuzione della shell \(vedere la Guida dell'amministratore per exe parametri di avvio\) con i parametri per il Visualizzatore della Guida locale \+ parole chiave nel contenitore delle proprietà se la Guida locale è il valore predefinito , o l'URL di MSDN con la parola chiave nell'elenco di parametri.  
  
 Se vengono restituite tre stringhe di F1, definita per come una stringa multivalore, eseguire il primo termine, cercare un riscontro, e se viene trovato, abbiamo terminato; in caso contrario, spostare la stringa successiva.  Ordine è importante. Presentazione delle parole chiave multivalore deve essere più lunga stringa alla stringa più corta.  Per effettuare questa verifica nel caso di parole chiave con più valori, esaminare la stringa di F1 URL online, che includerà la parola chiave scelta.  
  
 In Visual Studio 2012, tra online e offline, viene reso intenzionalmente una divisione più avanzata in modo che se l'impostazione dell'utente per Online, quindi è semplicemente passato la richiesta F1 direttamente al servizio query online su MSDN, piuttosto che eseguire il routing tramite l'agente di raccolta della Guida che avevamo in Visual Studio 2010. È quindi basarsi su uno stato di "contenuto fornitore installato \= true" per determinare se eseguire un'operazione diversa in tale contesto. Se true, quindi, viene eseguita la logica di analisi e di routing a seconda di ciò che si desidera supportare i clienti. Se false, quindi è sufficiente accedere a MSDN. Se l'impostazione dell'utente è locale, tutte le chiamate semplicemente passare al modulo di gestione della Guida locale.  
  
 F1 diagramma di flusso:  
  
 ![F1 flow](../../extensibility/internals/media/f1flow.png "F1flow")  
  
 Quando l'origine del contenuto della Guida in linea predefinito del Visualizzatore della Guida è impostata su online \(Avvia in browser\):  
  
-   Le funzionalità di Visual Studio Partner \(VSP\) generano un valore all'elenco di proprietà F1 \(prefix.keyword contenitore delle proprietà e l'URL in linea per il prefisso trovato nel Registro di sistema\): F1 invia un URL VSP \+ parametri al browser.  
  
-   Funzionalità di Visual Studio \(editor di linguaggio, voci di menu specifiche di Visual Studio, e così via\): F1 invia un URL di Visual Studio al browser.  
  
 Quando l'origine del contenuto della Guida in linea predefinito del Visualizzatore della Guida è impostata su Guida locale \(avvio in Help Viewer\):  
  
-   Funzionalità VSP in \(parola chiave\) corrispondenti tra il contenitore delle proprietà F1 e indice dell'archivio locale \(vale a dire il prefix.keyword contenitore delle proprietà \= valore trovato nell'archivio locale indice\): F1 esegue il rendering di argomento nel Visualizzatore della Guida.  
  
-   Funzionalità di Visual Studio \(nessuna opzione per VSP sostituire l'elenco di proprietà generato dalla funzionalità di Visual Studio\): F1 esegue il rendering di un argomento di Visual Studio nel Visualizzatore della Guida.  
  
 Impostare i valori del Registro di sistema seguente per abilitare F1 Fallback per il contenuto della Guida di fornitore. F1 Fallback significa che il Visualizzatore della Guida è impostato per cercare di F1 Guida in linea contenuto in linea e il contenuto del fornitore è installato localmente sul disco rigido degli utenti. Anche se l'impostazione predefinita per la Guida in linea Guida locale per il contenuto necessario controllare il Visualizzatore della Guida.  
  
1.  Impostare il **VendorContent** valore nella chiave del Registro di sistema di Guida 2.1:  
  
    -   Per i sistemi operativi a 32 bit:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent" \= DWORD: 00000001  
  
    -   Per i sistemi operativi a 64 bit:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent" \= DWORD: 00000001  
  
2.  Registrare lo spazio dei nomi partner sotto la chiave del Registro di sistema di Guida 2.1:  
  
    -   Per i sistemi operativi a 32 bit:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Partner*\\ \< namespace \>*  
  
         "percorso"\="offline"  
  
    -   Per i sistemi operativi a 64 bit:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Partner*\\ \< namespace \>*  
  
         "percorso"\="offline"  
  
 **Spazio dei nomi nativo l'analisi di base**  
  
 Per attivare l'analisi di base dello spazio dei nomi nativo, nel Registro di sistema aggiungendo un nuovo valore DWORD il nome del: BaseNativeNamespaces e impostarne il valore su 1 \(sotto la chiave di catalogo che si desidera supportare\).  Ad esempio, se si desidera utilizzare il catalogo di Visual Studio, è possibile aggiungere la chiave per il percorso:  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
 Quando una parola chiave F1 nel formato di CHE INTESTAZIONE o di metodi viene rilevato, il carattere '\/' verrà analizzato, determinando il costrutto seguente:  
  
-   INTESTAZIONE: sarà lo spazio dei nomi che può essere utilizzato per registrare nel Registro di sistema  
  
-   METODO: diventerà la parola chiave che viene passata tramite.  
  
 Si consideri ad esempio una libreria personalizzata denominata CustomLibrary e un metodo denominato MyTestMethod, quando un F1 arriva richiesta verrà formattato come `CustomLibrary/MyTestMethod`.  
  
 Un utente può quindi registrare CustomLibrary come spazio dei nomi nell'hive partner e fornire qualsiasi chiave percorso hanno l'esigenza di, e la parola chiave passata alla query sarà MyTestMethod.  
  
 **Attivare la Guida nell'IDE di strumento di debug**  
  
 Aggiungere la seguente chiave del Registro di sistema e il valore:  
  
 Tasto Guida HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\12.0\\Dynamic: Display Debug Output in valore commerciale: Sì  
  
 Nell'IDE, sotto la voce di menu della Guida in linea, selezionare "Debug il contesto della Guida"  
  
 **Contenuto dei metadati**  
  
 Nella tabella seguente, qualsiasi stringa che viene visualizzato tra parentesi è un segnaposto che deve essere sostituito con un valore riconosciuto. Ad esempio, in \< meta name\="Microsoft.Help.Locale" contenuto \= "\[codice di lingua\]" \/ \>, "\[codice di lingua\]" deve essere sostituito con un valore, ad esempio "en\-us".  
  
|Proprietà \(rappresentazione HTML\)|Descrizione|  
|-----------------------------------------|-----------------|  
|\< meta name\="Microsoft.Help.Locale" contenuto \= "\[codice lingua\]" \/ \>|Imposta le impostazioni locali per questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta e deve essere inserito sopra degli altri tag di Microsoft Help. Se non viene utilizzato questo tag, il testo del corpo dell'argomento è indicizzato con word breaker è associato con le impostazioni locali del prodotto, se è specificato; in caso contrario, en\-us word breaker viene utilizzato. Questo tag è conforme a RFC 4646 ISOC. Per garantire il corretto funzionamento di Microsoft Help, utilizzare questa proprietà anziché l'attributo di linguaggio generale.|  
|\< meta name\="Microsoft.Help.TopicLocale" contenuto \= "\[codice lingua\]" \/ \>|Imposta le impostazioni locali per questo argomento quando vengono utilizzate anche altre impostazioni locali. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta. Utilizzare questo tag quando il catalogo include il contenuto in più lingue. Più argomenti in un catalogo possono avere lo stesso ID, ma ognuno deve specificare un TopicLocale univoco. L'argomento che specifica un TopicLocale corrispondente alle impostazioni internazionali del catalogo è l'argomento che viene visualizzato il sommario. Tuttavia, tutte le versioni localizzate dell'argomento vengono visualizzate nei risultati della ricerca.|  
|\< title \> \[Title\] \< \/ title \>|Specifica il titolo di questo argomento. Questo tag è obbligatorio e deve essere utilizzato una sola volta in un argomento. Se il corpo dell'argomento non contiene una sezione \< div \> titolo, il titolo viene visualizzato nell'argomento e il sommario.|  
|\< nome meta \= "Microsoft.Help.Keywords" contenuto \= "\[aKeywordPhrase\]" \/ \>|Specifica il testo di un collegamento che viene visualizzato nel riquadro di indice del Visualizzatore della Guida. Quando si fa clic sul collegamento, viene visualizzato l'argomento. È possibile specificare più parole chiave di indice per un argomento, oppure è possibile omettere il tag se non si desidera che i collegamenti a questo argomento da visualizzare nell'indice. Parole chiave "K" da versioni precedenti della Guida in linea possono essere convertite in questa proprietà.|  
|\< meta name\="Microsoft.Help.Id" contenuto \= "\[TopicID\]" \/ \>|Imposta l'identificatore per questo argomento. Questo tag è obbligatorio e deve essere utilizzato una sola volta in un argomento. L'ID deve essere univoco tra gli argomenti nel catalogo con le stesse impostazioni internazionali. In un altro argomento, è possibile creare un collegamento a questo argomento utilizzando questo ID.|  
|\< meta name\="Microsoft.Help.F1" content\="\[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator\]"\/ \>|Specifica la parola chiave F1 in questo argomento. È possibile specificare più parole chiave F1 per un argomento, oppure è possibile omettere il tag se non si desidera che in questo argomento da visualizzare quando un utente dell'applicazione preme F1. In genere, viene specificata una sola parola chiave F1 per un argomento. Parole chiave "F" da versioni precedenti della Guida in linea possono essere convertite in questa proprietà.|  
|\< nome meta \= "Description" content \= "\[Descrizione dell'argomento\]" \/ \>|Fornisce un breve riepilogo del contenuto in questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta. Questa proprietà si accede direttamente dalla libreria di query. non è archiviato nel file di indice.|  
|\< meta name\="Microsoft.Help.TocParent" contenuto \= "\[parent\_Id\]" \/ \>|Specifica l'argomento padre di questo argomento nel sommario. Questo tag è obbligatorio e deve essere utilizzato una sola volta in un argomento. Il valore è Microsoft.Help.Id dell'elemento padre. Un argomento può disporre di un'unica posizione nella tabella dei contenuti. "\-1" è considerato l'ID di argomento per la radice del sommario. In [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)], tale pagina è home page del Visualizzatore della Guida. Questo è lo stesso motivo che aggiungiamo specificamente TocParent \=\-1 per alcuni argomenti per assicurarsi che vengono visualizzati nella parte superiore livello. Home page del Visualizzatore della Guida è una pagina di sistema e pertanto non sostituibili. Se un VSP tenta di aggiungere una pagina con un ID di \-1, si potrebbe ottenere aggiunto al set di contenuti, ma il Visualizzatore della Guida verrà sempre utilizzare la pagina system: home page di Visualizzatore della Guida|  
|\< meta name\="Microsoft.Help.TocOrder" contenuto \= "\[numero intero positivo\]" \/ \>|Specifica dove il sommario in questo argomento verrà visualizzato relativo relativi argomenti. Questo tag è obbligatorio e deve essere utilizzato una sola volta in un argomento. Il valore è un numero intero. Un argomento che specifica un valore integer di valore inferiore viene visualizzata sopra un argomento che specifica un valore più elevato numero intero.|  
|\< meta name\="Microsoft.Help.Product" contenuto \= "\[product code\]" \/ \>|Specifica del prodotto descritte in questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta. Queste informazioni possono inoltre essere specificate come un parametro viene passato all'indicizzatore della Guida.|  
|\< meta name\="Microsoft.Help.ProductVersion" contenuto \= "\[numero versione\]" \/ \>|Specifica la versione del prodotto descritte in questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta. Queste informazioni possono inoltre essere specificate come un parametro viene passato all'indicizzatore della Guida.|  
|\< meta name\="Microsoft.Help.Category" contenuto \= "\[string\]" \/ \>|Utilizzato dai prodotti per identificare le sezioni di contenuto. È possibile identificare più sottosezioni per un argomento, o se non si desidera che i collegamenti per identificare qualsiasi sottosezioni, è possibile omettere questo tag. Questo tag viene usato per archiviare gli attributi per TargetOS e TargetFrameworkMoniker quando un argomento viene convertito da una versione precedente della Guida in linea. Il formato del contenuto è AttributeName:AttributeValue.|  
|\< contenuto name\="Microsoft.Help.TopicVersion meta \="\[numero versione argomento\]"\/ \>|Specifica la versione dell'argomento quando esistono più versioni in un catalogo. Poiché Microsoft.Help.Id non è garantito che sia univoco, questo tag è obbligatorio quando più di una versione di un argomento presente in un catalogo, ad esempio, quando un catalogo contiene un argomento per .NET Framework 3.5 e un argomento per .NET Framework 4 e che entrambi contengano Microsoft.Help.Id stesso.|  
|\< nome meta \= "SelfBranded" content \= "\[TRUE o FALSE\]" \/ \>|Specifica se questo argomento viene utilizzato il pacchetto di personalizzazione di avvio di gestione librerie della Guida o un pacchetto di personalizzazione è specifico per l'argomento. Questo tag deve essere TRUE o FALSE. Se è TRUE, il pacchetto di personalizzazione per l'argomento associato sostituisce il pacchetto di personalizzazione che viene impostato all'avvio di gestione librerie della Guida in modo che l'argomento viene eseguito il rendering come previsto anche se differisce dal rendering di altro contenuto. Se è FALSE, l'argomento corrente viene eseguito il rendering in base al pacchetto di personalizzazione che viene impostato all'avvio di gestione librerie della Guida. Per impostazione predefinita, Gestione librerie della Guida si presuppone self\-personalizzazione su false, a meno che la variabile SelfBranded viene dichiarata come TRUE. Pertanto, non è necessario dichiarare \< nome meta \= "SelfBranded" content \= "FALSE" \/ \>.|  
  
### Creazione di un pacchetto di personalizzazione  
 La versione di Visual Studio include un numero di diversi prodotti Visual Studio, inclusi i Isolated e shell integrata per i partner di Visual Studio.  Ognuno di questi prodotti richiede un certo livello di contenuto della Guida basate sull'argomento personalizzazione supporto, univoco per il prodotto.  Negli argomenti di Visual Studio, ad esempio, necessario disporre di una presentazione coerente del marchio, mentre SQL Studio, che esegue il wrapping ISO Shell, richiede un proprio univoco della Guida contenuto per la personalizzazione di ogni argomento.  Un Partner di Shell integrata potrebbe essere necessario gli argomenti della Guida in linea per rientrare il contenuto della Guida del prodotto Visual Studio padre mantenendo i propri argomento personalizzazione.  
  
 Personalizzazione i pacchetti vengono installati per il prodotto che contiene il Visualizzatore della Guida.  Per i prodotti Visual Studio:  
  
-   Un pacchetto di personalizzazione di fallback \(Branding\_ \< locale \> mshc\) viene installato nella directory principale dell'applicazione 2.1 Visualizzatore della Guida \(esempio: C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\) per il language pack del Visualizzatore della Guida.  Viene utilizzato per i casi in cui non è installato prodotto personalizzazione pacchetto \(non è stato installato nessun contenuto\) o in cui il pacchetto di personalizzazione installato è danneggiato.  Si noti che gli elementi di Visual Studio \(logo e commenti\) vengono ignorati quando viene utilizzato il fallback radice app personalizzazione del pacchetto.  
  
-   Quando il contenuto di Visual Studio è installato dal servizio di pacchetto di contenuto, viene installato anche un pacchetto di personalizzazione \(per il primo scenario di installazione del contenuto di tempo\).  Se è presente un aggiornamento per il pacchetto di personalizzazione, l'aggiornamento viene installato quando si verifica il successivo aggiornamento del contenuto o l'azione di installazione del pacchetto aggiuntivi.  
  
 Il Visualizzatore della Guida Microsoft supporta la personalizzazione degli argomenti in base ai metadati di argomento.  
  
-   In cui i metadati di argomento definiscono self marchio \= true, l'argomento è di eseguire il rendering, non eseguire alcuna operazione \(per quanto riguarda la personalizzazione\).  
  
-   In cui i metadati di argomento definiscono self marchio \= false, utilizzare il pacchetto di personalizzazione associato TopicVendor del valore dei metadati.  
  
-   Contenuto in cui i metadati di argomento definiscono name\="Microsoft.Help.TopicVendor" \= \< pacchetto nome personalizzazione in fornitore MSHA \>, utilizzare il pacchetto di personalizzazione definito nel valore del contenuto.  
  
-   Si noti che all'interno del catalogo di Visual Studio, è disponibile un'applicazione di priorità dei pacchetti di personalizzazione.  Branding predefinito prima Visual Studio viene applicato e quindi, se definito nei metadati dell'argomento e supportato con la personalizzazione associata del pacchetto \(come definito in msha l'installazione\), il fornitore definito personalizzazione viene applicato come una sostituzione.  
  
 Elementi di personalizzazione in genere rientrano in tre categorie principali:  
  
-   Elementi di intestazione \(esempi collegamento feedback, responsabilità condizionale, logo\)  
  
-   Contenuto comportamenti \(ad esempio elementi di testo di controllo di espansione\/compressione e gli elementi di frammento di codice\)  
  
-   Elementi di un piè di pagina, ad esempio Copyright.  
  
 Gli elementi considerati come includono elementi personalizzati \(descritti in dettaglio in questa specifica\):  
  
-   Logo del catalogo\/prodotto \(ad esempio, Visual Studio\)  
  
-   Elementi di posta elettronica e collegamento di commenti e suggerimenti  
  
-   Dichiarazione di non responsabilità  
  
-   Testo di copyright  
  
 I file di supporto nel pacchetto di personalizzazione di Visualizzatore della Guida di Visual Studio includono:  
  
-   Grafica \(logo, le icone e così via\)  
  
-   Branding.js – supporto comportamenti del contenuto di file di script  
  
-   Branding.XML – stringhe che vengono usati in modo coerente tra il contenuto del catalogo.  Nota: per gli elementi di testo di localizzazione Visual Studio in branding.xml, includono locid \= "\< valore univoco \>"  
  
-   Branding.CSS – le definizioni di stile per la coerenza di presentazione  
  
-   Printing.CSS – definizioni di stile per la presentazione stampata coerente  
  
 Come indicato in precedenza, pacchetti di personalizzazione sono associati all'argomento:  
  
-   Quando SelfBranded \= false è definita nei metadati, l'argomento eredita il catalogo di personalizzazione del pacchetto  
  
-   O quando SelfBranded \= false e vi è un pacchetto di personalizzazione univoco definito nel MSHA e disponibili quando è installato il contenuto  
  
 Per l'implementazione di pacchetti personalizzati di personalizzazioni vsp \(contenuto VSP, SelfBranded \= True\), per continuare è possibile iniziare con il pacchetto di personalizzazione fallback \(installato con il Visualizzatore della Guida\) e modificare il nome del file come appropriato.  Il file mshc Branding\_ \< locale \> è un file zip con l'estensione del file modificato in mshc, è sufficiente così modificare l'estensione da mshc in. zip ed estrarre il contenuto.  Vedere di seguito per la personalizzazione di elementi del pacchetto e modificare come appropriato \(ad esempio, modificare il logo per il logo VSP e il riferimento per il logo nel file Branding.xml, aggiornare Branding.xml per specifiche VSP, ecc.\).  
  
 Al termine di tutte le modifiche, creare un file zip contenente gli elementi di personalizzazione desiderati e modificare l'estensione in mshc.  
  
 Per associare il pacchetto di personalizzazione personalizzato, creare MSHA che contiene il riferimento al file mshc personalizzazione con il contenuto mshc \(contenente gli argomenti\).  Vedere di seguito "MSHA" per creare una base MSHA.  
  
 Il file Branding.xml contiene un elementi di elenco utilizzato per il rendering in modo coerente del elementi specifici in un argomento quando l'argomento contiene \< meta name\="Microsoft.Help.SelfBranded" contenuto \= "false" \/ \>.  Elenco di elementi nel file Branding.xml Visual Studio è elencato di seguito.  Si noti che questo elenco deve essere utilizzato come modello per gli utilizzatori ISO Shell, in cui modificare questi elementi \(ad esempio logo, commenti e suggerimenti e Copyright\) per soddisfare i propri prodotti le esigenze di personalizzazione.  
  
 Nota: le variabili indicate da "{n}" sono le dipendenze del codice, rimuovere o modificare questi valori causerà errori e possibilmente arresto anomalo dell'applicazione. Gli identificatori di localizzazione \(esempio \_locID\="codesnippet.n"\) sono inclusi nel pacchetto di personalizzazione di Visual Studio.  
  
 **Branding.Xml**  
  
|||  
|-|-|  
|Funzionalità:|**CollapsibleArea**|  
|Utilizzo:|Espandere comprime controllo contenuto testo|  
|**Elemento**|**Valore**|  
|ExpandText|Espandi|  
|CollapseText|Comprimi|  
|Funzionalità:|**CodeSnippet**|  
|Utilizzo:|Testo del frammento di codice.  Nota: Il contenuto di frammento di codice con "Non sostanziale" spazio verrà modificato nello spazio.|  
|**Elemento**|**Valore**|  
|CopyToClipboard|Copia negli Appunti|  
|ViewColorizedText|Visualizza testo a colori|  
|CombinedVBTabDisplayLanguage|Visual Basic \(esempio\)|  
|VBDeclaration|Dichiarazione|  
|VBUsage|Utilizzo|  
|Funzionalità:|**Commenti e suggerimenti, piè di pagina e Logo**|  
|Utilizzo:|Fornire un controllo di commenti e suggerimenti per il cliente fornire commenti e suggerimenti sull'argomento corrente tramite posta elettronica.  Testo di copyright per il contenuto.  Definizione del logo.|  
|**Elemento**|**Valore \(queste stringhe possono essere modificate per soddisfare nuove esigenze adopter contenuto\).**|  
|CopyRight|© 2013 Microsoft Corporation. Tutti i diritti sono riservati.|  
|SendFeedback|\< href \= "{0}" \\{1\\} \> commenti e suggerimenti \< \/a \> in questo argomento a Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]|  
|LogoFileName|vs\_logo\_bk.gif|  
|LogoFileNameHC|vs\_logo\_wh.gif|  
|Funzionalità:|**Dichiarazione di non responsabilità**|  
|Utilizzo:|Un set di case specifici dichiarazioni di non responsabilità per la macchina contenuto tradotto.|  
|**Elemento**|**Valore**|  
|MT\_Editable|In questo articolo è stato tradotto. Se si dispone di una connessione a Internet, selezionare "Visualizza la Guida in linea" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese nello stesso momento.|  
|MT\_NonEditable|In questo articolo è stato tradotto. Se si dispone di una connessione a Internet, selezionare "Visualizza la Guida in linea" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese nello stesso momento.|  
|MT\_QualityEditable|In questo articolo è stato tradotto manualmente. Se si dispone di una connessione a Internet, selezionare "Visualizza la Guida in linea" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese nello stesso momento.|  
|MT\_QualityNonEditable|In questo articolo è stato tradotto manualmente. Se si dispone di una connessione a Internet, selezionare "Visualizza la Guida in linea" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese nello stesso momento.|  
|MT\_BetaContents|In questo articolo è stato tradotto per una versione preliminare. Se si dispone di una connessione a Internet, selezionare "Visualizza la Guida in linea" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese nello stesso momento.|  
|MT\_BetaRecycledContents|In questo articolo è stato tradotto manualmente per una versione preliminare. Se si dispone di una connessione a Internet, selezionare "Visualizza la Guida in linea" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese nello stesso momento.|  
|Funzionalità:|**Configurazione LinkTable**|  
|Utilizzo:|Supporto per collegamenti ad argomenti in linea|  
|**Elemento**|**Valore**|  
|LinkTableTitle|Tabella di collegamento|  
|TopicEnuLinkText|Consente di visualizzare la versione inglese \< \/a \> di questo argomento è disponibile nel computer in uso.|  
|TopicOnlineLinkText|Visualizzare questo argomento \< href \= "{0}" \\{1\\} \> online \< \/a \>|  
|OnlineText|In linea|  
|Funzionalità:|**Controllo Audio video**|  
|Utilizzo:|Visualizza gli elementi e il testo per il contenuto video|  
|**Elemento**|**Valore**|  
|MultiMediaNotSupported|Internet Explorer 9 o versione successiva deve essere installato per supportare il contenuto di {0}.|  
|VideoText|la visualizzazione dei video|  
|AudioText|flusso audio|  
|OnlineVideoLinkText|\< p \> per visualizzare il video associato a questo argomento, fare clic su {0} \< href \= "\\ \\ " \> \\{2\\}here \< \/a \>. \<\/p \>|  
|OnlineAudioLinkText|\< p \> per ascoltare l'audio associata a questo argomento, fare clic su {0} \< href \= "\\ \\ " \> \\{2\\}here \< \/a \>. \<\/p \>|  
|Funzionalità:|**Controllo contenuto non installato**|  
|Utilizzo:|Elementi di testo \(stringhe\) utilizzati per il rendering di contentnotinstalled.htm|  
|**Elemento**|**Valore**|  
|ContentNotInstalledTitle|Nessun contenuto è stato trovato nel computer in uso.|  
|ContentNotInstalledDownloadContentText|\< p \> per scaricare il contenuto al computer in uso, \< href \= "{0}" \\{1\\} \> fare clic sulla scheda Gestisci \< \/a \>. \<\/p \>|  
|ContentNotInstalledText|\< p \> No contenuto viene installato nel computer in uso. Consultare l'amministratore locale della Guida contenuto installazione. \<\/p \>|  
|Funzionalità:|**Controllo di argomento non trovato**|  
|Utilizzo:|Elementi di testo \(stringhe\) utilizzati per il rendering di topicnotfound.htm|  
|**Elemento**|**Valore**|  
|TopicNotFoundTitle|Impossibile trovare l'argomento richiesto nel computer in uso.|  
|TopicNotFoundViewOnlineText|\< p \> l'argomento richiesto non è stato trovato nel computer in uso, ma è possibile \< href \= "{0}" \\{1\\} \> visualizzare l'argomento online \< \/a \>. \<\/p \>|  
|TopicNotFoundDownloadContentText|\< p \> vedere il riquadro di spostamento per i collegamenti agli argomenti simili, o \< href \= "{0}" \\{1\\} \> fare clic sulla scheda Gestisci \< \/a \> per scaricare il contenuto nel computer. \<\/p \>|  
|TopicNotFoundText|\< p \> l'argomento richiesto non è stato trovato nel computer. \<\/p \>|  
|Funzionalità:|**Argomento danneggiato controllo**|  
|Utilizzo:|Elementi di testo \(stringhe\) utilizzati per il rendering di topiccorrupted.htm|  
|**Elemento**|**Valore**|  
|TopicCorruptedTitle|Impossibile visualizzare l'argomento richiesto.|  
|TopicCorruptedViewOnlineText|\< p \> il Visualizzatore della Guida non è in grado di visualizzare l'argomento richiesto. Potrebbe essersi verificato un errore nel contenuto dell'argomento o una dipendenza del sistema sottostante. \<\/p \>|  
|Funzionalità:|**Controllo Home Page**|  
|Utilizzo:|Testo che supporta la visualizzazione del contenuto del nodo di livello superiore del Visualizzatore della Guida.|  
|**Elemento**|**Valore**|  
|HomePageTitle|Home page di Visualizzatore della Guida|  
|HomePageIntroduction|\< p \> Benvenuti in Microsoft Help Viewer, una fonte di informazioni per tutti coloro che utilizzano strumenti, prodotti, tecnologie e servizi Microsoft fondamentale. Il Visualizzatore della Guida consente di accedere a informazioni di riferimento e sulle procedure, codice di esempio, articoli tecnici e altre. Per trovare il contenuto che è necessario, consultare il sommario, utilizzare la ricerca full\-text o esplorare il contenuto tramite l'indice \(parola chiave\). \<\/p \>|  
|HomePageContentInstallText|\< p \>\< br \/ \> utilizzo di \< href \= "{0}" \\{1\\} \> scheda Gestisci contenuto \< \/a \> per eseguire le operazioni seguenti: \< ul \>\< li \> Aggiungi contenuto nel computer. \<\/li \>\< li \> verifica degli aggiornamenti per il contenuto locale. \<\/li \>\< li \> rimuove il contenuto dal computer. \<\/li \>\< \/ ul \>\< \/ p \>|  
|HomePageInstalledBooks|Libri installati|  
|HomePageNoBooksInstalled|Nessun contenuto è stato trovato nel computer in uso.|  
|HomePageHelpSettings|Impostazioni del contenuto della Guida in linea|  
|HomePageHelpSettingsText|\< p \> l'impostazione corrente è la Guida locale. Il Visualizzatore della Guida consente di visualizzare il contenuto installato nel computer in uso. \< br \/ \> per modificare l'origine del contenuto della Guida, nella barra dei menu di Visual Studio, scegliere \< span style \= "{0}" \> Guida in linea, Imposta preferenza Guida \< \/ span \>. \< br \/ \>\< \/ p \>|  
|MegaByte|MB|  
  
 **Branding.js**  
  
 Il file branding.js contiene JavaScript utilizzato dagli elementi di personalizzazione del Visualizzatore della Guida di Visual Studio.  Di seguito è riportato un elenco degli elementi di personalizzazione e la funzione di supporto JavaScript.  Tutte le stringhe da localizzare per questo file sono definite nella sezione "Stringhe localizzabili" nella parte superiore di questo file.  Si noti che è stato creato il file ICL per stringhe localizzate all'interno del file branding.js.  
  
||||  
|-|-|-|  
|**Funzionalità di personalizzazione**|**Funzione JavaScript**|**Descrizione**|  
|Var...||Definire le variabili|  
|Ottenere il linguaggio del codice utente|setUserPreferenceLang|esegue il mapping di un indice \# per il linguaggio del codice|  
|Impostare e ottenere i valori dei cookie|getCookie, setCookie||  
|Membri ereditati|changeMembersLabel|Espandi\/Comprimi membro ereditato|  
|Quando SelfBranded \= False|onLoad|Leggere la stringa di query per verificare se si tratta di una richiesta di stampa.  Impostare tutte le codesnippets di concentrarsi sulla scheda Preferiti utente.  In caso di stampa isPrinterFriendly richiesta quindi imposta su true. Controllare la modalità contrasto elevato.|  
|Frammento di codice|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||Scheda Modifica vengono||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|scrivere tutti l'oggetto controllo comprimibile in elenco.|  
||CA\_Click|in base allo stato dell'area comprimibile, definisce quali immagini e testo per presentare|  
|Supporto del contrasto per Logo|isBlackBackground\(\)|Chiamato per determinare se in background è nero.  Solo quando accurata in modalità contrasto elevato.|  
||isHighContrast\(\)|Utilizzare un intervallo di colorato per rilevare la modalità contrasto elevato|  
||onHighContrast\(black\)|Chiamato quando viene rilevato il contrasto elevato|  
|Funzionalità LST|||  
||addToLanSpecTextIdSet\(id\)||  
||updateLST\(currentLang\)||  
||getDevLangFromCodeSnippet\(lang\)||  
|Funzionalità multimediali|didascalia \(inizio, fine, testo, stile\)||  
||findAllMediaControls\(normalizedId\)||  
||getActivePlayer\(normalizedId\)||  
||captionsOnOff\(id\)||  
||toSeconds\(t\)||  
||getAllComments\(node\)||  
||styleRectify \(styleName, styleValue\)||  
||showCC\(id\)||  
||SUBTITLE\(ID\)||  
  
 **FILE HTM**  
  
 Il pacchetto di personalizzazione contiene un set di file HTM che supportano scenari per la comunicazione di informazioni sulla chiave agli utenti di contenuto della Guida in linea, ad esempio una home page che contiene una sezione che descrive il set di contenuti vengono installati e le pagine che informa l'utente quando risulta impossibile trovare argomenti nel set di argomenti locali. Si noti che è possono modificare questi file HTM per prodotto.  ISO Shell fornitori sono in grado di eseguire il pacchetto di personalizzazione predefinito e modificare il comportamento e il contenuto di queste pagine per suite la necessità.  Questi file, consultare i rispettivi pacchetti personalizzazioni affinché i tag di personalizzazioni ottenere il contenuto corrispondente dal file branding.xml.  
  
||||  
|-|-|-|  
|**File**|**Uso**|**Origine del contenuto visualizzato**|  
|Homepage|Si tratta di una pagina che visualizza contenuto attualmente installato e qualsiasi altro messaggio appropriato per presentare all'utente il relativo contenuto.  Questo file contiene il contenuto aggiuntivo meta dati attributo "Microsoft.Help.Id" \= "\-1" che inserisce questo contenuto nella parte superiore del sommario del contenuto locale.||  
||\< META\_HOME\_PAGE\_TITLE\_ADD \/ \>|Branding.XML, tag \< HomePageTitle \>|  
||\< HOME\_PAGE\_INTRODUCTION\_SECTION\_ADD \/ \>|Branding.XML, tag \< HomePageIntroduction \>|  
||\< HOME\_PAGE\_CONTENT\_INSTALL\_SECTION\_ADD \/ \>|Branding.XML, tag \< HomePageContentInstallText \>|  
||\< HOME\_PAGE\_BOOKS\_INSTALLED\_SECTION\_ADD \/ \>|Intestazione sotto la sezione Branding.xml tag \< HomePageInstalledBooks \>, i dati generati dall'applicazione, \< HomePageNoBooksInstalled \> quando non sono installati alcuna documentazione.|  
||\< HOME\_PAGE\_SETTINGS\_SECTION\_ADD \/ \>|Intestazione sotto la sezione Branding.xml tag \< HomePageHelpSettings \> testo della sezione \< HomePageHelpSettingsText \>.|  
|topiccorrupted.htm|Quando è presente un argomento nel set di locale, ma per qualche motivo non può essere visualizzato \(contenuto danneggiato\).||  
||\< META\_TOPIC\_CORRUPTED\_TITLE\_ADD \/ \>|Branding.XML, tag \< TopicCorruptedTitle \>|  
||\< TOPIC\_CORRUPTED\_SECTION\_ADD \/ \>|Branding.XML, tag \< TopicCorruptedViewOnlineText \>|  
|topicnotfound.htm|Quando un argomento non viene trovato il contenuto locale impostata né disponibile online||  
||\< META\_TOPIC\_NOT\_FOUND\_TITLE\_ADD \/ \>|Branding.XML, tag \< TopicNotFoundTitle \>|  
||\< META\_TOPIC\_NOT\_FOUND\_ID\_ADD \/ \>|Branding.XML, tag \< TopicNotFoundViewOnlineText \> \+ \< TopicNotFoundDownloadContentText \>|  
||\< TOPIC\_NOT\_FOUND\_SECTION\_ADD \/ \>|Branding.XML, tag \< TopicNotFoundText \>|  
|contentnotinstalled.htm|Quando non è disponibile contenuto locale per il prodotto installato.||  
||\< META\_CONTENT\_NOT\_INSTALLED\_TITLE\_ADD \/ \>|Branding.XML, tag \< ContentNotInstalledTitle \>|  
||\< META\_CONTENT\_NOT\_INSTALLED\_ID\_ADD \/ \>|Branding.XML, tag \< ContentNotInstalledDownloadContentText \>|  
||\< CONTENT\_NOT\_INSTALLED\_SECTION\_ADD \/ \>|Branding.XML, tag \< ContentNotInstalledText \>|  
  
 **File CSS**  
  
 Il pacchetto Visual Studio Guida Visualizzatore personalizzazione contiene due file css per il supporto coerente presentazione del contenuto della Guida di Visual Studio:  
  
-   Branding.CSS: contiene gli elementi di css per il rendering dove SelfBranded \= false  
  
-   Printer.CSS: contiene gli elementi di css per il rendering dove SelfBranded \= false  
  
 Branding.CSS file include le definizioni per la presentazione di argomento di Visual Studio \(avvertenza è che il branding.css contenuti nel mshc Branding\_ \< locale \> dal servizio pacchetto potrebbe cambiare\).  
  
 **File di immagine**  
  
 Il contenuto di Visual Studio consente di visualizzare un logo di Visual Studio, nonché altri elementi grafici.  Seguito è riportato l'elenco completo dei file di immagine nel pacchetto di personalizzazione di Visualizzatore della Guida di Visual Studio.  
  
||||  
|-|-|-|  
|**File**|**Uso**|**Esempi**|  
|Clear.gif|Per eseguire il rendering Area comprimibile||  
|footer\_slice.gif|Presentazione di piè di pagina||  
|info\_icon.gif|Utilizzato per la visualizzazione di informazioni|Dichiarazione di non responsabilità|  
|online\_icon.gif|Questa icona viene associata a collegamenti online||  
|tabLeftBD.gif|Per eseguire il rendering del contenitore di frammento di codice||  
|tabRightBD.gif|Per eseguire il rendering del contenitore di frammento di codice||  
|vs\_logo\_bk.gif|Utilizzata per normali contrasto logo riferimenti come definito nel tag Branding.xml \< LogoFileName \>.  Per i prodotti Visual Studio, nome logo è vs\_logo\_bk.gif.||  
|vs\_logo\_wh.gif|Utilizzata per riferimenti normale logo elevata come definito nel tag Branding.xml \< LogoFileNameHC \>.  Per i prodotti Visual Studio, nome logo è vs\_logo\_wh.gif.||  
|ccOff.png|Immagine di sottotitoli codificati||  
|ccOn.png|Immagine di sottotitoli codificati||  
|ImageSprite.png|Per eseguire il rendering Area comprimibile|Espandere o comprimere l'immagine|  
  
### Distribuzione di un set di argomenti  
 Si tratta di un'esercitazione molto semplice e rapida per la creazione di una distribuzione di contenuto del Visualizzatore della Guida imposta comprendere un file MSHA e il set di file CAB o MSHC contenente gli argomenti. Il MSHA è un file XML che descrive un set di file CAB o i file MSHC. Il Visualizzatore della Guida può leggere MSHA per ottenere un elenco di contenuti \(i. File CAB o. File MSHC\) disponibili per l'installazione locale.  
  
 Questo è solo una panoramica che descrive lo schema XML di base per MSHA di Visualizzatore della Guida.  Si noti che è un esempio di implementazione di sotto di questa breve panoramica e il campionamento HelpContentSetup. msha.  
  
 Il nome del MSHA, ai fini di questa panoramica è HelpContentSetup. msha \(il nome del file può essere qualsiasi, con l'estensione. MSHA\). HelpContentSetup. msha \(ad esempio riportato di seguito\) deve contenere un elenco dei file CAB o MSHCs disponibili.  Si noti che il tipo di file deve essere coerenza all'interno di MSHA \(non supporta una combinazione di tipi di file CAB e MSHA\). Per ogni file CAB o MSHC, dovrebbe esserci un \< div classe \= "pacchetto" \>... \< \/ div \> \(vedere l'esempio riportato di seguito\).  
  
 Nota: nell'esempio di implementazione seguente, è stato incluso il pacchetto di personalizzazione. Questo è importante includere per ottenere i necessari gli elementi di rendering del contenuto di Visual Studio e i comportamenti del contenuto.  
  
 Esempio di file helpcontentsetup. msha: \(sostituire "contenuto set nome 1" e "contenuto set nome 2" e così via con i nomi dei file.\)  
  
```  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div>.  
  
```  
  
1.  Creare una cartella locale, è simile a "C:\\SampleContent"  
  
2.  In questo esempio utilizzeremo file MSHC per contenere gli argomenti.  Un MSHC è un file zip con l'estensione del file modificato da ZIP a. MSHC.  
  
3.  Creare il seguito HelpContentSetup. msha come file di testo \(il blocco note è stato usato per creare il file\) e salvarlo nella cartella indicati sopra \(vedere il passaggio 1\).  
  
 Si noti che la classe "Personalizzazione" esista e sia univoco. La personalizzazione mshc è incluso in questa panoramica in modo che il contenuto installato disporrà del marchio e i comportamenti di contenuto presenti il MSHCs avrà supporto appropriato per gli elementi contenuti nel pacchetto di personalizzazione. In caso contrario, si verificheranno degli errori quando il sistema cerca elementi di supporto che non fanno parte di copiati \(installata\) del contenuto.  
  
 Per ottenere il pacchetto di personalizzazione di Visual Studio, copiare file Branding\_en US.mshc \\Microsoft Help Viewer\\v2.1\\ C:\\Program Files \(x86\) nella cartella di lavoro.  
  
```html  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div> <div class="package"> <span class="packageType">branding</span> <span class="name">Branding_en-US</span> <span class="deployed">True</span> <a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a> </div> </div> </body> </html>  
  
```  
  
 **Riepilogo**  
  
 Utilizzo ed estensione i passaggi sopra descritti consentirà vsp distribuire i relativi set di contenuti per il Visualizzatore della Guida di Visual Studio.  
  
### Aggiunta della Guida di Visual Studio Shell \(Integrated e isolata\)  
 **Introduzione**  
  
 Questa procedura dettagliata viene illustrato come incorporare il contenuto della Guida in un'applicazione di Visual Studio Shell e quindi distribuirlo.  
  
 **Requisiti**  
  
1.  [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 isolato Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
 **Panoramica**  
  
 Il [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Shell è una versione di [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] IDE in cui è possibile basare un'applicazione. Tali applicazioni contengono Shell isolata con estensioni creati dall'utente. Utilizzare i modelli di progetto Shell isolata sono inclusi nel [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] SDK, compilare estensioni.  
  
 I passaggi di base per la creazione di un'applicazione basata su Shell isolata e la Guida:  
  
1.  Ottenere il [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] ISO Shell redistributable \(download di Microsoft\).  
  
2.  In Visual Studio, creare un'estensione della Guida che si basa su Shell isolata, ad esempio, l'estensione per la Guida di Contoso è descritto più avanti in questa procedura dettagliata.  
  
3.  Eseguire il wrapping dell'estensione e la Shell di ISO redistributable in una distribuzione MSI \(un programma di installazione dell'applicazione\). Questa procedura dettagliata non include un passaggio di configurazione.  
  
 Creare un archivio del contenuto di Visual Studio. Per lo scenario di Shell integrata, modificare Visual Studio12 per il nome del catalogo prodotti come segue:  
  
-   Creare cartella C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12.  
  
-   Creare un file denominato Catalogtype e aggiungerlo alla cartella. Il file deve contenere le righe di codice seguenti:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
 Definire l'archivio contenuto nel Registro di sistema. Per la Shell integrata, modificare il nome del catalogo prodotti VisualStudio12:  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
     Chiave: Valore stringa LocationPath: C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12\\en\-us  
  
     Chiave: Valore stringa CatalogName: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] documentazione  
  
 **Creare il progetto**  
  
 Per creare un'estensione della Shell isolata:  
  
1.  In Visual Studio, in **File**, scegliere **Nuovo progetto**, in **altri tipi di progetto** scegliere **estendibilità**, quindi scegliere  **Visual Studio Shell isolata**. Denominare il progetto `ContosoHelpShell`\) per creare un progetto di estensibilità in base al modello di Visual Studio Shell isolata.  
  
2.  In Esplora soluzioni, nel progetto ContosoHelpShellUI, nella cartella file di risorse, aprire ApplicationCommands.vsct. Assicurarsi che questa riga di commento \(cercare "No\_Help"\): `<!-- <define name=“No_HelpMenuCommands”/> -->`  
  
3.  Premere il tasto F5 per compilare ed eseguire **Debug**. Nell'istanza sperimentale di IDE Shell isolata, scegliere il **Guida** menu. Assicurarsi che il **Visualizza Guida**, **Aggiungi e Rimuovi contenuto della Guida**, e **Imposta preferenza Guida** i comandi vengono visualizzati.  
  
4.  In Esplora soluzioni, nel progetto ContosHelpShell, nella cartella della personalizzazione della Shell, aprire ContosoHelpShell.pkgdef. Per definire il catalogo della Guida di Contoso, aggiungere le righe seguenti:  
  
    ```  
    [$RootKey$\Help] "Product"="Contoso" "Catalog"="Contoso" “Version"="100" "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  In Esplora soluzioni, nel progetto ContosHelpShell, nella cartella della personalizzazione della Shell, aprire ContosoHelpShell.Application.pkgdef. Per abilitare F1 Guida in linea, aggiungere le righe seguenti:  
  
    ```  
    // F1 Help Provider [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="13407" "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}" @="Help3 Provider" [$RootKey$\HelpProviders] @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}" [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="Help3 Provider" @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  In Esplora soluzioni, nel menu di scelta rapida della soluzione ContosoHelpShell, scegliere il **proprietà** voce di menu. In **le proprietà di configurazione**, selezionare **Configuration Manager**. Nel **configurazione** colonna, modificare ogni valore di "Debug" in "Rilascio".  
  
7.  Compilare la soluzione. Consente di creare un set di file in una cartella di rilascio, che verrà usata nella sezione successiva.  
  
 Per testare questo come se distribuita:  
  
1.  Il computer si distribuisce Contoso per installare scaricato da ISO Shell \(sopra\).  
  
2.  Creare una cartella \\\\Program Files \(x86\) \\ e denominarla `Contoso`.  
  
3.  Copiare il contenuto dalla cartella della versione ContosoHelpShell \\\\Program Files \(x86\) \\Contoso\\ cartella.  
  
4.  Avviare l'Editor del Registro di sistema scegliendo  **eseguire** nel **avviare** menu e immettere `Regedit`. Nell'editor del Registro di sistema, scegliere **File**, e quindi **importazione**. Passare alla cartella del progetto ContosoHelpShell. Nella sottocartella ContosoHelpShell, scegliere ContosoHelpShell.reg.  
  
5.  Creare un archivio del contenuto:  
  
     Per la Shell ISO \- creare un archivio contenuto Contoso C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\ContosoDev12  
  
     Per [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Integrated Shell, creare una cartella C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12  
  
6.  Creare Catalogtype e aggiungere all'archivio del contenuto \(passaggio precedente\) che contiene:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Aggiungere le seguenti chiavi del Registro di sistema:  
  
     HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12Key: Valore stringa LocationPath:  
  
     Per ISO Shell:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
     [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Shell integrata:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\\\en\-us  
  
     Chiave: Valore stringa CatalogName: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] documentazione. Per ISO Shell, questo è il nome del catalogo.  
  
8.  Copiare il contenuto \(file CAB o MSHC e MSHA\) in una cartella locale.  
  
9. Shell integrata riga di comando per il test dell'archivio del contenuto. Per ISO Shell, modificare i valori di catalogo e launchingApp come appropriato in base al prodotto.  
  
     Metodo di \/helpQuery \/catalogName VisualStudio12 "C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\\HlpViewer.exe" \= "pagina & id \= ContosoTopic0" \/launchingApp Microsoft VisualStudio, 12.0  
  
10. Avviare l'applicazione Contoso \(dalla radice dell'applicazione Contoso\). All'interno della Shell di ISO, scegliere il **Guida** voce di menu e modificare il **Imposta preferenza Guida** a **utilizza Guida locale**.  
  
11. All'interno della shell, scegliere il **Guida** voce di menu, quindi **Visualizza Guida**. Deve essere avviato il Visualizzatore della Guida locale. Scegliere la scheda **Gestisci contenuto**. In **origine di installazione**, scegliere il **disco** pulsante di opzione. Scegliere il **...** pulsante e passare alla cartella locale contenente il contenuto di Contoso \(copiato nella cartella locale nel passaggio precedente\). Scegliere il HelpContentSetup. msha. Contoso deve ora visualizzata come un libro nelle selezioni della Rubrica. Scegliere **Aggiungi**, quindi scegliere il **aggiornamento** pulsante \(nell'angolo inferiore destro\).  
  
12. All'interno dell'IDE di Contoso, premere il tasto F1 per testare le funzionalità di F1.  
  
### Risorse aggiuntive  
 Per l'API di Runtime, vedere [Windows API della Guida](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
 Per ulteriori informazioni su come sfruttare le API della Guida, vedere [esempi di codice del Visualizzatore della Guida](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
 Per fornire commenti e suggerimenti su questi componenti, utilizzare [Microsoft Connect](http://connect.microsoft.com/).  
  
 Inviare suggerimenti sulle funzionalità di [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
 Per ottenere ulteriore assistenza, provare il [Guida e documentazione per sviluppatori MSDN forum](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
 Gli aggiornamenti in rilievo problema, vedere il [file Leggimi di Visualizzatore della Guida](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
 Per contattare direttamente il team PM Visualizzatore della Guida, inviare tramite posta elettronica a hlpfdbk@microsoft.com