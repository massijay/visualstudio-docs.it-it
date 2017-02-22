---
title: "Visual Studio Shell (integrata) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Funzionalità di Visual Studio in modalità integrata, shell"
  - "Shell [Visual Studio], le funzionalità in modalità integrata"
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio Shell (integrata)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La shell di Visual Studio integrated include l'ambiente di sviluppo integrato \(IDE\), debugger e integrazione del controllo codice sorgente. Non è incluso alcun linguaggio di programmazione. Tuttavia, la shell integrata fornisce un framework che consente di aggiungere i linguaggi di programmazione.  
  
 La shell di Visual Studio integrato è effettivamente una serie di shell di Visual Studio isolato e una procedura di installazione aggiuntiva che includono i componenti specifici di shell integrata.  L'applicazione di shell integrata deve includere sia il pacchetto ridistribuibile shell isolata da [Microsoft Visual Studio Shell \(Isolated\) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022) nonché il pacchetto ridistribuibile di shell integrata da [Microsoft Visual Studio Shell \(Integrated\) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Prima di poter accedere i pacchetti ridistribuibili di shell isolata e integrata, verrà richiesto di compilare un questionario sui clienti breve.  Dopo aver compilato il sondaggio, si verrà indirizzati a una pagina con i collegamenti ai download del pacchetto ridistribuibile Visual Studio connettersi.  È possibile trovare i collegamenti ai download durante le successive visite al sito di Visual Studio Connect sotto il **programmi &#124; VISUAL STUDIO 2015 e isolato SHELL integrata** scheda.  
  
 Se si installa l'applicazione di shell integrata nello stesso computer di una versione completa di Visual Studio, i componenti dell'applicazione verranno integrati direttamente in Visual Studio.  
  
## Funzionalità nella Shell integrata  
  
|||  
|-|-|  
|Area funzionale|Funzionalità|  
|Supporto delle lingue|-   Nessuna|  
|IDE|<ul><li>Impostazioni<br /><br /> <ul><li>Creare le impostazioni</li><li>Importa \/ Esporta impostazioni</li><li>Impostazioni di ripristino</li></ul></li><li>**Della casella degli strumenti** integrazione</li><li>**Elenco attività** integrazione</li><li>Integrazione della Guida in linea</li><li>**Opzioni** la finestra di dialogo</li><li>Gestione di tipi di carattere e colori</li><li>**Output** finestra</li><li>**Comando** finestra</li><li>Gestione delle finestre</li><li>I comandi, menu e tasti di scelta rapida</li><li>Runtime di linguaggio specifico di dominio \(DSL\)</li></ul>|  
|Sistema di progetto e tipi di progetto|-   Soluzioni e le cartelle della soluzione<br />-   Gestione configurazione di soluzione<br />-   Gestione degli elementi<br />-   Soluzioni multiprogetto e progetto singolo<br />-   Progettazione di applicazioni \(proprietà del progetto semplificata\)<br />-   Aggiungi riferimento Web<br />-   Aggiungi riferimento al servizio<br />-   Progetto singolo<br />-   Tipi di progetto di sito Web<br />-   Progetti di applicazione Web|  
|Compilazione|-   Passaggi di compilazione personalizzato nell'IDE<br />-   Pre\-compilazione per la protezione della proprietà intellettuale \(IP\)<br />-   La firma del codice<br />     MSBuild|  
|Editor|-   Esplorazione degli strumenti \(ricerca unificata, definizione dell'origine, ereditarietà\) del codice<br />-   Esplorazione del codice<br />-   IntelliSense<br />-   Smart tag<br />-   Refactoring<br />-   Elenco<br />-   Filtro IntelliSense<br />-   **Definizione codice** finestra|  
|Designer|-   Progettazione di Windows Presentation Foundation<br />-   Progettazione Windows Form<br />-   Finestra di progettazione Web e un Editor HTML|  
|Dati|-   **Esplora server** \(semplificato: solo i dati\). Vedere la nota 1.<br />-   **Origini dati** finestra<br />-   Set completo di controlli dati<br />-   Editor XML<br />-   Associare dati all'origine dati locale \(. MDF o. MDB\)<br />-   Associare dati all'oggetto<br />-   Associazione dei dati al servizio Web<br />-   Associazione dei dati al server di database locale<br />-   Associazione dei dati al server di database remoto<br />-   Strumenti DDL per i dati remoti<br />-   **Esplora server** estendibilità \([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] esempi\)|  
|Debugger|-   Il debug locale. Vedere la nota 2.<br />-   Debug gestito<br />-   Il debug locale<br />-   Connetti a processo locale<br />-   Connetti a processo remoto<br />-   Delegato anonimo<br />-   Domini applicazione<br />-   Il debug ASPX<br />-   Attributi<br />-   Interrompere la funzione eval<br />-   Punti di interruzione<br />-   Vincoli di punto di interruzione<br />-   Stack di chiamate<br />-   **Comando** finestra<br />-   Debug di cross\-thread<br />-   Suggerimenti dati<br />-   Visualizzatore dati<br />-   Supporto del debugger per assistenti al debug gestiti \(MDA\)<br />-   Supporto del debugger per server d'inoltro<br />-   Supporto DTEEvents per OTB<br />-   Gestore di istruzioni JMC<br />-   Test di AppID debugger \(DBGCLR\)<br />-   Profilo del debugger<br />-   Strumenti di debug e opzioni<br />-   Iteratori di debug<br />-   Valutazione delle espressioni in fase di progettazione<br />-   Analizzatore di espressioni c\#<br />-   Disassembly<br />-   Modifica e continuazione<br />-   Finestre dell'analizzatore di espressioni \(espressioni di controllo, variabili locali, Auto\)<br />-   Supporto eccezioni<br />-   Eccezioni<br />-   Esecuzione<br />-   Generics<br />-   Ottenere l'origine corretta<br />-   Cluster HPC\/debug<br />-   Debug di più linguaggi integrato<br />-   Debug di interoperabilità<br />-   Il debug Just\-in\-time<br />-   Il debug locale<br />-   Debug gestito<br />-   Controllo manuale \(finestra processi\)<br />-   Memoria<br />-   Supporto miniDump<br />-   Moduli<br />-   Debug multiprocesso<br />-   Debug nativo<br />-   Nuovo supporto del motore di debug<br />-   Debug di codice ottimizzato<br />-   Finestra di output filtro<br />-   Processo di hosting per il debug gestito<br />-   Processi<br />-   Controllo immediato<br />-   Registri<br />-   Registri nello stack<br />-   Debug remoto<br />-   Valori restituiti<br />-   Debug di script<br />-   Supporto del servizio di origine<br />-   Sicurezza<br />-   Side\-by\-side<br />-   SQL<br />-   Server di simboli<br />-   Punti di traccia<br />-   Thread<br />-   Visualizzazioni<br />-   Debugger di Extensible Stylesheet Language Transformations \(XSLT\)|  
|Supporto a 64 bit|-   64 bit, il debug del codice nativo e gestito, tutte le lingue<br />-   supporto x64 nativo|  
|Controllo del codice sorgente \(SCC\)|-   Integrazione di base SCC. Vedere la nota 3.<br />-   Strumenti e opzioni di verifica|  
|Extensibility|-   Utilizzare i componenti MEF e package VS|  
  
## Note  
  
#### 1. Data Tools  
 La shell integrata include strumenti di sviluppo di database, ad esempio semplificato e al supporto di estendibilità dati **Esplora**. Tuttavia, SQL Server Express, SQL Reporting e Crystal Reports non sono inclusi nella shell integrata.  
  
#### 2. Supporto per il debug  
 La shell integrata include lo stesso motore di debug che è incluso nella versione Community di Visual Studio. Il motore di debug sono inclusi il debugger comune per codice gestito e funzionalità correlate, come eseguire, collegamento, impostare punti di interruzione, modifica e continuazione e altri. Tuttavia, il motore di debug non supporta il debug di database di SQL Server.  
  
 Sebbene il supporto per il debug nativo è incluso nel pacchetto di base del debugger, non è possibile estendere per il supporto di lingue aggiuntive.  
  
#### 3. Integrazione del controllo del codice sorgente  
 La shell integrata fornisce API per l'implementazione del controllo del codice sorgente \(SCC\) e per fornire il controllo origine comune MSSCCI basato su componenti di integrazione.  
  
 Anche se l'integrazione di controllo del codice sorgente non è una normale funzionalità dell'edizione di Visual Studio Pro, integrazione di controllo del codice sorgente viene fornito nella shell integrata.  
  
#### 4. Supporto per la compilazione  
 La shell integrata fornisce supporto per la compilazione. È possibile trovare informazioni sulle compilazioni di [MSBuild Reference](../msbuild/msbuild-reference.md).  
  
## Funzionalità non incluse nella Shell integrata  
 Di seguito è riportato un elenco delle funzionalità che non sono inclusi nella shell integrata:  
  
-   Progettazione classi  
  
-   DotFuscator preventiva  
  
-   Funzionalità del linguaggio  
  
-   VSHost  
  
-   Nessuna lingua di Visual Studio o i modelli di progetto associato o i modelli di progetto, sono inclusi nella shell integrata. Nessun implementazioni specifiche della lingua di altre funzionalità sono incluse, frammenti di codice di esempio Visual Basic.  
  
## Vedere anche  
 [Panoramica sull'estensione di Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md)