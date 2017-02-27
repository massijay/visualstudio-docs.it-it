---
title: "Avviare una sessione di debug per le app dello Store in Visual Studio (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.installedapppackagelauncher"
  - "vs.debug.error.wwahost_scriptdebuggingdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Avviare una sessione di debug per le app dello Store in Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Si applica a Windows e Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Questo argomento descrive come avviare una sessione di debug per le app di Windows Store scritte in JavaScript e HTML5. Puoi avviare il debug con una sola sequenza di tasti oppure puoi configurare la sessione di debug per scenari specifici e poi scegliere il modo in cui avviare l'app.  
  
> [!NOTE]
>  Per app scritte in XAML e Visual C\#, Visual C\+\+ o Visual Basic, vedi [Avviare una sessione di debug \(VB, C\#, C\+\+ e XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 [In questo argomento](#BKMK_In_this_topic)  
  
 [Il modo più semplice per avviare il debug](#BKMK_The_easy_way_to_start_debugging)  
  
 [Configurare la sessione di debug](#BKMK_Configure_the_debugging_session)  
  
-   [Aprire la pagina delle proprietà di debug per il progetto](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Scegliere le opzioni di configurazione della compilazione](#BKMK_Choose_the_build_configuration_options)  
  
-   [Scegliere la destinazione di distribuzione](#BKMK_Choose_the_deployment_target)  
  
-   [Scegliere il debugger da utilizzare](#BKMK_Choose_the_debugger_to_use)  
  
-   [Ritardare l'avvio dell'app nella sessione di debug (facoltativo)](#BKMK__Optional__Delay_starting_app_in_the_debug_session)  
  
-   [(Facoltativo) Disabilitare i loopback di rete](#BKMK__Optional__Disable_network_loopbacks)  
  
 [Avviare la sessione di debug](#BKMK_Start_the_debugging_session)  
  
-   [Avviare i debug (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Avviare il debug (F5) ma ritardare l'avvio dell'app](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
 [Avviare un'app installata nel debugger](#BKMK_Start_an_installed_app_in_the_debugger)  
  
 [Collegare il debugger a un'app in esecuzione](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
-   [Impostare l'esecuzione dell'app in modalità debug](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
-   [Collegare il debugger](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Il modo più semplice per avviare il debug  
 ![Si applica solo a Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
1.  Apri la soluzione dell'app in Visual Studio.  
  
2.  Se la soluzione contiene progetti sia per le app di Windows Store sia per le app di Windows Store Phone, assicurati che il progetto di cui vuoi eseguire il debug sia il progetto di avvio. In Esplora soluzioni seleziona il progetto e scegli **Imposta come progetto di avvio** dal menu di scelta rapida.  
  
3.  Premi F5.  
  
 ![Si applica solo a Windows Phone](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Visual Studio compila e avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione, se sospendi manualmente l'esecuzione, si verifica un'eccezione non gestita o l'app termina. Per altre informazioni, vedi [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md).  
  
##  <a name="BKMK_Configure_the_debugging_session"></a> Configurare la sessione di debug  
 Dato che lo script non è compilato, sono escluse le impostazioni relative a configurazione e piattaforma di compilazione. Se stai eseguendo il debug di un componente C\+\+ o gestito, imposta **Configurazione** su **Debug** e scegli la piattaforma di destinazione nella finestra di dialogo **Configurazione**.  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Aprire la pagina delle proprietà di debug per il progetto  
  
1.  Seleziona il progetto in Esplora soluzioni. Scegli **Proprietà** dal menu di scelta rapida.  
  
2.  Espandi il nodo **Proprietà di configurazione** e scegli **Debug**.  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a> Scegliere le opzioni di configurazione della compilazione  
  
1.  Dall'elenco **Configurazione** scegli **Debug** o **Debug \(attivo\)**.  
  
2.  Dall'elenco **Piattaforma** seleziona la piattaforma di destinazione per cui eseguire la compilazione. Nella maggior parte dei casi, la scelta migliore è l'opzione **Qualsiasi CPU**.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Scegliere la destinazione di distribuzione  
 Puoi distribuire ed eseguire il debug di un'app nel computer Visual Studio, nel simulatore di Visual Studio sul computer locale o in un computer remoto. Scegli la destinazione nell'elenco **Debugger da avviare** nella pagina delle proprietà **Debug** per il progetto.  
  
 ![Si applica solo a Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Per un'app di Windows Store, scegli una di queste opzioni nell'elenco **Dispositivo di destinazione**:  
  
|||  
|-|-|  
|**Computer locale**|Esegue il debug dell'app nella sessione corrente nel computer locale. Vedi [Eseguire applicazioni Windows Store in un computer locale](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulatore**|Esegue il debug dell'app nel simulatore di Visual Studio per le app di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. Il simulatore è una finestra del desktop che consente di eseguire il debug delle funzionalità del dispositivo, ad esempio i movimenti tocco e la rotazione del dispositivo, che non sono disponibile nel computer locale. Vedi [Eseguire applicazioni Windows Store nel simulatore](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Computer remoto**|Esegue il debug dell'app in un dispositivo connesso al computer locale su una rete Intranet o collegato direttamente tramite un cavo Ethernet. Per eseguire il debug in modalità remota, Visual Studio Remote Tools deve essere installato e in esecuzione sul dispositivo remoto. Vedi [Eseguire app di Windows Store in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Se scegli **Computer remoto**, specifica il nome o l'indirizzo IP del computer remoto nei modi seguenti:  
  
-   Immetti il nome o l'indirizzo IP del computer remoto nella casella **Nome computer**.  
  
-   Fai clic sulla freccia in giù nella casella **Nome computer** e scegli **\<Trova...\>**. Quindi, scegli il computer remoto nella finestra di dialogo **Seleziona connessione debugger remoto**.  
  
     ![Selezionare connessione debugger remoto](../debugger/media/vsrun_pro_selectremotedebuggerdlg.png "VSRUN\_PRO\_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  Nella finestra di dialogo Seleziona connessione debugger remoto sono visualizzati i computer sulla subnet locale e i computer collegati direttamente al computer che esegue Visual Studio tramite un cavo Ethernet. Per specificare un altro computer, immetti il nome nella casella **Nome computer**.  
  
 ![Si applica solo a Windows Phone](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Per un'app di Windows Store Phone, scegli **Dispositivo** o uno degli emulatori nell'elenco **Dispositivo di destinazione**.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a> Scegliere il debugger da utilizzare  
 Per impostazione predefinita, il debugger viene collegato al codice JavaScript nell'app. Puoi scegliere di eseguire il debug del codice gestito e C\+\+ nativo dei componenti dell'app invece che del codice JavaScript. Specifica il codice per cui eseguire il debug nell'elenco **Tipo di debugger** nella pagina delle proprietà **Debug** del progetto dell'app.  
  
 Scegli uno di questi debugger dall'elenco **Tipo di debugger**:  
  
|||  
|-|-|  
|**Solo script**|Esegue il debug del codice JavaScript nell'app. Il codice gestito e il codice nativo vengono ignorati.|  
|**Solo nativo**|Esegue il debug del codice C\/C\+\+ nativo nell'app. Il codice gestito e il codice JavaScript vengono ignorati.|  
|**Nativo con script**|Esegue il debug del codice C\+\+ nativo e del codice JavaScript nell'app.|  
|**Solo gestito**|Esegue il debug del codice gestito nell'app. Il codice JavaScript e il codice C\/C\+\+ nativo vengono ignorati.|  
|**Misto \(gestito e nativo\)**|Esegue il debug del codice C\+\+ nativo e del codice gestito nell'app. Il codice JavaScript viene ignorato.|  
  
###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> Ritardare l'avvio dell'app nella sessione di debug \(facoltativo\)  
 Per impostazione predefinita, Visual Studio avvia immediatamente l'app quando avvii il debug. Puoi anche avviare una sessione di debug ma ritardare l'avvio dell'app. L'app viene avviata nel debugger quando viene avviata dal menu Start o da un contratto di attivazione oppure da un altro processo o metodo. Puoi anche ritardare l'avvio per eseguire il debug di eventi in background nell'app che vuoi si verifichino quando l'app non è in esecuzione.  
  
 Specifica se vuoi ritardare l'avvio dell'app nell'elenco **Avvia applicazione** nella pagina delle proprietà **Debug** del progetto dell'app. Scegli una delle seguenti opzioni:  
  
-   Scegli **No** per ritardare l'avvio dell'app.  
  
-   Scegli **Sì** per avviare immediatamente l'app.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> \(Facoltativo\) Disabilitare i loopback di rete  
 ![Si applica solo a Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Per motivi di sicurezza, a un'app di Windows Store installata in modalità standard non è consentito effettuare chiamate di rete al dispositivo in cui è installata. Per impostazione predefinita, la distribuzione di Visual Studio crea una esenzione da questa regola per l'app distribuita. Questa esenzione ti consente di verificare le procedure di comunicazione in un singolo computer. Prima di inviare l'app a Windows Store, dovrai testare l'app senza l'esenzione.  
  
 Per rimuovere l'esenzione relativa al loopback della rete, scegli **No** nell'elenco **Consenti loopback della rete locale** nella pagina delle proprietà **Debug**.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Avviare la sessione di debug  
  
###  <a name="BKMK_Start_debugging__F5_"></a> Avviare i debug \(F5\)  
 Quando scegli **Avvia debug** dal menu **Debug**, \(tastiera: F5\) Visual Studio avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione, se sospendi manualmente l'esecuzione, si verifica un'eccezione non gestita o l'app termina.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Avviare il debug \(F5\) ma ritardare l'avvio dell'app  
 Puoi impostare l'app per l'esecuzione in modalità di debug, ma avviarla con un metodo diverso dal debugger. Ad esempio, puoi decidere di eseguire il debug dell'avvio dell'app dal menu Start o di eseguire il debug di un processo in background nell'app senza avviare l'app. Per ritardare l'avvio dell'app, procedi come indicato di seguito:  
  
1.  Nella pagina **Debug** delle proprietà del progetto dell'app seleziona **No** nell'elenco **Avvia applicazione**.  
  
2.  Scegli **Avvia debug** dal menu **Debug** \(tastiera: F5\).  
  
3.  Avvia l'app dal menu Start, da un contratto di esecuzione o da un'altra routine.  
  
 L'app viene avviata in modalità debug. L'esecuzione continua fino a raggiungere un punto di interruzione, se sospendi manualmente l'esecuzione, si verifica un'eccezione non gestita o l'app termina.  
  
 Per altre informazioni sul debug di attività in background, vedi [Attivare eventi di sospensione, ripresa e background per Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Avviare un'app installata nel debugger  
 Quando avvii il debug usando F5, Visual Studio compila e distribuisce l'app, la imposta per l'esecuzione in modalità debug, quindi la avvia. Per avviare un'app già installata in un dispositivo, utilizza la finestra di dialogo Debug pacchetto applicazione installato. Questa è una procedura utile per il debug di un'app installata da Windows Store o quando disponi dei file di origine dell'app, ma non di un progetto di Visual Studio per l'app. Ad esempio, potresti disporre di un sistema di compilazione personalizzato che non usa progetti o soluzioni di Visual Studio.  
  
 L'app può essere installata nel dispositivo locale oppure in un dispositivo remoto. Puoi avviare l'app immediatamente oppure impostarla per l'esecuzione nel debugger quando viene avviata da un altro processo o metodo, ad esempio dal menu Start o da un contratto di attivazione. Puoi anche impostarne l'esecuzione in modalità debug per eseguire il debug di un processo in background senza avviare l'app. Per altre informazioni, vedi [Attivare eventi di sospensione, ripresa e background per Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Per impostare l'esecuzione di un'app installata in modalità debug, procedi come indicato di seguito:  
  
> [!NOTE]
>  L'app non deve essere in esecuzione all'avvio della procedura.  
  
1.  Scegli **Debug pacchetto applicazione installato** dal menu **Debug**.  
  
2.  Scegli una delle opzioni seguenti dall'elenco:  
  
    |||  
    |-|-|  
    |**Computer locale**|Esegue il debug dell'app nella sessione corrente nel computer locale. Vedi [Eseguire applicazioni Windows Store in un computer locale](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
    |**Simulatore**|Esegue il debug dell'app nel simulatore di Visual Studio per le app di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. Il simulatore è una finestra del desktop che consente di eseguire il debug delle funzionalità del dispositivo, ad esempio i movimenti tocco e la rotazione del dispositivo, che non sono disponibile nel computer locale. Vedi [Eseguire applicazioni Windows Store nel simulatore](../debugger/run-windows-store-apps-in-the-simulator.md).|  
    |**Computer remoto**|Esegue il debug dell'app in un dispositivo connesso al computer locale su una rete Intranet o collegato direttamente tramite un cavo Ethernet. Per eseguire il debug in modalità remota, Visual Studio Remote Tools deve essere installato e in esecuzione sul dispositivo remoto. Vedi [Eseguire app di Windows Store in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
3.  Scegli l'app dall'elenco **Pacchetti applicazione installati**.  
  
4.  Scegli il motore di debug da usare dall'elenco **Debug tipo di codice**.  
  
5.  \(Facoltativo\). Scegli **Non eseguire il codice utente, ma eseguine il debug all'avvio** per il debug dell'app all'avvio tramite un altro metodo o per il debug di un processo in background.  
  
 Quando fai clic su **Start** l'app viene avviata o impostata per l'esecuzione in modalità debug.  
  
##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Collegare il debugger a un'app in esecuzione  
 Per collegare il debugger a un'app di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], devi usare Debuggable Package Manager per impostare l'esecuzione dell'app in modalità debug. Debuggable Package Manager viene installato con Visual Studio Remote Tools.  
  
 Il collegamento del debugger a un'app è utile quando devi eseguire il debug di un'app già installata, ad esempio un'app installata da Windows Store. Il collegamento è necessario quando disponi dei file di origine dell'app, ma non di un progetto di Visual Studio per l'app. Ad esempio, potresti disporre di un sistema di compilazione personalizzato che non usa progetti o soluzioni di Visual Studio.  
  
 Per collegare il debugger a un'app:  
  
1.  Imposta l'esecuzione dell'app in modalità debug. Questa operazione deve essere effettuata quando l'app non è in esecuzione.  
  
2.  Avvia l'app. Puoi avviare l'app dal menu Start, da un contratto di esecuzione o con un altro metodo.  
  
3.  Collega il debugger all'app in esecuzione.  
  
###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Impostare l'esecuzione dell'app in modalità debug  
  
1.  Installa Visual Studio Remote Tools sul dispositivo in cui è installata l'app. Vedi [Installazione di Remote Tools](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  Nel menu Start cerca `Debuggable Package Manager` e avvialo.  
  
     Viene visualizzata una finestra di PowerShell correttamente configurata per il cmdlet AppxDebug.  
  
3.  Per abilitare il debug di un'app, devi specificare l'identificatore PackageFullName dell'app. Per visualizzare un elenco di tutte le app che includono PackageFullName, digita `Get-AppxPackage` al prompt di PowerShell.  
  
4.  Al prompt di PowerShell immetti `Enable-AppxDebug` *PackageFullName*, dove *PackageFullName* è l'identificatore PackageFullName dell'app.  
  
###  <a name="BKMK_Attach_the_debugger"></a> Collegare il debugger  
  
> [!TIP]
>  Le app JavaScript vengono eseguite in un'istanza del processo wwahost.exe. Se vengono eseguite altre app JavaScript quando colleghi il debugger all'app, dovrai conoscere l'ID processo numerico \(PID\) del processo wwahost.exe in cui viene eseguita l'app.  
>   
>  Il modo più semplice per gestire questa situazione consiste nel chiudere tutte le altre app JavaScript. Altrimenti, puoi aprire Gestione attività di Windows prima di avviare l'app e annotare gli ID dei processi wwahost.exe. Quando specifichi il processo a cui collegare il debugger nella finestra di dialogo **Processi disponibili**, il processo wwahost.exe dell'app avrà un ID diverso da quelli annotati.  
  
 Per collegare il debugger:  
  
1.  Scegli **Connetti a processo** dal menu **Debug**.  
  
     Verrà visualizzata la finestra di dialogo **Connetti a processo**.  
  
2.  Per connetterti a un'app in un dispositivo remoto, specifica il dispositivo remoto nella casella **Qualificatore**. Procedi così:  
  
    -   Immetti il nome nella casella **Qualificatore**.  
  
    -   Fai clic sulla freccia in giù nella casella **Qualificatore** e seleziona il dispositivo in un elenco di dispositivi collegati in precedenza.  
  
    -   Scegli **Trova** per selezionare il dispositivo in un elenco di dispositivi sulla subnet locale.  
  
3.  Specifica il tipo di codice di cui vuoi eseguire il debug nella casella **Connetti a**.  
  
     Scegli **Seleziona** e quindi esegui una delle operazioni seguenti:  
  
    -   Scegli **Determina automaticamente il tipo di codice di cui eseguire il debug**  
  
    -   Scegli **Esegui il debug di questi tipi di codice**, quindi scegli uno o più tipi dall'elenco.  
  
4.  Nell'elenco **Processi disponibili** seleziona il processo **wwahost.exe** appropriato. Usa la colonna **Titolo** per identificare la tua app.  
  
5.  Scegli **Connetti**.  
  
 Visual Studio collega il debugger al processo. L'esecuzione continua fino a raggiungere un punto di interruzione, se sospendi manualmente l'esecuzione, si verifica un'eccezione non gestita o l'app termina.  
  
## Vedere anche  
 [Controllare l'esecuzione in una sessione di debug \(JavaScript\)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Attivare eventi di sospensione, ripresa e background per Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Eseguire il debug di app in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)