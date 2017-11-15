---
title: R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 693b070974c86babcfb57f71d37aa7eb030aac90
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-r-in-visual-studio"></a>Utilizzo di R in Visual Studio

R è un linguaggio estremamente estendibile, nonché un ambiente per l'elaborazione statistica e la grafica. Viene distribuito gratuitamente con la GNU General Public License, può contare su un forte supporto della community ed è noto per la possibilità di creare tracciati di alta qualità, inclusi formule e simboli matematici. Per altre informazioni su R, visitare il sito [r-project.org](https://www.r-project.org/about.html) e vedere [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) (Introduzione a R).

R Tools per Visual Studio (RTVS) è un'estensione [open-source](https://github.com/microsoft/RTVS) gratuita per Visual Studio 2017 e Visual Studio 2015 Update 3 (o versione successiva) rilasciato con licenza MIT. Un secondo componente open-source denominato [RHost](https://github.com/microsoft/R-Host), che esegue il collegamento ai file binari dell'interprete R, viene rilasciato con la GNU Public License V2.

Per sperimentare R in Visual Studio:

- [Installare R Tools](installation.md).
- Seguire le istruzioni riportate nell'argomento [Getting Started](getting-started-with-r.md) (Introduzione), nonché quelle fornite negli argomenti [Samples](getting-started-samples.md) (Esempi) e [Getting Help](getting-started-help.md) (Informazioni di supporto).

Usare quindi i collegamenti per saperne di più sulle funzionalità correlate a R, nonché sulle funzionalità generali di Visual Studio.

| Funzionalità | Descrizione | Documentazione generale su Visual Studio | 
| --- | --- | --- |
| [Sistema del progetto di Visual Studio](projects.md) | È possibile organizzare e gestire i file correlati in una pratica struttura e sfruttare gli utili modelli per elementi quali il codice R, la documentazione R e R Markdown, nonché per le query SQL e le stored procedure. È inoltre possibile sfruttare la funzionalità di [gestione pacchetti](package-manager.md) e l'[integrazione con SQL Server](sql-server.md).  | [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Area di lavoro](workspaces.md) | RTVS supporta l'associazione ad aree di lavoro locali e remote, consentendo all'utente di sviluppare localmente codice R con set di dati di dimensioni ridotte e quindi di eseguire facilmente tale codice su computer più potenti basati su cloud con set di dati molto più grandi. | n/d |
| [Opzioni di R Tools](options.md) | Consentono di controllare i diversi aspetti di RTVS. | [Finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md) |
| [Modifica avanzata, IntelliSense e frammenti di codice](code-editing.md) | Sono inclusi colorazione della sintassi, [IntelliSense](code-intellisense.md) in tutto il codice e in tutte le librerie, formattazione del codice, supporto per la firma, accesso alle definizioni, opzione per trovare tutti i riferimenti, [frammenti di codice](code-snippets.md) e altro ancora. | [Scrittura di codice nell'Editor di testo e del codice](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown.md) | I documenti R Markdown consentono di condividere i risultati dei dati, con codice R integrato all'interno di blocchi di codice markdown. | n/d |
| [Finestra interattiva](interactive-repl.md) | Fornisce un'esperienza completa di REPL per R con la possibilità di eseguire facilmente il codice in un file di origine nella finestra interattiva. | n/d |
| [Visualizzazione dei dati](visualizing-data.md) | La creazione di tracciati è parte integrante dell'esperienza R e RTVS supporta diverse finestre dei tracciati indipendenti, ciascuna delle quali con la propria cronologia e la possibilità di spostare tracciati da una finestra all'altra. I tracciati possono essere salvati in bitmap e file PDF oppure copiati negli Appunti come bitmap o metafile.  | n/d |
| [Variable Explorer](variable-explorer.md) | Consente di esaminare le variabili in ambiti globali o specifici del pacchetto, con la possibilità di visualizzare tabelle ordinabili ed eseguire l'esportazione in CSV. | n/d |
| [Debug con funzionalità complete](debugging.md) | Include l'integrazione con la finestra interattiva. | [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md) |

Il video seguente fornisce anche un breve riepilogo (5 minuti e 48 secondi) delle funzionalità di R Tools:

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="frequently-asked-questions"></a>Domande frequenti

**D. RTVS funziona con le edizioni di Visual Studio Express?**

R. No.

**D. Con quali interpreti R funziona RTVS?**

Un  [CRAN R](https://cran.r-project.org/), [Microsoft R Client e Microsoft R Server](https://msdn.microsoft.com/microsoft-r/)

**D. Dove è possibile scaricare questi interpreti?**

R. Vedere l'argomento [Installation](installation.md) (Installazione).

**D. È possibile usare estensioni di Visual Studio con RTVS?**

R. Certamente. Di seguito sono elencate alcune estensioni usate di frequente dagli utenti che utilizzano R.

- [VsVim per tasti di scelta rapida Vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor markdown con anteprima in tempo reale](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Per altre informazioni, vedere [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**D. Dato che RTVS è integrato in Visual Studio, significa che è possibile usarlo facilmente con C#, C++ e altri linguaggi Microsoft?**

R. No. RTVS è uno strumento per lo sviluppo di codice R e usa gli interpreti R nativi standard. L'interoperabilità tra R e altri linguaggi non è al momento supportata.

**D. La funzionalità X non è presente, mentre è disponibile in RStudio.**

R. RStudio è un IDE per R avanzato e maturo il cui sviluppo è in corso da diversi anni. RTVS tenta di offrire tutte le funzionalità critiche necessarie agli utenti. È consigliabile contribuire alla definizione delle priorità del lavoro futuro partecipando al [sondaggio RTVS](https://www.surveymonkey.com/r/RTVS1).

**D. RTVS funziona in OS X o Linux?**

Un  No, RTVS è basato su Visual Studio, un'implementazione solo per Windows. Detto questo, Microsoft sta analizzando la creazione di un nuovo set di strumenti basati su [Visual Studio Code](https://code.visualstudio.com/), il popolare editor multipiattaforma di Microsoft.

**D. È possibile contribuire a RTVS?**

R. Certamente. Il codice sorgente è disponibile su [GitHub](https://github.com/microsoft/RTVS). Usare la funzionalità di gestione dei problemi per segnalare bug e commentare quelli già registrati.

È anche possibile contribuire a questa documentazione. È sufficiente selezionare il comando **Modifica** disponibile in altro a destra in tutte le pagine. Sono inoltre benvenuti i commenti sulla documentazione, da aggiungere nella parte inferiore della pagina.

**D. RTVS funziona con il sistema di controllo del codice sorgente in uso?**

R. Sì, è possibile usare qualsiasi sistema di controllo del codice sorgente integrato in Visual Studio.

**D. RTVS funziona con impostazioni locali diverse dall'inglese?**

Un  La versione 1.0 di RTVS è solo in lingua inglese. La versione 1.1 sarà localizzata per lo stesso set di lingue di Visual Studio. Nel frattempo, usare [Visual Studio 2015 Language Pack](https://www.microsoft.com/download/details.aspx?id=48157) o, in Visual Studio 2017, eseguire il programma di installazione e selezionare Inglese nella scheda **Language Pack**.

![Impostazioni internazionali per Visual Studio 2017](media/FAQ-international-settings.png)

**D. RTVS funziona con edizioni di R a 32 bit?**

Un  No, RTVS supporta soltanto edizioni di R a 64 bit in esecuzione su edizioni di Windows a 64 bit.

**D. Apprezzo molto le impostazioni correnti di Visual Studio, ma vorrei provare le nuove impostazioni di Data Science. Come si deve procedere?**

R. Salvare le impostazioni correnti di Visual Studio usando **Strumenti > Importa/Esporta impostazioni**, quindi passare a Impostazioni di Data Science. Per ripristinare le impostazioni salvate, usare di nuovo il comando **Importa/Esporta impostazioni**.

**D. Quali sono le impostazioni `.gitignore` consigliate per un progetto RTVS?**

R. GitHub gestisce un repository master dei file `.gitignore` consigliati. È possibile visualizzarlo qui: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

**D. È possibile archiviare un progetto di Visual Studio in una condivisione di rete?**

Un  No, Visual Studio non supporta il caricamento di progetti da una condivisione di rete.

## <a name="send-us-your-feedback"></a>Inviateci i vostri commenti!

1. **Problemi GitHub**: il modo migliore per contattare il team RTVS consiste nel [segnalare un problema in GitHub](https://github.com/Microsoft/RTVS/issues) oppure usare il menu **R Tools > Feedback**.

1. **Invia smile/Invia faccia imbronciata**: il menu **R Tools > Feedback** è un modo rapido per inviare commenti e suggerimenti e allegare file di log RTVS per facilitare la diagnosi del problema. I log vengono scritti in `%temp%/RTVSlogs.zip`, nel caso li si voglia inviare separatamente. La registrazione è disabilitata se si è scelto di disattivare la telemetria di Visual Studio durante l'installazione oppure usando il comando di menu **Guida > Feedback > Impostazioni**.

1. **Messaggio di posta elettronica**: è possibile inviare commenti e suggerimenti direttamente al team all'indirizzo *rtvsuserfeedback (at) microsoft.com*.
