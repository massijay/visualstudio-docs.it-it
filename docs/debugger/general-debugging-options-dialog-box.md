---
title: "Generale, Debug, finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.options.General"
  - "VS.ToolsOptionsPages.Debugger.General"
  - "VS.ToolsOptionsPages.Debugger.ENC"
  - "vs.debug.options.ENC"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "Finestra di dialogo Opzioni, debug"
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 46
caps.handback.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Generale, Debug, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La pagina **Strumenti \/ Opzioni \/ Debug \/ Generale** consente di impostare le opzioni seguenti:  
  
 **Chiedi prima di eliminare tutti i punti di interruzione**  
 Richiede conferma prima dell'esecuzione del comando **Elimina tutti i punti di interruzione**.  
  
 **Quando si interrompe un processo, interrompi tutti i processi**  
 Interrompe simultaneamente tutti i processi a cui è connesso il debugger quando si verifica un'interruzione.  
  
 **Interrompi quando le eccezioni superano il dominio applicazione o i limiti gestiti\/nativi**  
 Durante il debug in modalità gestita o mista, Common Language Runtime è in grado di rilevare eccezioni che superano i limiti del dominio applicazione o i limiti gestiti\/nativi quando sono vere le seguenti condizioni:  
  
 1\) Quando il codice nativo chiama il codice gestito utilizzando l'interoperabilità COM e il codice gestito genera un'eccezione. Vedere [Introduction to COM Interop](/dotnet/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
 2\) Quando il codice gestito in esecuzione nel dominio applicazione 1 chiama il codice gestito presente nel dominio applicazione 2 e il codice nel dominio applicazione 2 genera un'eccezione. Vedere [Programmazione con i domini applicazione](http://msdn.microsoft.com/it-it/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3\) Quando il codice chiama una funzione tramite reflection e la funzione genera un'eccezione. Vedere [Reflection](../Topic/Reflection%20in%20the%20.NET%20Framework.md).  
  
 Nei casi 2\) e 3\) l'eccezione viene talvolta intercettata dal codice gestito in `mscorlib` anziché da Common Language Runtime. Questa opzione non influisce sull'interruzione di eccezioni intercettate da `mscorlib`.  
  
 **Abilita debug a livello di indirizzo**  
 Abilita le funzionalità avanzate per il debug a livello di indirizzo \(finestra **Disassembly**, finestra **Registri** e punti di interruzione\).  
  
 **Mostra disassembly se l'origine non è disponibile**  
 Visualizza automaticamente la finestra **Disassembly** quando si tenta di eseguire il debug del codice per il quale non è disponibile l'origine.  
  
 **Abilita i filtri dei punti di interruzione**  
 Consente di applicare filtri ai punti di interruzione in modo che abbiano effetto solo su determinati processi, thread o computer.  
  
 **Abilita Informazioni sulle eccezioni**  
 Solo per il codice gestito. Le eccezioni gestite aprono la finestra di dialogo Informazioni sulle eccezioni.  Vedere [Exception Assistant](../Topic/Exception%20Assistant.md).  
  
 **Rimuovi stack di chiamate su eccezioni non gestite**  
 La finestra **Stack di chiamate** esegue il rollback dello stack di chiamate al punto precedente l'eccezione non gestita.  
  
 **Abilita Just My Code**  
 Il debugger visualizza ed esegue solo il codice utente \("My Code"\), ignorando il codice di sistema e altro codice ottimizzato o privo di simboli di debug.  
  
 **Mostra tutti i membri per gli oggetti non utente nelle finestre delle variabile \(solo Visual Basic\)**  
 Attiva la visualizzazione dei membri non pubblici per gli oggetti presenti nel codice non utente \(non "My Code"\).  
  
 **Avvisa se all'avvio non è presente codice utente**  
 Quando il debug viene avviato con Just My Code attivato, questa opzione determina la visualizzazione di un avviso se non è presente codice utente \("My Code"\).  
  
 **Abilita esecuzione di istruzioni origine .NET Framework**  
 Consente al debugger di eseguire l'origine di .NET Framework. L'abilitazione di questa opzione disabilita automaticamente Just My Code. I simboli .NET Framework saranno scaricati in un percorso della cache. È possibile modificare il percorso della cache nella finestra di dialogo **Opzioni**, categoria **Debug**, pagina **Simboli**.  
  
 **Esegui istruzione\/routine di proprietà e operatori \(solo gestito\)**  
 Impedisce al debugger di eseguire istruzioni di proprietà e operatori nel codice gestito.  
  
 **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**  
 Attiva la valutazione automatica di proprietà e altre chiamate di funzioni implicite nelle finestre delle variabili e nella finestra di dialogo **Controllo immediato**.  
  
 **Chiama la funzione di conversione delle stringhe su oggetti nelle finestre delle variabili \(solo C\# e JavaScript\)**  
 Esegue una chiamata di conversione delle stringhe implicita durante la valutazione di oggetti nelle finestre delle variabili. Pertanto, il risultato viene visualizzato come stringa anziché come nome del tipo. Questa opzione è applicabile solo al debug in codice C\#. È possibile eseguire l'override di questa impostazione mediante l'attributo DebuggerDisplay \(vedere [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)\).  
  
 **Abilita il supporto del server di origine**  
 Indica al debugger di Visual Studio di ottenere i file di origine da server di origine che implementano il protocollo di SrcSrv \(`srcsrv.dll`\). Team Foundation Server e gli strumenti di debug per Windows sono due server di origine che implementano il protocollo. Per altre informazioni sull'installazione di SrcSrv, vedere la documentazione relativa agli Strumenti di debug per Windows. Vedere anche [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Poiché la lettura dei file PDB può determinare l'esecuzione del codice arbitrario nei file, assicurarsi di ritenere attendibile il server.  
  
 **Visualizza i messaggi diagnostici del server di origine nella finestra di output**  
 Quando è attivato il supporto per il server di origine, questa opzione attiva la visualizzazione dei messaggi di diagnostica.  
  
 **Abilitare il server di origine per gli assembly parzialmente attendibili \(solo gestito\)**  
 Quando il supporto del server di origine è abilitato, questa impostazione esegue l'override del comportamento predefinito che non recupera le origini per gli assembly parzialmente attendibili.  
  
 **Evidenzia la riga completa per i punti di interruzione e l'istruzione corrente**  
 Quando il debugger evidenzia un punto di interruzione o l'istruzione corrente, estende l'evidenziazione all'intera riga.  
  
 **Richiedi corrispondenza esatta dei file di origine con la versione originale**  
 Indica al debugger di verificare che un file di origine corrisponda alla versione del codice sorgente utilizzato per compilare l'eseguibile sottoposto a debug. Se la versione non corrisponde, verrà chiesto di cercare un'origine corrispondente. Se la ricerca ha esito negativo, il codice sorgente non verrà visualizzato durante il debug.  
  
 **Reindirizza tutto il testo della finestra di output nella finestra di controllo immediato**  
 Invia alla finestra **Controllo immediato** tutti i messaggi del debugger che normalmente verrebbero visualizzati nella finestra **Output**.  
  
 **Mostra la struttura non elaborata degli oggetti nelle finestre delle variabili**  
 Disattiva tutte le personalizzazioni di visualizzazione della struttura degli oggetti. Per altre informazioni sulle personalizzazioni della visualizzazione, vedere [Visualizzazione di tipi di dati personalizzati](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
 **Disattiva l'ottimizzazione JIT al caricamento del modulo \(solo gestito\)**  
 Disabilita l'ottimizzazione JIT del codice gestito quando un modulo viene caricato e JIT viene compilato al momento della connessione al debugger. La disabilitazione dell'ottimizzazione JIT può semplificare il debug di determinati errori, anche se può avere effetti negativi sulle prestazioni. Se si usa Just My Code e si disattiva l'ottimizzazione JIT, è possibile che il codice non utente venga visualizzato come codice utente \("My Code"\).  
  
 **Avvisa se non vi sono simboli all'avvio \(solo nativo\)**  
 Visualizza una finestra di dialogo di avviso ogni volta che si prova a eseguire il debug di un programma per il quale il debugger non ha informazioni sui simboli.  
  
 **Avvisa se il debug degli script è disabilitato all'avvio**  
 Visualizza una finestra di dialogo di avviso ogni volta che il debugger viene avviato con il debug degli script disabilitato.  
  
 **Carica esportazioni DLL**  
 Carica le tabelle di esportazione DLL. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili se usano messaggi Windows, routine Windows \(WindowProc\), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. La lettura di informazioni di esportazione DLL comporta un sovraccarico. Pertanto questa funzionalità è disattivata per impostazione predefinita.  
  
 Per visualizzare i simboli disponibili nella tabella di esportazione di una DLL, usare `dumpbin /exports`. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Leggendo l'output di `dumpbin /exports`, è possibile visualizzare il nome esatto della funzione, compresi i caratteri non alfanumerici. Ciò risulta utile per impostare un punto di interruzione su una funzione. I nomi di funzione delle tabelle di esportazione DLL possono apparire troncati in altri punti del debugger. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente \(al più alto livello di annidamento\) all'inizio dell'elenco. Per altre informazioni, vedere [dumpbin \/exports](/visual-cpp/build/reference/dash-exports).  
  
 **Mostra diagramma degli stack in parallelo dal basso verso l'alto**  
 Controlla la direzione in cui vengono visualizzati gli stack nella finestra **Stack in parallelo**.  
  
 **Ignora eccezioni di accesso a memoria GPU se i dati scritti non hanno modificato il valore**  
 Ignora le race condition rilevate durante il debug se i dati non sono stati modificati. Per altre informazioni, vedere [Debug del codice GPU](../debugger/debugging-gpu-code.md).  
  
 **Utilizza modalità di compatibilità gestita**  
 Sostituisce il motore di debug predefinito con una versione legacy per abilitare gli scenari seguenti:  
  
-   Si utilizza un linguaggio .NET Framework diverso da C\#, VB o F\# che fornisce il proprio analizzatore di espressioni \(questo include C\+\+\/CLI\).  
  
-   Si vuole abilitare Modifica e continuazione per i progetti C\+\+ durante il debug in modalità mista.  
  
 Si noti che scegliendo la modalità di compatibilità gestita vengono disabilitate alcune funzionalità implementate solo nel motore di debug predefinito.  
  
 **Usa modalità di compatibilità nativa**  
 Quando questa opzione è selezionata, il debugger usa il debugger nativo di Visual Studio 2010 anziché il nuovo debugger nativo.  
  
 Usare questa opzione quando si esegue il debug di codice C\+\+ .NET perché il nuovo motore di debug non supporta la valutazione delle espressioni C\+\+ .NET. Tuttavia, l'abilitazione della modalità di compatibilità nativa disabilita molte funzionalità che dipendono dall'implementazione corrente del debugger per il funzionamento. Ad esempio, il motore legacy non contiene molti dei visualizzatori per i tipi predefiniti, ad esempio `std::string` nei progetti di Visual Studio 2015.   Per un'esperienza di debug ottimale, in questi casi usare i progetti di Visual Studio 2013.  
  
 **Usa gli analizzatori di espressioni C\# e VB legacy**  
 Il debugger userà gli analizzatori di espressioni di Visual Studio 2013 C\#\/VB anziché quelli basati su Visual Studio 2015 Roslyn.  
  
 **Avvisa quando si usano visualizzatori di debugger personalizzati in caso di processi potenzialmente non sicuri**  
 Visual Studio genera avvisi quando si usa un visualizzatore di debugger personalizzato che esegue codice nel processo oggetto del debug perché potrebbe essere in esecuzione codice unsafe.  
  
 **Abilita l'allocatore di heap per il debug di Windows \(solo nativo\)**  
 Consente all'heap per il debug di Windows di migliorare la diagnostica dell'heap. L'abilitazione di questa opzione influirà sulle prestazioni di debug.  
  
 **Abilita strumenti di debug dell'interfaccia utente per XAML**  
 Le finestre Albero elementi visivi attivi e Esplora proprietà attive vengono visualizzate quando si avvia il debug \(F5\) di un tipo di progetto supportato. Per altre informazioni, vedere [Analizzare le proprietà XAML durante il debug](../debugger/inspect-xaml-properties-while-debugging.md).  
  
 **Anteprima degli elementi selezionati in Albero elementi visivi attivi**  
 Anche l'elemento XAML di cui è selezionato il contesto viene selezionato nella finestra Albero elementi visivi attivi.  
  
 **Abilita strumenti di diagnostica durante il debug**  
 Durante il debug viene visualizzata la finestra Strumenti di diagnostica. Per altre informazioni, vedere [Diagnostica integrata nel debugger](../Topic/Debugger-integrated%20profiling.md).  
  
 **Mostra il PerfTip relativo al tempo trascorso durante il debug**  
 La finestra di codice mostra il tempo trascorso di una specifica chiamata al metodo quando si esegue il debug.  
  
 **Abilita Modifica e continuazione**  
 È possibile usare la funzionalità Modifica e continuazione durante il debug.  
  
 **Abilita Modifica e continuazione nativo**  
 È possibile usare la funzionalità Modifica e continuazione durante il debug del codice C\+\+ nativo. Per altre informazioni, vedere [Modifica e continuazione \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md).  
  
 **Applica le modifiche durante la continuazione \(solo nativo\)**  
 Visual Studio compila e applica automaticamente le modifiche di codice in sospeso apportate quando il processo viene ripreso da uno stato di interruzione. Se non è selezionato, è possibile scegliere di applicare le modifiche usando l'elemento "Applica modifiche del codice" nel menu Debug.  
  
 **Avvisa in caso di codice non aggiornato \(solo nativo\)**  
 Consente di ricevere avvisi relativi al codice non aggiornato.  
  
 **Consenti precompilazione \(solo nativo\)**  
 La precompilazione è consentita.  
  
## Vedere anche  
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)