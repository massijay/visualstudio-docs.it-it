---
title: Visual Studio Shell (integrata) | Documenti di Microsoft
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
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
ms.sourcegitcommit: 4f2ddbc47f9a014acde2850dba5c72ef3a784847
ms.openlocfilehash: 8edd3a6fcca0c2ddd4d580f0874b737cfbbc40c9
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integrata)
La shell di Visual Studio integrated include l'ambiente di sviluppo integrato (IDE), debugger e integrazione del controllo codice sorgente. Non è incluso alcun linguaggio di programmazione. Tuttavia, la shell integrata fornisce un framework che consente di aggiungere i linguaggi di programmazione.  
  
 La shell di Visual Studio integrato è effettivamente una serie di shell di Visual Studio isolato e una procedura di installazione aggiuntiva che includono i componenti specifici di shell integrata.  L'applicazione di shell integrata deve includere sia il pacchetto ridistribuibile shell isolata da [Microsoft Visual Studio Shell (Isolated) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022) nonché il pacchetto ridistribuibile di shell integrata da [Microsoft Visual Studio Shell (Integrated) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Prima di poter accedere i pacchetti ridistribuibili di shell isolata e integrata, verrà richiesto di compilare un questionario sui clienti breve.  Dopo aver compilato il sondaggio, si verrà indirizzati a una pagina con i collegamenti ai download del pacchetto ridistribuibile Visual Studio connettersi.  È possibile trovare i collegamenti ai download durante le successive visite al sito di Visual Studio Connect sotto il **programmi | VISUAL STUDIO 2015 e isolato SHELL integrata** scheda.  
  
 Se si installa l'applicazione di shell integrata nello stesso computer di una versione completa di Visual Studio, i componenti dell'applicazione verranno integrati direttamente in Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Funzionalità nella Shell integrata  
  
|||  
|-|-|  
|Area funzionale|Funzionalità|  
|Supporto per le lingue|-Nessuno|  
|IDE|<ul><li>Impostazioni<br /><br /> <ul><li>Creare le impostazioni</li><li>Importa / Esporta impostazioni</li><li>Impostazioni di ripristino</li></ul></li><li>**Casella degli strumenti** integrazione</li><li>**Elenco attività** integrazione</li><li>Integrazione della Guida in linea</li><li>**Opzioni** la finestra di dialogo</li><li>Gestione di tipi di carattere e colori</li><li>**Output** finestra</li><li>**Comando** finestra</li><li>Gestione delle finestre</li><li>I comandi, menu e tasti di scelta rapida</li><li>Runtime di linguaggio specifico di dominio (DSL)</li></ul>|  
|Sistema di progetto e tipi di progetto|-Soluzioni e le cartelle della soluzione<br />-Gestione della configurazione soluzione<br />-Gestione elemento<br />-Soluzioni multiprogetto e progetto singolo<br />-Progettazione di applicazioni (proprietà del progetto semplificata)<br />-Aggiungi riferimento Web<br />-Aggiungi riferimento al servizio<br />Progetto singolo<br />: Tipi di progetto di sito Web<br />-Progetti di applicazione web|  
|Compilazione|-Istruzioni di compilazione personalizzate nell'IDE<br />-La precompilazione per la protezione della proprietà intellettuale (IP)<br />: La firma del codice<br />     MSBuild|  
|Editor|-Codice esplorazione di strumenti (ricerca unificata, definizione dell'origine, ereditarietà)<br />-Navigazione codice<br />-IntelliSense<br />-Smart tag<br />-Refactoring<br />-Elenco<br />-Filtro IntelliSense<br />-   **Definizione di codice** finestra|  
|Designer|-Windows Presentation Foundation Designer<br />-Windows Form Designer<br />-Finestra di progettazione e web Editor HTML|  
|Dati|-   **Esplora server** (semplificato: solo i dati). Vedere la nota 1.<br />-   **Origini dati** finestra<br />-Set completo di controlli dati<br />-Editor XML<br />-Data binding a origine dati locale (. MDF o. MDB)<br />-L'associazione dati oggetto<br />-Data binding al servizio Web<br />-Data binding al server di database locale<br />-Data binding al server database remoto<br />-Strumenti DDL per i dati remoti<br />-   **Esplora server** estendibilità ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] esempi)|  
|Debugger|-Debug locale. Vedere la nota 2.<br />-Debug gestito<br />-Debug locale<br />-Connetti a processo locale<br />-Connetti a processo remoto<br />-Delegato anonimo<br />-Domini applicazione<br />-Debug ASPX<br />-Gli attributi<br />-Interrompere la funzione eval<br />-I punti di interruzione<br />-I vincoli punto di interruzione<br />-Stack di chiamate<br />-   **Comando** finestra<br />-Debug Cross-thread<br />-I suggerimenti dati<br />-Visualizzatore dati<br />-Supporto del debugger per assistenti al debug gestiti (MDA)<br />-Supporto del debugger per server d'inoltro<br />-Supporto DTEEvents per OTB<br />-Gestore di istruzioni JMC<br />-Test di AppID debugger (DBGCLR)<br />-Profilo debugger<br />-Debugger strumenti e opzioni<br />-Debug iteratore<br />-Valutazione dell'espressione design-time<br />-C# l'analizzatore di espressioni<br />-Disassembly<br />-Modifica e continuazione<br />-Windows dell'analizzatore di espressioni expression (espressioni di controllo, variabili locali, Auto)<br />-Supporto eccezioni<br />-Eccezioni<br />-Esecuzione<br />-Generics<br />-Introduzione origine corretta<br />-Debug/Cluster HPC<br />-Multilingue debug integrato<br />-Debug interoperabilità<br />Debug just-in-time<br />-Debug locale<br />-Debug gestito<br />-Controllo manuale (finestra processi)<br />-Memoria<br />-Supporto miniDump<br />-Moduli<br />-Debug multiprocesso<br />-Debug nativo<br />-Supporto del motore di debug nuovo<br />-Debug di codice ottimizzato<br />-Filtro di windows output<br />-Processo di hosting per il debug gestito<br />-Processi<br />-Controllo immediato<br />-Esegue la registrazione<br />-Registri nello stack<br />-Debug remoto<br />-I valori restituiti<br />: Debug di script<br />-Supporto del servizio origine<br />-Sicurezza<br />Side-by-side<br />-SQL<br />: Server di simboli<br />: Punti di traccia<br />-Thread<br />-Visualizzazioni<br />-Debugger di extensible Stylesheet Language Transformations (XSLT)|  
|Supporto a&64; bit|-debug a 64 bit per codice nativo e gestito, tutte le lingue<br />-supporto x64 nativo|  
|Controllo del codice sorgente (SCC)|-Integrazione di controllo del codice sorgente di base. Vedere la nota 3.<br />-Strumenti e le opzioni di verifica|  
|Estendibilità|-Utilizzare i componenti MEF e package VS|  
  
## <a name="notes"></a>Note  
  
#### <a name="1-data-tools"></a>1. Strumenti dati  
 La shell integrata include strumenti di sviluppo di database, ad esempio semplificato e al supporto di estendibilità dati **Esplora**. Tuttavia, SQL Server Express, SQL Reporting e Crystal Reports non sono inclusi nella shell integrata.  
  
#### <a name="2-debugging-support"></a>2. Supporto per il debug  
 La shell integrata include lo stesso motore di debug che è incluso nella versione Community di Visual Studio. Il motore di debug sono inclusi il debugger comune per codice gestito e funzionalità correlate, come eseguire, collegamento, impostare punti di interruzione, modifica e continuazione e altri. Tuttavia, il motore di debug non supporta il debug di database di SQL Server.  
  
 Sebbene il supporto per il debug nativo è incluso nel pacchetto di base del debugger, non è possibile estendere per il supporto di lingue aggiuntive.  
  
#### <a name="3-source-code-control-integration"></a>3. Integrazione del controllo del codice sorgente  
 La shell integrata fornisce API per l'implementazione del controllo del codice sorgente (SCC) e per fornire il controllo origine comune MSSCCI basato su componenti di integrazione.  
  
 Anche se l'integrazione di controllo del codice sorgente non è una normale funzionalità dell'edizione di Visual Studio Pro, integrazione di controllo del codice sorgente viene fornito nella shell integrata.  
  
#### <a name="4-build-support"></a>4. Supporto per la compilazione  
 La shell integrata fornisce supporto per la compilazione. È possibile trovare informazioni sulle compilazioni di [riferimento MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Funzionalità non incluse nella Shell integrata  
 Di seguito è riportato un elenco delle funzionalità che non sono inclusi nella shell integrata:  
  
-   Progettazione classi  
  
-   [Protezione preEmptive - Dotfuscator](../ide/dotfuscator/index.md)  
  
-   Funzionalità del linguaggio  
  
-   VSHost  
  
-   Nessuna lingua di Visual Studio o i modelli di progetto associato o i modelli di progetto, sono inclusi nella shell integrata. Nessun implementazioni specifiche della lingua di altre funzionalità sono incluse, frammenti di codice di esempio Visual Basic.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione Panoramica di Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md)
