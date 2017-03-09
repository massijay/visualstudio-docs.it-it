---
title: "Debug del codice gestito | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug di applicazioni Web ASP.NET, codice gestito"
  - "debug di codice gestito"
  - "codice gestito, debug"
ms.assetid: fa3aff01-c271-4aa7-b5b1-def560471c84
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug del codice gestito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione vengono descritti alcuni problemi di debug comuni e vengono illustrate varie tecniche per le applicazioni gestite, ovvero scritte in linguaggi compatibili con Common Language Runtime, ad esempio Visual Basic, C\# e C\+\+.  Le tecniche descritte sono di livello avanzato.  Per ulteriori informazioni, vedere [Utilizzo del debugger](../debugger/debugger-basics.md).  
  
## In questa sezione  
 [Messaggi diagnostici nella finestra di output](../debugger/diagnostic-messages-in-the-output-window.md)  
 Vengono descritte le classi <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>, con le quali è possibile scrivere messaggi di runtime nella finestra di **Output**.  Queste classi includono metodi di output che supportano l'output di informazioni senza interruzione dell'esecuzione e l'output di informazioni con interruzione dell'esecuzione se non viene rispettata una condizione specificata.  
  
 [Asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md)  
 Vengono descritte le asserzioni nel codice gestito, che verificano le condizioni specificate come argomenti per i metodi `Assert`.  In questo argomento vengono anche forniti il codice di esempio, le informazioni sull'utilizzo dei metodi <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>, le considerazioni sulle versioni di debug e di rilascio del codice, gli effetti secondari, gli argomenti assert, la personalizzazione del comportamento assert e i file di configurazione.  
  
 [Istruzioni Stop in Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
 Viene descritta l'istruzione `Stop`, che fornisce un'alternativa all'impostazione di un punto di interruzione.  Sono inoltre disponibili esempi di codice e un confronto tra le istruzioni `Stop` ed `End` e tra le istruzioni `Stop` e `Assert`.  
  
 [Procedura dettagliata: debug di un Windows Form](../debugger/walkthrough-debugging-a-windows-form.md)  
 Vengono date istruzioni dettagliate per la creazione di un Windows Form e per il debug di tale form.  Un Windows Form, un componente standard di un'applicazione Windows gestita, è una delle applicazioni gestite più comuni.  In questa procedura dettagliata vengono utilizzati Visual C\# e Visual Basic, ma le tecniche per la creazione di un Windows Form con C\+\+ sono simili.  
  
 [Debug del metodo OnStart](../debugger/how-to-debug-the-onstart-method.md)  
 Vengono forniti codici di esempio per consentire il debug del metodo `OnStart` di un servizio Windows gestito.  Per eseguire il debug del metodo `OnStart` di un servizio Windows, è necessario aggiungere alcune righe di codice per simulare il servizio.  
  
 [Debug in modalità mista](../debugger/debugging-mixed-mode-applications.md)  
 Viene descritto il debug di applicazioni in modalità mista,  ovvero qualsiasi applicazione nella quale vengono combinati codice nativo e codice gestito.  
  
 [Errore: impossibile eseguire il debug perché nel sistema è attivato un debugger del kernel](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
 Viene descritto un messaggio di errore visualizzato se si tenta di eseguire il debug del codice gestito in un sistema [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] o Windows NT avviato in modalità debug.  
  
 [Debug e ottimizzazione JIT](../debugger/jit-optimization-and-debugging.md)  
 Vengono descritti gli effetti dell'ottimizzazione JIT sul debug.  
  
 [Debug LINQ e DLINQ](../debugger/debugging-linq.md)  
 Vengono illustrate le tecniche per il debug di query LINQ.  
  
 [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Viene descritto come utilizzare le finestre degli strumenti **Attività in parallelo** e **Stack in parallelo** per eseguire il debug di un'applicazione parallela.  
  
## Sezioni correlate  
 [Utilizzo di IntelliTrace](../debugger/intellitrace.md)  
 Individuare i bug in modo più rapido e semplice registrando la cronologia di esecuzione dell'app con IntelliTrace.  Eseguire all'indietro e in avanti gli eventi registrati e le chiamate per esaminare lo stato dell'app in determinati momenti.  Eseguire il debug del codice senza impostare molti punti di interruzione o riavviare l'app con frequenza.  Richiede Visual Studio Ultimate.  
  
 [Traccia e strumentazione di applicazioni](../Topic/Tracing%20and%20Instrumenting%20Applications.md)  
 Vengono descritte la traccia, che consente di monitorare l'esecuzione dell'applicazione, e la strumentazione, che prevede l'inserimento di istruzioni di traccia in corrispondenza di posizioni strategiche nel codice.  In questo argomento vengono anche forniti collegamenti a un'introduzione all'instrumentazione e alla traccia, opzioni di traccia, listener di traccia, traccia del codice in un'applicazione, aggiunta di istruzioni di traccia al codice dell'applicazione e compilazione in modo condizionale con <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>.  
  
 [\/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)  
 Viene descritta un'opzione del linker che aggiunge <xref:System.Diagnostics.DebuggableAttribute> al codice scritto con C\+\+.  Questo attributo è necessario per l'utilizzo di funzioni di debug, quali la connessione con C\+\+.  
  
 [Esecuzione del debug delle applicazioni di servizio Windows](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md)  
 Vengono fornite considerazioni per il debug di applicazioni di servizio Windows, quali: impostazione, connessione al processo, debug del codice nel metodo `OnStart` del servizio e il codice nel metodo Main, impostazione di punti di interruzione e utilizzo di Services Control Manager per avviare, interrompere, arrestare e continuare il servizio.  
  
 [Esecuzione del debug e creazione del profilo delle applicazioni](../Topic/Debugging,%20Tracing,%20and%20Profiling.md)  
 Viene discusso il debug di applicazioni .NET Framework e i requisiti di configurazione.  
  
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)  
 Vengono presentati le tecniche di debug e i problemi più comuni riscontrabili durante il debug di script e applicazioni Web.  
  
 [Novità relative al debugger di Visual Studio 2015](../debugger/what’s-new-for-the-debugger-in-visual-studio-2015.md)  
 Vengono descritte le nuove funzionalità di debug integrate in questa versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Debug \- Home page](../debugger/debugging-in-visual-studio.md)  
 Vengono forniti collegamenti a sezioni più ampie della documentazione sul debug.  Le informazioni fornite comprendono: novità del debugger, impostazioni e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice gestito, debug di progetti Visual C\+\+, debug di COM e ActiveX, debug di DLL, debug di SQL e riferimenti per l'interfaccia utente.  
  
## Vedere anche  
 [Procedura dettagliata: debug di controlli di Windows Form personalizzati in fase di progettazione](../Topic/Walkthrough:%20Debugging%20Custom%20Windows%20Forms%20Controls%20at%20Design%20Time.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)