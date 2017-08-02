---
title: "Informazioni sui linguaggi specifici del dominio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio"
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 26
---
# Informazioni sui linguaggi specifici del dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A differenza di un linguaggio per tutti gli utilizzi ad esempio c\# o UML, un linguaggio \(DSL\) specifico di dominio è progettato per esprimere le istruzioni in uno spazio particolare di problema, o al dominio.  
  
 DSLs noto include le espressioni regolari e SQL.  Ogni modello DSL è molto più efficace di un linguaggio di utilizzo generale per la descrizione delle operazioni sulle stringhe di testo o in un database, ma è molto peggiorando per descrivere le idee che sono esterno il relativo ambito.  Le singole industrie anche dispongono di un proprio DSLs.  Ad esempio, nelle telecomunicazioni, i linguaggi di descrizione di chiamata sono ampiamente utilizzate per specificare la sequenza di stati in una telefonata e in di viaggio æreo uno standard DSL è utilizzato per descrivere le prenotazioni di volo.  
  
 L'azienda e il progetto si occupano di impostare speciali di concetti che possono essere descritti con un modello DSL.  Ad esempio, è possibile definire un modello DSL per una di queste applicazioni:  
  
-   Piano di percorsi di navigazione in un sito Web.  
  
-   Schemi elettrici per i componenti di.  
  
-   Reti di nastri trasportatori e dell'attrezzatura di gestione dei bagagli per un società.  
  
 Quando si progetta un modello DSL, definire un oggetto *classe di dominio* per ognuno dei concetti importanti nel dominio, ad esempio una pagina Web, una lampada, o un banco dell'aeroporto.  Si definisce *relazioni di dominio* come il collegamento ipertestuale, il cavo, o un nastro trasportatore per collegare i concetti.  
  
 Gli utenti del modello DSL creano *modelli.* i modelli sono *istanze* il modello DSL.  Ad esempio, descrive un particolare sito Web, oppure i collegamenti di un determinato dispositivo, o del sistema di gestione dei bagagli in un società particolare.  
  
 Gli utenti possono visualizzare un modello come un diagramma o come Windows Form.  I modelli possono essere visualizzati come XML, che indica il modo in cui vengono archiviati.  Quando si definisce un linguaggio specifico di dominio, definite come istanze di ogni classe di dominio e le relazioni vengono visualizzati sullo schermo dell'utente.  Un modello DSL tipico visualizzata come una raccolta di icone o di rettangoli connessi dalle frecce.  
  
 Nella figura seguente viene illustrato un piccolo modello in un modello DSL diagrammatico:  
  
 ![Modello della struttura ad albero della famiglia Tudor](~/docs/modeling/media/tudor_familytreemodel.png "Tudor\_FamilyTreeModel")  
  
## Le operazioni che è possibile eseguire con DSLs  
 Un'applicazione tipica di un modello DSL è necessario generare codice programma o altri elementi.  Quando si definisce il modello DSL, è possibile definire *modelli di testo* tale leggere un modello DSL e generare file di testo.  
  
 Ad esempio, è possibile scrivere modelli che accettano un piano per gli aeroporti e generano la parte del software per la gestione dei bagagli oltre ad altri documenti dell'utente che descrivono il piano.  
  
 Dopo aver definito un modello DSL, è possibile distribuirlo ad altri utenti che possono installarla nei propri computer.  Gli utenti del modello DSL possono creare e modificare i modelli in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 È inoltre possibile definire i comandi di menu e altri strumenti che consente agli utenti di modificare il modello DSL, vincoli di convalida garantire che il modello DSL è utilizzato correttamente e modelli di elemento che consente agli utenti di creare nuove istanze.  È possibile eseguire il wrapping di uno o più DSLs con gli strumenti e altre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensioni come integrated package.  
  
 In genere, un linguaggio specifico di dominio viene creato quando un team di sviluppo deve scrivere codice analogo per diversi prodotti.  Ad esempio, una società che è specializza in sistemi di gestione dei bagagli possibile definire una barra di avanzamento DSL bagagli che possono generare parte del codice per ogni installazione.  I vantaggi del modello DSL sono che può essere considerato dai clienti, che il codice generato da sia affidabile e che il sistema possibile rapidamente essere aggiornato se la modifica dei requisiti dei clienti.  
  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] consente di creare un linguaggio specifico di dominio che dispone della finestra di progettazione grafica e per contenere la notazione del diagramma e quindi viene utilizzato il linguaggio per generare il codice sorgente appropriato per ogni progetto.  
  
## sviluppo specifico di dominio  
 Lo sviluppo specifico di dominio è il processo di identificazione delle parti delle applicazioni che possono essere create utilizzando un linguaggio specifico di dominio e quindi di costruzione del linguaggio e di distribuirlo agli sviluppatori di applicazioni.  Gli sviluppatori utilizzano il linguaggio specifico di dominio per costruire i modelli specifici delle loro applicazioni, utilizzano modelli per generare il codice sorgente e quindi utilizzano codice sorgente per sviluppare applicazioni.  
  
## Aspetti dello sviluppo specifico di dominio grafico  
 Un linguaggio specifico di dominio grafico necessario includere le funzionalità seguenti:  
  
-   Notation  
  
-   modello di dominio  
  
-   Generazione di elementi  
  
-   Serializzazione  
  
-   Integrazione con Visual Studio  
  
### Notation  
 Un linguaggio specifico di dominio deve disporre di un insieme di elementi ragionevolmente piccolo che possono essere facilmente definiti e estesi rappresentare i costrutti specifici di dominio.  Una notazione è costituito dalle forme, che rappresentano elementi e i connettori, che rappresentano le relazioni tra gli elementi, sulla superficie del diagramma grafica.  in [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], le forme possono essere estese e ottimali per rappresentare gli elementi del linguaggio specifico di dominio.  
  
### modello di dominio  
 Un linguaggio specifico di dominio necessario combinare il set di elementi e relazioni tra essi in una grammatica coerente.  È necessario definire anche se le combinazioni di elementi e relazioni sono valide.  Ad esempio, i linguaggi di programmazione in genere evitare l'ereditarietà circolare, in cui la classe è derivata dalla classe e la seconda classe è derivata dalla prima classe.  I vincoli possono essere utilizzati per definire la logica di business, ad esempio, l'utente non può essere un dipendente di se stesso.  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilizza i vincoli per esprimere i tipi di restrizioni che la maggior parte dei linguaggi specifici di dominio richiedono.  
  
### Generazione di elementi  
 Uno degli scopi principali di un linguaggio specifico di dominio consiste nel creare un elemento, ad esempio, il codice sorgente, un file XML, o altri dati utilizzabili.  In genere, una modifica nel modello indica una modifica nell'elemento.  È possibile utilizzare [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] per generare gli elementi e rigenerarli quando si modifica il modello.  
  
### Serializzazione  
 Un linguaggio specifico di dominio deve essere conservato in un formato che può essere modificato, salvato, chiuso e sono ricaricatoe.  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilizza un formato XML che consente di definire e personalizzare come linguaggio specifico di dominio viene serializzato o salvato in modo permanente.  
  
### Integrazione con Visual Studio  
 Poiché [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] ospitata in  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], estende molti  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] finestre e controlli.  Consente di personalizzare il comportamento dei comandi di menu, gli elementi della casella degli strumenti e altri elementi dell'interfaccia utente.  
  
 È inoltre possibile creare un adattatore di template bus del linguaggio specifico di dominio.  Questo adattatore consente di fare riferimento a un modello ed elementi all'interno di un modello e consente di scrivere il codice che può accedere e aggiornare un'istanza del modello DSL.  Utilizzando il meccanismo di modello efficace di bus\), è possibile scrivere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensioni che utilizzano più modelli.  È anche possibile scrivere applicazioni autonome che utilizzano i modelli.  Per ulteriori informazioni, vedere [L'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## vantaggi di sviluppo specifico di dominio  
 Un linguaggio specifico di dominio può fornire i vantaggi seguenti:  
  
-   Contiene i costrutti perfettamente si adattano allo spazio del problema.  
  
     A differenza dei linguaggi di utilizzo generale, un linguaggio specifico di dominio è costituito da elementi e relazioni che rappresentano direttamente la logica dello spazio del problema.  Ad esempio, un'applicazione di polizza d'assicurazione deve includere elementi per i criteri e requisiti.  Un linguaggio specifico di dominio semplifica progettare l'applicazione e individuare e correggere gli errori di logica.  
  
-   Consente agli sviluppatori non e le persone che non conosce il dominio comprendere la progettazione globale.  
  
     Utilizzando un linguaggio specifico di dominio grafico, è possibile creare una rappresentazione visiva del dominio in modo che possano facilmente comprendere gli sviluppatori non la progettazione dell'applicazione.  
  
-   Semplifica creare un prototipo dell'applicazione finale.  
  
     Gli sviluppatori possono utilizzare il codice del modello generi per creare un'applicazione di prova che possono visualizzare i client.  
  
## il processo di sviluppo specifico di dominio  
 La maggior parte dei team di sviluppo software che utilizzano i linguaggi specifici di dominio seguendo questi passaggi per creare e utilizzare i rispettivi modelli:  
  
-   Il team è possibile distinguere le parti variabili del dominio dalle parti che non cambiano mai.  
  
-   Gli sviluppatori scrivere il codice per le parti fisse e dei punti di estensione per le parti variabili.  
  
-   Lo sviluppatore software del responsabile o l'architetto crea un linguaggio specifico di dominio che include modelli di progettazione delle parti fisse del dominio e i punti di estensione per le parti variabili.  
  
-   Lo sviluppatore software del responsabile o l'architetto implementa il linguaggio specifico di dominio agli sviluppatori di varie applicazioni che il team produce.  
  
-   Ogni sviluppatore crea un modello applicato all'applicazione specifica.