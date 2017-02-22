---
title: "Procedura: Raccogliere dati sulle prestazioni per un sito Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.url.url"
  - "vsperf.chooseurl"
  - "vs.performance.wizard.asppage"
  - "vsperf.url.ok"
  - "vsperf.url.cancel"
helpviewer_keywords: 
  - "strumenti per la profilatura, profilatura ASP.NET"
  - "siti Web, profilatura delle prestazioni"
  - "ASP.NET, profilatura delle prestazioni"
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Raccogliere dati sulle prestazioni per un sito Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per raccogliere dati sulle prestazioni di un'applicazione Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], è possibile usare la **Creazione guidata sessione di prestazioni**. È possibile profilare un'applicazione Web aperta in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oppure un sito Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] presente nel computer locale e non aperto nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  La **Creazione guidata sessione di prestazioni** consente di aggiungere dati di interazione tra livelli \(TIP\), dati relativi alle prestazioni di JScript o entrambi ai dati di profilatura raccolti. L'opzione TIP raccoglie dati dai processi sul lato server. L'opzione di profilatura JScript raccoglie dati da script in esecuzione in un sito Web locale o remoto. Nella maggior parte dei casi, è consigliabile scegliere solo una delle opzioni.  
  
 In base alle autorizzazioni di accesso a livello utente che un amministratore ha reso disponibili, un singolo utente può avere o meno le autorizzazioni di sicurezza necessarie per creare una sessione del profiler sul computer che ospita il processo ASP.NET. Gli esempi seguenti illustrano le possibili differenze tra i diversi tipi di utenti:  
  
-   Se l'amministratore ha impostato l'avvio del driver e del servizio, alcuni utenti possono accedere a funzionalità di profilatura avanzate.  
  
-   Gli utenti di dominio possono accedere soltanto ad esempi di profilatura.  
  
-   Alcuni utenti possono negare l'accesso alle funzionalità di profilatura a tutti gli altri utenti.  
  
 Per altre informazioni, vedere [Profilatura e sicurezza in Windows Vista](../profiling/profiling-and-windows-vista-security.md) e le opzioni ADMIN in [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Per profilare un progetto di sito Web  
  
1.  Aprire il progetto Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] o [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)].  
  
2.  Nel menu **Analizza** fare clic su **Avvia Creazione guidata sessione di prestazioni**.  
  
3.  Nella prima pagina della procedura guidata selezionare un metodo di profilatura e quindi fare clic su **Avanti**. Per altre informazioni sui metodi di profilatura, vedere [Informazioni sui metodi di profilatura](../profiling/understanding-performance-collection-methods.md). Tenere presente che il metodo di profilatura del visualizzatore di concorrenza non è disponibile per le applicazioni Web.  
  
4.  Nell'elenco a discesa **Specificare l'applicazione di destinazione per la profilatura** verificare che il progetto corrente sia selezionato e quindi fare clic su **Avanti**.  
  
5.  Nella terza pagina della procedura guidata è possibile scegliere di aggiungere dati di profilatura dell'interazione tra livelli \(TIP\), dati da JavaScript in esecuzione nelle pagine Web o entrambi.  
  
    -   Per raccogliere dati di interazione tra livelli, selezionare la casella di controllo **Abilita profilatura interazione tra livelli**.  
  
    -   Per raccogliere dati da JavaScript in esecuzione nelle pagine Web, selezionare la casella di controllo **Profila JavaScript**.  
  
6.  Scegliere **Avanti**.  
  
7.  Nella quarta pagina della procedura guidata fare clic su **Fine**.  
  
8.  Verrà creata una sessione di prestazioni per l'applicazione di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e il sito Web verrà avviato nel browser. Verificare la funzionalità che si vuole profilare e quindi chiudere il browser.  
  
     Il profiler genera il file di dati e apre la visualizzazione Riepilogo dei dati nella finestra principale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Per profilare un sito Web senza aprire un progetto in Visual Studio  
  
1.  Aprire [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] o [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)].  
  
2.  Nel menu **Analizza** fare clic su **Avvia Creazione guidata sessione di prestazioni**.  
  
3.  Nella prima pagina della procedura guidata selezionare un metodo di profilatura e quindi fare clic su **Avanti**. Per altre informazioni, vedere [Informazioni sui metodi di profilatura](../profiling/understanding-performance-collection-methods.md).  
  
4.  Nella seconda pagina della procedura guidata, selezionare l'opzione **Profilatura di un'applicazione ASP.NET o JavaScript** e quindi fare clic su **Avanti**.  
  
5.  Nella terza pagina della procedura guidata digitare l'URL della home page dell'applicazione nella casella **Specificare l'URL o il percorso che esegue l'applicazione Web** e quindi fare clic su **Avanti**.  
  
    -   Per un sito Web basato su server \(IIS\), digitare un URL, ad esempio **http:\/\/localhost\/MySite\/default.aspx**. In questo modo verrà profilata l'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] presente nel computer locale nella radice dell'applicazione di MySite e in Internet Explorer verrà aperta la pagina default.aspx del sito per avviare la sessione.  
  
    -   Per un sito Web basato su file, digitare un percorso, ad esempio file\/\/\/**c:\\WebSites\\MySite\\default.aspx**. In questo modo verrà profilata l'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] presente in c:\\webSites\\MySite e in Internet Explorer verrà aperta la pagina http:\/\/localhost:nnnn\/MySite\/default.aspx per avviare la sessione.  
  
    -   Per i siti esterni sui quali si vuole raccogliere dati JavaScript, digitare l'URL, ad esempio http:\/\/www.contoso.com.  
  
     Per altre informazioni, visualizzare le pagine delle proprietà per un file binario di destinazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
6.  Nella terza pagina della procedura guidata è possibile scegliere di aggiungere dati di profilatura dell'interazione tra livelli \(TIP\), dati da JavaScript in esecuzione nelle pagine Web o entrambi.  
  
    -   Per raccogliere dati di interazione tra livelli, selezionare la casella di controllo **Abilita profilatura interazione tra livelli**.  
  
    -   Per raccogliere dati da JavaScript in esecuzione nelle pagine Web, selezionare la casella di controllo **Profila JavaScript**.  
  
7.  Scegliere **Avanti**.  
  
8.  Nella quarta pagina della procedura guidata fare clic su **Fine**.  
  
9. Verrà creata una sessione di prestazioni per l'applicazione ASP.NET e il sito Web verrà avviato nel browser. Verificare la funzionalità che si vuole profilare e quindi chiudere il browser.  
  
     Il profiler genera il file di dati e apre la visualizzazione Riepilogo dei dati nella finestra principale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vedere anche  
 [Cenni preliminari](../profiling/overviews-performance-tools.md)   
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)