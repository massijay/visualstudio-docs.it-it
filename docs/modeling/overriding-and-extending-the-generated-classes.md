---
title: "Override ed estensione delle classi generate | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, fornitura di classi sottoponibili a override"
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 15
caps.handback.revision: 15
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Override ed estensione delle classi generate
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La definizione di modello DSL è una piattaforma su cui è possibile compilare un insieme completo di strumenti basati su un linguaggio specifico di dominio.  Molti estensioni e adattamenti possono essere sottoposti a override e distribuendo uniformemente le classi generate dalla definizione di modello DSL.  Queste classi non includono solo le classi di dominio che è stato definito in modo esplicito nel diagramma della definizione di modello DSL, ma anche altre classi che definiscono la casella degli strumenti, esplora modelli scegliere da, serializzazione, e così via.  
  
## Meccanismi di estensibilità  
 Diversi meccanismi sono forniti per consentire di estendere il codice generato.  
  
### Metodi di override in una classe parziale  
 Definizioni di classe parziali consentono della classe sia definita in più punti.  Ciò consente di separare il codice generato dal codice scritto personalmente.  Nel codice manualmente\-scritto, è possibile eseguire l'override delle classi ereditate da codice generato.  
  
 Ad esempio, se nella definizione di modello DSL si definisce una classe di dominio denominata `Book`, è possibile scrivere codice personalizzato che aggiunge i metodi di override:  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  I metodi di override in una classe generata, scrivere sempre il codice di un file che è separato dai file generati.  In genere, il file è contenuto in una cartella denominata CustomCode.  Se si apportano modifiche al codice generato, andranno perse quando rigenerate il codice dalla definizione di modello DSL.  
  
 Per individuare quali metodi è possibile eseguire l'override di, l'override del tipo nella classe, seguito da uno spazio.  La descrizione comando IntelliSense viene indicato che metodi possono essere sottoposti a override.  
  
### Doppio classi Derivate  
 La maggior parte dei metodi nelle classi generate vengono ereditati da un set prestabilito di classi negli spazi dei nomi modellazione.  Tuttavia, alcuni metodi sono definiti nel codice generato.  In genere, non è possibile eseguirne l'override, non è possibile eseguire l'override in una classe parziale i metodi definiti in un'altra definizione parziale della stessa classe.  
  
 Tuttavia, è possibile eseguire l'override di questi metodi impostando **genera il doppio derivato** flag per la classe di dominio.  Ciò comporta due classi a essere generata, una che è una classe base astratta dell'altro.  Tutte le definizioni di proprietà e metodi nella classe base e solo il costruttore nella classe derivata.  
  
 Ad esempio, in Library.dsl, `CirculationBook` la classe di dominio ha  `Generates``Double Derived` insieme di proprietà su  `true`.  Il codice generato per la classe di dominio contiene due classi:  
  
-   `CirculationBookBase`, ovvero un estratto e contenente tutti i metodi e proprietà.  
  
-   `CirculationBook`, che viene derivato  `CirculationBookBase`.  È vuoto, ad eccezione dei costruttori.  
  
 Per eseguire l'override del metodo, si crea una definizione parziale della classe derivata come `CirculationBook`.  È possibile ignorare i metodi generati dai metodi ereditati dal framework di modellizzazione.  
  
 È possibile utilizzare questo metodo con tutti i tipi di elementi, inclusi gli elementi del modello, le relazioni, forme, i diagrammi e i connettori.  È inoltre possibile eseguire l'override dei metodi di altre classi generate.  Alcune classi generate come il ToolboxHelper doppio vengono derivate sempre.  
  
### costruttori personalizzati  
 Non è possibile eseguire l'override di un costruttore.  Anche le classi derivate doppio, il costruttore deve trovarsi nella classe derivata.  
  
 Se si desidera fornire diventi proprietaria del costruttore, a tale scopo `Has Custom Constructor` per la classe di dominio nella definizione di modello DSL.  Quando si fa clic su **Trasformazione di tutti i modelli**, il codice generato non includerà un costruttore per la classe.  Includerà una chiamata al costruttore mancante.  Ciò comporta una segnalazione errori quando si compila la soluzione.  Fare doppio clic sulla segnalazione errori per visualizzare un commento nel codice generato che gli spieghi cosa è necessario fornire.  
  
 Scrivere una definizione di classe parziale di un file che è separato dai file generati e fornire al costruttore.  
  
### punti di estensione contrassegnati  
 Un punto di estensione denominato è un punto della definizione di modello DSL in cui è possibile impostare una proprietà o una casella di controllo per indicare che forniscono un metodo personalizzato.  i costruttori personalizzati sono un esempio.  Altri esempi includono impostare `Kind` per una proprietà di un dominio all'archiviazione calcolata o personalizzata o impostare  **Viene personalizzato** flag in un generatore di connessione.  
  
 In ogni caso, quando si imposta il flag e rigenerate il codice, un errore di compilazione risulterete.  Fare doppio clic sull'errore per visualizzare un commento che gli spieghi cosa è necessario fornire.  
  
### Regole  
 Il gestore delle transazioni consente di definire regole da eseguire prima della fine di una transazione in cui un evento definito si è verificato, ad esempio una modifica in una proprietà.  Le regole vengono in genere utilizzate per gestire il sincronismo tra i diversi elementi nell'archivio.  Ad esempio, le regole vengono utilizzate per assicurarsi che il diagramma visualizza lo stato corrente del modello.  
  
 Le regole definite nella per\-classe, pertanto non è necessario includere codice che registra la regola per ogni oggetto.  Per ulteriori informazioni, vedere [Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).  
  
### Eventi dell'archivio  
 L'archivio di modellizzazione fornisce un meccanismo degli eventi che è possibile utilizzare per l'ascolto di tipi specifici di modifica nell'archivio, incluse l'aggiunta e l'eliminazione di elementi, modificare i valori delle proprietà, e così via.  I gestori eventi vengono chiamati dopo la fine della transazione nella quale sono state apportate le modifiche.  In genere, questi eventi vengono utilizzati per aggiornare le risorse all'esterno dell'archivio.  
  
### eventi di .NET  
 È possibile sottoscrivere ad alcuni eventi sulle forme.  Ad esempio, è possibile restare in attesa dei clic del mouse su una forma.  È necessario scrivere il codice che sottoscrive l'evento per ciascun oggetto.  Questo codice può essere scritto nell'override di InitializeInstanceResources\(\).  
  
 Alcuni eventi vengono generati per ShapeFields, che vengono utilizzati per disegnare elementi Decorator su una forma.  Per un esempio, vedere [Procedura: intercettare un clic su una forma o su un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 Questi eventi in genere non si verificano in una transazione.  È necessario creare una transazione se si desidera apportare modifiche nell'archivio.