---
title: Strumenti di profilatura in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 09c33f3cc331af03659922e178e4089f177132de
ms.contentlocale: it-it
ms.lasthandoff: 05/13/2017

---
# <a name="profiling-tools"></a>Strumenti di profilatura
Gli strumenti di profilatura e diagnostica consentono di diagnosticare l'utilizzo della memoria e della CPU e altri problemi a livello di applicazione. Con questi strumenti è possibile accumulare i dati, ad esempio i valori delle variabili, le chiamate di funzione e gli eventi, in base al tempo di esecuzione dell'applicazione nel debugger. È possibile visualizzare lo stato dell'applicazione in punti diversi durante l'esecuzione del codice.  
  
 Consultare il riepilogo in basso per vedere quali strumenti sono disponibili per il tipo di progetto, ad esempio, desktop, UWP, ASP.NET.  
  
 Per accedere agli strumenti di profilatura, usare **Debug / Windows / Mostra strumenti di diagnostica** per usare gli strumenti durante la sessione di debug. In alternativa, eseguire un'analisi dopo che l'applicazione è terminata usando approcci differenti.  Per altre informazioni sui diversi approcci, vedere [Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) (Eseguire gli strumenti di profilatura con o senza il debugger).
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")
  
 Per informazioni sulle nuove funzionalità per questa versione, vedere [Novità introdotte negli strumenti di diagnostica](../profiling/what-s-new-in-profiling-tools.md).
  
 Nelle sezioni seguenti vengono descritti i diversi strumenti di prestazioni disponibili in Visual Studio.
  
## <a name="memory-usage"></a>Utilizzo memoria  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 È possibile rilevare perdite e inefficienze di funzionamento della memoria durante il debug con lo strumento **Utilizzo memoria**, che consente di creare snapshot dell'heap di memoria gestito e nativo. È possibile usare questo strumento con le applicazioni desktop, le app universali di Windows e le applicazioni ASP.NET. Lo strumento **Utilizzo memoria** può essere eseguito dalla finestra **Strumenti di diagnostica** durante il debug (**Debug / Windows / Mostra strumenti di diagnostica**) o all'esterno del debugger (**Debug / Profiler prestazioni**). Per altre informazioni, vedere [Utilizzo memoria](../profiling/memory-usage.md) e [Utilizzo memoria senza debug](../profiling/Memory-Usage-without-Debugging2.md).  
  
## <a name="cpu-usage"></a>Utilizzo CPU  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 Lo strumento **Utilizzo CPU** indica i punti in cui la CPU impiega più tempo per l'esecuzione di codice C++, C#/VB e JavaScript.  È possibile usare questo strumento con le applicazioni desktop e le app universali di Windows, nonché con le app ASP.NET e del Servizio app di Azure. Lo strumento **Utilizzo CPU** può essere eseguito dalla finestra **Strumenti di diagnostica** durante il debug (**Debug / Windows / Mostra strumenti di diagnostica**) o all'esterno del debugger (**Debug / Profiler prestazioni**). Per altre informazioni, vedere [Beginner's Guide to Performance Profiling](../profiling/beginners-guide-to-performance-profiling.md) (Guida per principianti alla profilatura delle prestazioni) e [CPU Usage](../profiling/cpu-usage.md) (Utilizzo CPU).
  
## <a name="gpu-usage"></a>Utilizzo GPU  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Usare lo strumento [Utilizzo GPU](../debugger/gpu-usage.md) per comprendere meglio l'utilizzo dell'hardware di alto livello dell'app Direct3D. È possibile usare questo strumento sia con le applicazioni desktop che con le app universali di Windows, ma non con le applicazioni ASP.NET. Lo strumento **Utilizzo GPU** può essere eseguito all'esterno del debugger (**Debug / Profiler prestazioni**).  
  
## <a name="application-timeline"></a>Sequenza temporale applicazione  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 Lo strumento [Sequenza temporale applicazione](../profiling/application-timeline.md) consente di migliorare le prestazioni delle applicazioni XAML offrendo una visualizzazione dettagliata dell'utilizzo delle risorse. È possibile usare lo strumento **Sequenza temporale applicazione** sia con le applicazioni desktop che con le app universali di Windows, ma non con le applicazioni ASP.NET. Lo strumento **Sequenza temporale applicazioni** può essere eseguito all'esterno del debugger (**Debug / Profiler prestazioni**).
  
## <a name="perftips"></a>PerfTips  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Quando il debugger interrompe l'esecuzione in un punto di interruzione o un'operazione passo a passo, il tempo trascorso tra l'interruzione e il precedente punto di interruzione viene visualizzato come un suggerimento nella finestra dell'editor. Questi [PerfTips](../profiling/perftips.md) consentono di monitorare e analizzare le prestazioni dell'applicazione durante il debug. È possibile visualizzare i **PerfTips** nelle applicazioni desktop, universali di Windows e ASP.NET.

## <a name="performance-explorer"></a>Esplora prestazioni  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **Esplora prestazioni** (**Debug / Profiler / Esplora prestazioni**) consente di usare molti strumenti diversi, tra cui **Campionamento CPU**,  **Strumentazione**, **Allocazione della memoria .NET**e **Conflitto di risorse**. È possibile usare gli strumenti di Esplora prestazioni con le applicazioni desktop e ASP.NET, ma non con le app universali di Windows. Per altre informazioni, vedere [Esplora prestazioni](../profiling/performance-explorer.md).

 > [!NOTE]
 > A meno che non si voglia eseguire un'attività specializzata, come la strumentazione, usare strumenti di diagnostica quali Utilizzo memoria e Utilizzo CPU anziché Esplora prestazioni, che è ora uno strumento legacy.
  
## <a name="javascript-memory"></a>Memoria JavaScript  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 Lo strumento [Memoria JavaScript](../profiling/javascript-memory.md) consente di individuare le perdite di memoria e i problemi di utilizzo inefficiente della memoria nelle app. Lo strumento consente di creare snapshot dell'heap JavaScript. È possibile usare questo strumento con le app HTML universali di Windows. Lo strumento **Memoria JavaScript** può essere eseguito all'esterno del debugger (**Debug / Profiler prestazioni**).  
  
## <a name="html-ui-responsiveness"></a>Velocità di risposta interfaccia utente HTML  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 Lo strumento [Velocità di risposta interfaccia utente HTML](../profiling/html-ui-responsiveness.md) consente di isolare i problemi di prestazioni delle app, inclusi velocità di risposta insufficiente, tempo di caricamento lento e aggiornamenti visivi meno frequenti del previsto. È possibile usare questo strumento con le app HTML universali di Windows. Lo strumento **Velocità di risposta interfaccia utente HTML** può essere eseguito all'esterno del debugger (**Debug / Profiler prestazioni**).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) consente di registrare eventi specifici, esaminare i dati della finestra **Variabili locali** durante gli eventi del debugger e le chiamate di funzioni, nonché gli errori di debug difficili da riprodurre.  IntelliTrace è principalmente uno strumento di debug, ma offre anche informazioni che possono essere usate per l'analisi delle prestazioni. È possibile usare questo strumento solo in Visual Studio Enterprise con applicazioni desktop, universali di Windows ASP.NET in C#. IntelliTrace è disponibile nella finestra **Strumenti di diagnostica** durante il debug (**Debug / Windows / Mostra strumenti di diagnostica**).  
  
## <a name="profiling-in-production"></a>Profilatura in fase di produzione  
 L'approccio consigliato per la profilatura in fase di produzione è eseguire la profilatura dalla [riga di comando usando vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) per raccogliere un profilo della CPU. Per il supporto per la profilatura remota nei servizi app di Azure, è possibile eseguire la profilatura da [Esplora Server o il portale di Kudu](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/).  
  
## <a name="which-tool-should-i-use"></a>Quale strumento utilizzare?  
 Nella tabella seguente sono riportati i diversi strumenti offerti da Visual Studio e i diversi tipi di progetto con cui possono essere usati:  
  
|Strumento di prestazioni|Desktop di Windows|Windows Store/universale|ASP.NET/ASP.NET Core|  
|----------------------|---------------------|------------------------------|-------------|  
|[Utilizzo memoria](../profiling/memory-usage.md)|sì|sì|sì|  
|[Utilizzo CPU](../profiling/cpu-usage.md)|sì|sì|sì|  
|[Utilizzo GPU](../debugger/gpu-usage.md)|sì|sì|no|  
|[Sequenza temporale applicazione](../profiling/application-timeline.md)|sì|sì|no|  
|[PerfTips](../profiling/perftips.md)|sì|Sì per XAML, no per HTML|sì|  
|[Esplora prestazioni](../profiling/performance-explorer.md)|sì|no|sì (no per ASP.NET Core)|  
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET Enterprise|Solo .NET Enterprise|Solo .NET Enterprise|
|[Utilizzo della rete](../profiling/network-usage.md)|no|sì|no| 
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|no|Sì per HTML, no per XAML|no|  
|[Memoria JavaScript](../profiling/javascript-memory.md)|no|Sì per HTML, no per XAML|no|  
  
## <a name="see-also"></a>Vedere anche  
 [IDE di Visual Studio](../ide/visual-studio-ide.md)
