---
title: "Utilizzo di IntelliTrace | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.historicaldebug.overview"
helpviewer_keywords: 
  - "debugger, (Vedere anche IntelliTrace [ALM di Visual Studio])"
  - "debugger, registrazione della cronologia delle esecuzioni"
  - "debug, (Vedere anche IntelliTrace [ALM di Visual Studio])"
  - "debug, registrazione della cronologia delle esecuzioni"
  - "IntelliTrace"
  - "IntelliTrace [ALM di Visual Studio]"
  - "IntelliTrace, raccolta di dati da Test Manager"
  - "IntelliTrace, debug successivo a un arresto anomalo"
  - "IntelliTrace, debug di applicazioni"
  - "Gestione test, debug con IntelliTrace"
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 135
caps.handback.revision: 133
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Utilizzo di IntelliTrace
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile ridurre il tempo richiesto per eseguire il debug dell'applicazione quando si usa IntelliTrace per registrare e tenere traccia della cronologia di esecuzione del codice.  È possibile trovare facilmente i bug perché IntelliTrace consente di:  
  
-   Registrare eventi specifici  
  
     Esaminare il codice correlato, i dati visualizzati nella finestra **Variabili locali** durante gli eventi del debugger e le informazioni di chiamata di funzione  
  
-   Eseguire il debug di errori difficili da riprodurre o verificatisi in fase di distribuzione  
  
 È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition \(ma non le edizioni Professional o Community\).  
  
## Selezionare l'operazione da eseguire.  
  
|||  
|-|-|  
|**Eseguire il debug dell’applicazione con IntelliTrace:**<br /><br /> -   Mostrare gli eventi passati.<br />-   Mostrare le informazioni sulle chiamate con gli eventi passati.<br />-   Salvare la sessione di IntelliTrace.<br />-   Controllare i dati raccolti da IntelliTrace.|-   [Procedura dettagliata: Utilizzo di IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [Funzionalità di IntelliTrace](../debugger/intellitrace-features.md)<br />-   [Raccogliere informazioni di debug con IntelliTrace](http://msdn.microsoft.com/it-it/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [Debug cronologico](../debugger/historical-debugging.md)|  
|**Raccogliere i dati IntelliTrace durante una sessione di test in Test Manager**|-   [Raccogliere un maggior numero di dati di diagnostica](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests)|  
|**Raccogliere dati IntelliTrace dalle applicazioni distribuite**|-   [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Avviare il debug da un file di log IntelliTrace \(file .iTrace\).**|-   [Eseguire il debug dell'app usando dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)|  
  
##  <a name="IntelliTraceSupport"></a> Di quali app è possibile eseguire il debug con IntelliTrace?  
  
|||  
|-|-|  
|**Supportato**|-   Applicazioni Visual Basic e Visual C\# che utilizzano .NET Framework 2.0 o versioni successive.<br />     È possibile eseguire il debug della maggior parte delle applicazioni, comprese le app ASP.NET, Microsoft Azure, Windows Form, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 e a 64 bit.<br />     Per eseguire il debug di applicazioni di SharePoint con IntelliTrace, vedere [Procedura dettagliata: debug di un'applicazione di SharePoint tramite IntelliTrace](../Topic/Walkthrough:%20Debugging%20a%20SharePoint%20Application%20by%20Using%20IntelliTrace.md).<br />     Per eseguire il debug delle app Microsoft Azure con IntelliTrace, vedere [Debug di un servizio cloud pubblicato con IntelliTrace e Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).|  
|**Supporto limitato**|-   App F\# su base sperimentale<br />-   App Windows Store supportate solo per eventi|  
|**Non supportato**|-   C\+\+, altri linguaggi e script<br />-   Windows Services, Silverlight, Xbox o applicazione [!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)]|  
  
> [!NOTE]
>  Se si desidera eseguire il debug di un processo già in esecuzione, non è possibile usare IntelliTrace.  È necessario avviare IntelliTrace all'avvio del processo.  
  
##  <a name="IntelliTraceVSTraditional"></a> Perché eseguire il debug con IntelliTrace?  
 Il debug tradizionale o *attivo* mostra solo lo stato corrente dell'applicazione con dati limitati sugli eventi passati.  È necessario dedurre tali eventi dallo stato corrente dell'applicazione oppure ricrearli rieseguendo l'applicazione.  
  
 IntelliTrace consente di espandere questa esperienza di debug tradizionale registrando dati ed eventi specifici in un preciso momento.  Ciò consente di verificare cosa sia accaduto nell'applicazione senza riavviarla, specialmente se si supera il punto in cui si è verificato il bug.  IntelliTrace è attivato per impostazione predefinita durante il debug tradizionale e raccoglie i dati in modo automatico e invisibile.  Ciò consente di passare facilmente dal debug tradizionale al debug IntelliTrace e viceversa per visualizzare le informazioni registrate.  Vedere [Funzionalità di IntelliTrace](../debugger/intellitrace-features.md) e [Quali dati raccoglie IntelliTrace?](#WhatData)  
  
 IntelliTrace consente anche di eseguire il debug di errori difficili da riprodurre o che si verificano in fase di distribuzione.  È possibile raccogliere dati IntelliTrace e salvarli in un file di log IntelliTrace \(file .iTrace\),  contenente dettagli su eccezioni, eventi di prestazioni, richieste Web, dati di test, thread, moduli e altre informazioni di sistema.  È possibile aprire questo file in Visual Studio Enterprise, selezionare un elemento e avviare il debug con IntelliTrace.  Ciò consente di passare a qualsiasi evento nel file e visualizzare dettagli specifici sull'applicazione in un dato momento.  
  
 È possibile salvare i dati IntelliTrace dalle seguenti origini:  
  
-   Una sessione di IntelliTrace in Visual Studio 2105 Enterprise o versioni precedenti di Visual Studio Ultimate.  
  
-   Una sessione di test in Microsoft Test Manager  
  
-   App Web ASP.NET ospitate in IIS o applicazioni SharePoint 2010 e SharePoint 2013 in esecuzione nella distribuzione quando si usa Microsoft Monitoring Agent, in modalità autonoma o con System Center 2012.  Vedere [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) e [Monitoraggio con Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).  
  
 Di seguito sono riportati alcuni esempi sul modo in cui IntelliTrace semplifica le operazioni di debug:  
  
-   L'applicazione ha danneggiato un file di dati, ma non si sa dove si è verificato l'evento.  
  
     Senza IntelliTrace, sarebbe necessario esaminare il codice per trovare tutti gli accessi possibili al file, inserire punti di interruzione in corrispondenza di tali accessi e quindi rieseguire l'applicazione per individuare dove si è verificato il problema.  Con IntelliTrace è possibile vedere tutti gli eventi di accesso ai file raccolti e dettagli specifici sull'applicazione nel momento in cui si è verificato ciascun evento.  
  
-   Si verifica un'eccezione.  
  
     Senza IntelliTrace si ottiene un messaggio su un'eccezione ma non si dispone di molte informazioni sugli eventi che ne hanno causato la comparsa.  È possibile esaminare lo stack di chiamate per individuare la catena che ha generato l'eccezione, ma non è possibile visualizzare la sequenza di eventi che si sono verificati durante tali chiamate.  Con IntelliTrace è possibile esaminare gli eventi che si sono verificati prima dell'eccezione.  
  
-   L'applicazione si arresta in modo anomalo in un computer utilizzato per i test, ma viene eseguita correttamente in un computer di sviluppo.  
  
     È possibile raccogliere dati IntelliTrace da Microsoft Test Manager, salvare i dati in un file .iTrace e allegarlo a un elemento di lavoro Team Foundation Server per analizzarlo in un secondo momento.  Vedere [Raccogliere un maggior numero di dati di diagnostica](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests) e [Eseguire il debug dell'app usando dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md).  
  
-   Un bug o un arresto anomalo si verifica in un'applicazione distribuita.  
  
     Per le app basate su Microsoft Azure, è possibile configurare la raccolta di dati IntelliTrace prima di pubblicare l'applicazione.  Mentre l'applicazione è in esecuzione, IntelliTrace salva i dati in un file .iTrace.  Vedere [Debug di un servizio cloud pubblicato con IntelliTrace e Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).  
  
     Per le app Web ASP.NET ospitate in IIS 7.0, 7.5 e 8.0 o le applicazioni SharePoint 2010 o SharePoint 2013, utilizzare Microsoft Monitoring Agent, in modalità autonoma o con System Center 2012, per salvare i dati IntelliTrace in un file .iTrace.  
  
     Si tratta di un'opzione utile per diagnosticare problemi con le app in fase di distribuzione.  Vedere [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
##  <a name="WhatData"></a> Quali dati raccoglie IntelliTrace?  
 **Raccolta delle informazioni sugli eventi**  
  
 Per impostazione predefinita, IntelliTrace registra solo gli eventi di IntelliTrace: eventi del debugger, eccezioni, eventi .NET Framework e altri eventi di sistema utili per il debug.  È possibile scegliere i tipi di eventi IntelliTrace che si desidera raccogliere, tranne gli eventi del debugger e le eccezioni, che vengono sempre raccolti.  Vedere [Raccogliere informazioni di debug con IntelliTrace](http://msdn.microsoft.com/it-it/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
-   **Eventi del debugger**  
  
     IntelliTrace registra sempre gli eventi che si verificano nel debugger di Visual Studio.  Ad esempio, l'avvio dell'applicazione è un evento del debugger.  Altri eventi del debugger sono eventi di arresto, ossia quelli che interrompono l'esecuzione dell'applicazione,  ad esempio il rilevamento di un punto di interruzione, il rilevamento di un punto di analisi o l'esecuzione di un comando di **esecuzione**.  
  
     Ai fini delle prestazioni, IntelliTrace non registra ogni possibile valore per un evento del debugger.  Vengono invece registrati questi valori:  
  
    -   Valori nella finestra **Variabili locali**.  Per visualizzarli, mantenere aperta la finestra **Variabili locali**.  
  
    -   Valori nella finestra **Auto** solo se questa finestra è aperta.  
  
    -   Valori nei suggerimenti dati mostrati quando si sposta il puntatore del mouse su una variabile nella finestra di origine per visualizzarne il valore.  Tramite IntelliTrace non vengono raccolti i valori nei suggerimenti dati bloccati.  
  
-   **Eccezioni**  
  
     Tramite IntelliTrace vengono registrati il tipo di eccezione e il messaggio per questi tipi di eccezione:  
  
    -   Eccezioni gestite in cui l'eccezione viene generata e rilevata  
  
    -   Eccezioni non gestite  
  
-   **Eventi .NET Framework**  
  
     Per impostazione predefinita, tramite IntelliTrace vengono registrati gli eventi .NET Framework più comuni.  Ad esempio:  
  
    -   Per un evento di accesso ai file, tramite IntelliTrace viene raccolto il nome del file.  
  
    -   Per un evento di verifica della casella di controllo, raccoglie lo stato e il testo della casella di controllo.  
  
-   **Eventi delle applicazioni SharePoint 2010 e SharePoint 2013**  
  
     È possibile registrare eventi di profili utente e un subset di eventi del sistema di registrazione unificato per le applicazioni SharePoint 2010 e 2013 in esecuzione all'esterno di Visual Studio.  È possibile salvare questi eventi in un file .iTrace.  È necessario Visual Studio Enterprise 2015, una versione precedente di Visual Studio Ultimate oppure [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) in esecuzione in modalità **Traccia**.  
  
     Quando si apre il file .iTrace, immettere un ID di correlazione SharePoint per trovare la richiesta Web corrispondente, visualizzare gli eventi registrati e avviare il debug da un evento specifico.  Se il file contiene eccezioni non gestite, è possibile scegliere un ID di correlazione per avviare il debug di un'eccezione.  
  
     Vedere:  
  
    -   [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
    -   [Eseguire il debug dell'app usando dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)  
  
    -   [Procedura dettagliata: debug di un'applicazione di SharePoint tramite IntelliTrace](../Topic/Walkthrough:%20Debugging%20a%20SharePoint%20Application%20by%20Using%20IntelliTrace.md)  
  
 **Raccolta delle informazioni sulle chiamate di funzione**  
  
 È possibile configurare IntelliTrace per la raccolta delle informazioni sulle chiamate per le funzioni.  Tali informazioni consentono di visualizzare la cronologia dello stack di chiamate e scorrere in avanti e indietro le chiamate nel codice.  Per ogni chiamata di funzione, IntelliTrace registra i seguenti dati:  
  
-   Nome della funzione  
  
-   Valori dei tipi di dati primitivi passati come parametri nei punti di ingresso di una funzione e restituiti nei punti di uscita  
  
-   Valori delle proprietà automatiche quando vengono letti o modificati  
  
-   Puntatori agli oggetti figlio di primo livello, ma non ai relativi valori, se non quelli che indicano se lo stato è null oppure no  
  
> [!NOTE]
>  IntelliTrace raccoglie solo i primi 256 oggetti in matrici e i primi 256 caratteri per le stringhe.  
  
 Vedere [Raccogliere informazioni di debug con IntelliTrace](http://msdn.microsoft.com/it-it/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Raccolta delle informazioni sui moduli**  
  
 Per controllare la quantità di informazioni sulle chiamate raccolte da IntelliTrace, specificare solo i moduli di interesse.  In questo modo è possibile migliorare le prestazioni dell'applicazione durante la raccolta.  Vedere [Raccogliere informazioni di debug con IntelliTrace](http://msdn.microsoft.com/it-it/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
##  <a name="AffectPerformance"></a> IntelliTrace rallenterà l'applicazione?  
 Per impostazione predefinita, vengono raccolti dati solo per eventi di IntelliTrace selezionati.  Ciò può rallentare o meno l'applicazione, a seconda della struttura e dell'organizzazione del codice.  Ad esempio, se IntelliTrace registra spesso un evento, questo potrebbe rallentare l'applicazione.  Potrebbe essere opportuno anche considerare il refactoring dell'applicazione.  
  
 La raccolta di informazioni sulle chiamate potrebbe rallentare significativamente l'applicazione.  Potrebbe inoltre aumentare la dimensione di ogni file di log IntelliTrace \(file .iTrace\) salvato nel disco.  Per ridurre al minimo questi effetti, raccogliere le informazioni sulle chiamate solo per i moduli desiderati.  Per modificare la dimensione massima dei file .iTrace, passare a **Strumenti**, **Opzioni**, **IntelliTrace**, **Avanzate**.  Vedere [Raccogliere informazioni di debug con IntelliTrace](http://msdn.microsoft.com/it-it/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## Contenuto della sezione  
 [Funzionalità di IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Raccogliere informazioni di debug con IntelliTrace](http://msdn.microsoft.com/it-it/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Inclusione di dati di traccia di diagnostica nei bug difficili da riprodurre](/devops-test-docs/test_notintoc/including-diagnostic-trace-data-with-bugs-that-are-difficult-to-reproduce)  
  
 [Diagnosticare i problemi dopo la distribuzione](../debugger/diagnose-problems-after-deployment.md)  
  
 [Eseguire il debug dell'app usando dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)  
  
### Blog  
 [Visual Studio ALM e Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### Forum  
 [Diagnostica di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)