---
title: "Installazione di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.about"
helpviewer_keywords: 
  - "Visual Studio, installazione"
  - "installazione di Visual Studio"
  - "installazioni server [Visual Studio]"
  - "installazione [Visual Studio]"
  - "installare Visual Studio"
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 177
caps.handback.revision: 150
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Installazione di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa pagina include informazioni dettagliate per l'installazione di Visual Studio 2015, la suite integrata di strumenti di produttività per gli sviluppatori. Sono stati inclusi anche alcuni collegamenti che permettono di accedere rapidamente a informazioni su [funzionalità](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx), [edizioni](http://go.microsoft.com/fwlink/?LinkID=242142), [requisiti di sistema](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [download](http://go.microsoft.com/fwlink/?LinkId=517106) e altro ancora.  
  
> [!TIP]
>  Per visualizzare informazioni sull'installazione di versioni precedenti di Visual Studio, fare clic sul collegamento "Altre versioni" nella parte superiore della pagina.  
  
## Collegamenti rapidi  
 Prima di entrare nei dettagli, ecco un elenco dei collegamenti richiesti più frequentemente.  
  
|Funzionalità|  
|------------------|  
|Per altre informazioni sulle funzionalità nuove o aggiornate in Visual Studio 2015, vedere le note sulla versione per [Visual Studio 2015 RTM](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx) e [Visual Studio 2015 Update 1](https://www.visualstudio.com/news/vs2015-update1-vs).|  
|Per informazioni sulle funzionalità disponibili in ogni edizione di Visual Studio 2015, vedere la pagina [Confrontare le offerte di Visual Studio](http://go.microsoft.com/fwlink/?LinkID=242142).|  
|Per visualizzare i requisiti di sistema per ogni edizione di Visual Studio 2015, vedere la pagina [Compatibilità di Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs).|  
|Per installare Visual Studio 2015, scaricarlo da [Download di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=517106) oppure usare i supporti di installazione del prodotto confezionato.|  
|Per trovare il codice Product Key, vedere l'argomento [Procedura: individuare il codice Product Key di Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md).|  
|Per informazioni sulle opzioni di licenza per i singoli utenti o i clienti aziendali, vedere il white paper sulle [licenze di Visual Studio e MSDN](https://www.microsoft.com/download/details.aspx?id=13350).|  
  
##  <a name="custom"></a> Confronto tra installazione predefinita e installazione personalizzata  
 Quando si installa Visual Studio 2015, è possibile includere o escludere i componenti che verranno usati ogni giorno. Questo vuol dire che un'installazione predefinita sarà spesso di dimensioni inferiori e verrà eseguita più rapidamente rispetto a un'installazione personalizzata. Significa anche che molti componenti che venivano installati per impostazione predefinita nelle versioni precedenti, ora sono considerati componenti personalizzati che è necessario selezionare in modo esplicito in questa versione.  
  
 ![Finestra di dialogo di installazione di Visual Studio 2015](~/docs/ide/media/vs2015_setup_screen.png "VS2015\_Setup\_screen")  
  
 I componenti personalizzati includono Visual C\+\+, Visual F\#, SQL Server Data Tools, strumenti mobili multipiattaforma e SDK, oltre a SDK ed estensioni di terze parti. Se i componenti personalizzati non vengono selezionati durante l'installazione iniziale, è possibile installarli in un secondo momento.  
  
> [!NOTE]
>  Un'installazione personalizzata include anche i componenti disponibili con l'installazione predefinita.  
  
 Di seguito è riportato l'elenco completo dei componenti personalizzati:  
  
-   **Linguaggi di programmazione**  
  
    -   Compilatori, librerie e strumenti Visual C\+\+  
  
    -   Visual F\#  
  
    -   Python Tools per Visual Studio  
  
-   **Windows e sviluppo Web**  
  
    -   Strumenti di pubblicazione ClickOnce  
  
    -   Microsoft SQL Server Data Tools  
  
    -   Microsoft Web Developer Tools  
  
    -   PowerShell Tools per Visual Studio  
  
    -   Kit di sviluppo di Silverlight  
  
    -   Strumenti per lo sviluppo di app universali di Windows  
  
    -   SDK e strumenti di Windows 10  
  
    -   Strumenti di Windows 8.1 e Windows Phone 8.0\/8.1  
  
    -   SDK e strumenti di Windows 8.1  
  
-   **Sviluppo mobile multipiattaforma**  
  
    -   Xamarin \(C\#\/.NET\)  
  
    -   Apache Cordova \(HTML\/JavaScript\)  
  
    -   Visual C\+\+ Mobile Development per iOS\/Android  
  
-   **SDK e strumenti comuni**  
  
    -   Android Native Development Kit \(R10E, 32 bit\)  
  
    -   Android SDK  
  
    -   Installazione di Android SDK \(livello API 19 e 21\)  
  
    -   Installazione di Android SDK \(livello API 22\)  
  
    -   Apache Ant \(1.9.3\)  
  
    -   Java SE Development Kit \(7.0.550.13\)  
  
    -   Joyent Node.js  
  
-   **Strumenti comuni**  
  
    -   Git per Windows  
  
    -   Estensioni GitHub per Visual Studio  
  
    -   Strumenti di estendibilità in Visual Studio  
  
##  <a name="installing"></a> Installare Visual Studio  
 Per installare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è necessario disporre delle credenziali di amministratore. Tuttavia, dopo l'installazione le credenziali non sono necessarie per usare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Per l'account dell'amministratore locale deve essere abilitati i privilegi seguenti per installare tutti gli elementi in Visual Studio.  
  
|Nome visualizzato dell'oggetto criterio locale|Diritto utente|  
|----------------------------------------------------|--------------------|  
|Backup di file e directory|SeBackupPrivilege|  
|Debug di programmi|SeDebugPrivilege|  
|Gestione registro di controllo e di protezione|SeSecurityPrivilege|  
  
 Per altre informazioni sui requisiti di questo account amministratore locale, vedere l'articolo della Knowledge Base, [L'installazione di SQL Server non riesce se l'account di configurazione non ha determinati diritti utente](https://support.microsoft.com/en-us/kb/2000257).  
  
###  <a name="BKMK_Media"></a> Installazione tramite supporti di installazione  
  
-   Per installare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], nella directory radice sui supporti di installazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], eseguire il file di installazione per l'edizione preferita:  
  
    |Edizione|File di installazione|  
    |--------------|---------------------------|  
    |Visual Studio Enterprise|vs\_enterprise.exe|  
    |Visual Studio Professional|vs\_professional.exe|  
    |Community di Visual Studio|vs\_community.exe|  
  
###  <a name="BKMK_Website"></a> Installazione mediante il download dal sito Web del prodotto  
  
-   Vedere la pagina [Download di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=517106) sul sito Web VisualStudio.com.  
  
###  <a name="BKMK_Offline"></a> Download di Visual Studio per un'installazione offline  
 In molti casi è possibile installare Visual Studio dal sito di download senza problemi. Tuttavia, in alcuni casi potrebbe essere necessario scaricare tutti i pacchetti di aggiornamento prima dell'installazione, ad esempio per eseguire l'installazione su più computer o su un computer offline. Nei passaggi seguenti viene illustrato come scaricare tutti i pacchetti di aggiornamento necessari per un'installazione offline.  
  
1.  Dopo aver scaricato l'eseguibile di aggiornamento dal sito Web MSDN in una posizione nel file system, eseguire il seguente comando dal prompt dei comandi: `<executable name> /layout`.  
  
     Questo comando scarica tutti i pacchetti di installazione.  
  
     Usando l'opzione `/layout` è possibile scaricare quasi tutti i pacchetti di installazione principali, non solo quelli adatti al computer di download. Questo approccio fornisce tutti i file necessari per eseguire l'aggiornamento da qualsiasi posizione e può essere utile per installare i componenti non installati in origine.  
  
2.  Dopo avere eseguito il comando, dovrebbe venire chiesto il percorso di download. Immettere il percorso e scegliere **Scarica**.  
  
3.  Se il download del pacchetto viene completato correttamente, verrà visualizzata una schermata di Visual Studio in cui è indicato **Installazione completata**. **Tutti i componenti specificati sono stati acquisiti correttamente.**  
  
4.  Nel percorso del file specificato individuare il file eseguibile e la cartella del pacchetto. Questo è tutto quello che occorre per eseguire la copia in un percorso condiviso o nei supporti di installazione.  
  
    > [!CAUTION]
    >  Al momento, Android SDK non supporta un'esperienza di installazione offline. Se si installano gli elementi del programma di installazione di Android SDK in un computer non connesso a internet, l'installazione potrebbe non riuscire.  
  
5.  È ora possibile eseguire l'installazione dal percorso del file o dal supporto di installazione.  
  
###  <a name="BKMK_Virtualized"></a> Installazione di Visual Studio in ambienti virtualizzati  
 **Problemi video con Hyper\-V**  
  
 Se si esegue Windows Server 2008 R2 con Hyper\-v abilitato e una scheda grafica con accelerazione, è possibile che si verifichino rallentamenti del sistema.  
  
 Per altre informazioni, vedere la seguente pagina sul sito Web Microsoft: [Possibile riduzione delle prestazioni video quando in un computer con Windows Server 2008 o Windows Server 2008 R2 è abilitato il ruolo Hyper\-V ed è installata una scheda video con accelerazione](http://go.microsoft.com/fwlink/?LinkID=231084).  
  
 **Emulazione di dispositivi con Hyper\-V**  
  
 Quando si installa Visual Studio 2015 sull'hardware effettivo senza virtualizzazione, è possibile scegliere le funzionalità che consentono l'emulazione di dispositivi Windows e Android usando Hyper\-V. Quando si esegue l'installazione in Hyper\-V, non sarà possibile emulare i dispositivi Windows o Android. Infatti, gli emulatori sono a loro volta macchine virtuali e attualmente non è possibile ospitare una macchina virtuale all'interno di un'altra macchina virtuale. La soluzione alternativa è costituita dagli effettivi dispositivi Windows o Android in cui è possibile distribuire direttamente l'applicazione ed eseguirne il debug.  
  
## Uso dei parametri della riga di comando  
 Quando si esegue l'applicazione di installazione, è possibile usare i seguenti parametri della riga di comando, senza distinzione tra maiuscole e minuscole.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**\/?**<br /><br /> **\/help**<br /><br /> **\/h**|Visualizza i parametri della riga di comando.|  
|**\/AddRemoveFeatures**|Specifica le funzionalità da aggiungere o rimuovere dal prodotto installato.|  
|**\/AdminFile** *AdminDeployment.xml*|Installa Visual Studio tramite il file di dati specificato per l'installazione amministrativa.|  
|**\/CEIPConsent**|Consente la raccolta di informazioni per migliorare l'analisi utilizzo software in conformità all'Informativa sulla privacy del prodotto.|  
|**\/ChainingPackage** *NomeBundle*|Specifica quale bundle è concatenato a questo bundle. Può anche essere usato per specificare una coorte nel programma Analisi utilizzo software.|  
|**\/CreateAdminFile \<filename\>**|Specifica il percorso per creare un file di controllo che può essere usato con \/AdminFile|  
|**\/CustomInstallPath** *DirectoryInstallazione*|Installa tutti i pacchetti con destinazione modificabile nella directory specificata.|  
|**\/ForceRestart**|Riavvia sempre il computer dopo l'installazione.|  
|**\/full**|Installa tutte le funzionalità del prodotto.|  
|**\/InstallSelectableItems \<item name 1\>\[;\<item name 2\>\]**|Elenco di elementi della struttura ad albero per la selezione da controllare nella schermata di selezione dell'installazione guidata.|  
|**\/l**<br /><br /> **\/Log** *NomeFile*|Specifica un percorso per il file di log.|  
|**\/layout** *Directory*|Copia i file sul supporto di installazione nella directory specificata.|  
|**\/NoCacheOnlyMode**|Impedisce il prepopolamento della cache del pacchetto.|  
|**\/NoRefresh**|Impedisce il controllo nelle versioni più recenti di questo prodotto della disponibilità di versioni aggiornate richieste o consigliate.|  
|**\/norestart**|Impedisce il riavvio dell'applicazione di installazione dal computer durante o dopo l'installazione. Per i codici restituiti da cercare, vedere la sezione della [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md).|  
|**\/noweb**|Impedisce l'installazione da Internet.|  
|**\/OverrideFeedUri \<path to feed file\>**|Percorso di un feed esterno locale che descrive gli elementi software|  
|**\/ProductKey**<br /><br /> *ProductKey*|Imposta un codice Product Key personalizzato che non includa trattini e non contenga più di 25 caratteri.|  
|**\/PromptRestart**|Richiede una conferma all'utente prima di riavviare il computer.|  
|**\/q**<br /><br /> **\/quiet**<br /><br /> **\/s**<br /><br /> **\/silent**|Elimina l'interfaccia utente \(UI\) per l'applicazione di installazione. Se Visual Studio è già installato e non vengono specificati altri parametri tranne questo, l'applicazione di installazione viene eseguita in modalità di manutenzione.|  
|**\/qb**<br /><br /> **\/passive**|Mostra l'avanzamento ma non attende l'input dell'utente.|  
|**\/repair**|Ripristina Visual Studio.|  
|**\/SuppressRefreshPrompt**|Impedisce la visualizzazione della finestra di dialogo che informa della disponibilità dell'aggiornamento. In tal modo, l'installazione guidata accetterà automaticamente eventuali versioni aggiornate richieste o consigliate.|  
|**\/u**<br /><br /> **\/Uninstall**|Disinstalla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|**\/Uninstall \/Force**<br /><br /> **\/u \/force**|Disinstalla Visual Studio e tutte le funzionalità condivise con altri prodotti. **Warning:**  Se si usa questo parametro, altri prodotti installati nello stesso computer potrebbero smettere di funzionare correttamente.|  
  
 Quando si esegue il programma di installazione dalla riga di comando, è possibile acquisire ed elaborare il codice restituito per una migliore esperienza della riga di comando.  Per altre informazioni, vedere la [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md).  
  
##  <a name="troubleshooting"></a> Risoluzione dei problemi relativi all'installazione  
 Usare queste risorse per ottenere assistenza riguardo problemi di configurazione e installazione:  
  
-   Forum relativo alla [configurazione e installazione di Visual Studio](http://go.microsoft.com/fwlink/?LinkID=151190). Leggere domande e risposte di altri utenti della community di Visual Studio. Se non si trova la risposta desiderata, è possibile porre una domanda.  
  
-   Sito Web del [Supporto tecnico Microsoft per Visual Studio](http://go.microsoft.com/fwlink/?LinkID=251019). Leggere gli articoli della Knowledge Base \(KB\) e scoprire come contattare il supporto Microsoft per ottenere informazioni sui problemi di installazione di Visual Studio.  
  
-   Per le versioni di Visual Studio 2015 è possibile segnalare un problema usando il sito Connect all'indirizzo [https:\/\/connect.microsoft.com\/visualstudio](https://connect.microsoft.com/visualstudio).  
  
     È consigliabile includere i log di installazione nella descrizione del problema. È possibile preparare i log per la segnalazione del problema usando Microsoft Visual Studio e lo strumento di raccolta dei log di .NET Framework, come descritto nei passaggi seguenti.  
  
    1.  Scaricare lo strumento di diagnostica dell'installazione da [http:\/\/aka.ms\/vscollect](http://aka.ms/vscollect).  
  
    2.  Eseguire il programma collect.exe da un prompt dei comandi con privilegi elevati.  
  
    3.  Dopo il completamento del programma collect.exe, recuperare il file vslogs.cab dalla directory Temp e caricarlo nel report dei problemi.  
  
##  <a name="enterprise"></a> Distribuzione di rete aziendale  
 Per informazioni su come distribuire [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in una rete, vedere [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md).  
  
##  <a name="afterInstalling"></a> Dopo l'installazione di Visual Studio  
 Dopo avere installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è consigliabile registrare la propria copia del prodotto.  
  
###  <a name="register"></a> Registrazione di Visual Studio  
  
##### Per registrare Visual Studio  
  
1.  Nella barra dei menu scegliere **Guida**, **Informazioni su**.  
  
     Nella finestra di dialogo **Informazioni su** è indicato il numero di identificazione del prodotto. Per registrare il prodotto sono necessarie le credenziali di account PID e Windows \(ad esempio un indirizzo di posta elettronica Hotmail o Outlook.com e una password\).  
  
2.  Nella barra dei menu scegliere **Guida**, **Registra prodotto**.  
  
###  <a name="helpContent"></a> Installazione del contenuto della Guida offline  
 Dopo aver installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile scaricare ulteriori contenuti della Guida in modo che siano disponibili offline.  
  
##### Per installare o disinstallare il contenuto della Guida  
  
1.  Nella barra dei menu di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], scegliere **?** quindi **Aggiungi e rimuovi contenuto della Guida**.  
  
2.  Nella scheda **Gestisci contenuti** di **Microsoft Help Viewer** selezionare l'origine di installazione per il contenuto della Guida.  
  
3.  Se si cerca una raccolta specifica della Guida, immettere il nome o una parola chiave nella casella di testo **Cerca**, quindi premere INVIO.  
  
4.  Accanto al nome della raccolta della Guida desiderata, scegliere il collegamento **Aggiungi** o **Rimuovi**.  
  
5.  Scegliere il pulsante **Aggiorna**.  
  
 Per altre informazioni sulla Guida offline, vedere [Microsoft Help Viewer 2.2](../ide/microsoft-help-viewer.md).  
  
###  <a name="repair"></a> Ripristino di Visual Studio  
  
##### Per ripristinare Visual Studio  
  
1.  Nella pagina **Programmi e funzionalità** del **Pannello di controllo** selezionare l'edizione del prodotto che si vuole ripristinare e fare clic su **Cambia**.  
  
2.  Nell'Installazione guidata scegliere **Ripristina**, scegliere **Avanti**, quindi seguire le istruzioni rimanenti.  
  
##### Per ripristinare Visual Studio in modalità invisibile all'utente o passiva \(ripristino dall'origine\)  
  
1.  Nel computer in cui è installato Visual Studio aprire il prompt dei comandi di Windows.  
  
2.  Immettere i seguenti parametri:  
  
     *DVDRoot* \\\<File di installazione\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/Repair  
  
###  <a name="optionalComponents"></a> Installazione degli elementi selezionabili  
  
##### Per installare gli elementi selezionabili  
  
1.  Nella pagina **Programmi e funzionalità** del **Pannello di controllo** selezionare l'edizione del prodotto a cui si vuole aggiungere uno o più componenti, quindi selezionare **Cambia**.  
  
2.  Nell'Installazione guidata scegliere **Modifica**, quindi selezionare i componenti da installare.  
  
3.  Scegliere **Avanti**, quindi seguire le istruzioni rimanenti.  
  
###  <a name="serviceReleases"></a> Verifica della disponibilità di Service Release e aggiornamenti del prodotto  
 Visual Studio non aggiorna automaticamente le estensioni quando si esegue l'aggiornamento da versioni precedenti, poiché non tutte le estensioni sono compatibili. È necessario reinstallare le estensioni da [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=178891) o dall'autore del software.  
  
##### Per cercare automaticamente versioni di servizio  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere **Ambiente**, quindi selezionare **Estensioni e aggiornamenti**. Assicurarsi che l'opzione **Controlla automaticamente la disponibilità di aggiornamenti** sia selezionata, quindi scegliere **OK**.  
  
##  <a name="uninstalling"></a> Disinstallazione di Visual Studio  
 Usare le procedure seguenti per disinstallare Visual Studio 2015.  
  
#### Per disinstallare Visual Studio  
  
1.  Nella pagina **Programmi e funzionalità** del **Pannello di controllo** selezionare l'edizione del prodotto che si vuole disinstallare e fare clic su **Cambia**.  
  
2.  Nell'Installazione guidata scegliere **Disinstalla**, scegliere **Sì**, quindi seguire le istruzioni rimanenti.  
  
#### Per disinstallare Visual Studio in modalità invisibile all'utente o passiva \(disinstallazione dall'origine\)  
  
1.  Nel computer in cui è installato Visual Studio aprire il prompt dei comandi di Windows.  
  
2.  Immettere i seguenti parametri:  
  
     *DVDRoot* \\\<Installation File\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/uninstall  
  
 Se non è possibile disinstallare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tramite l'utilità di disinstallazione, è possibile eseguire una disinstallazione manuale rimuovendo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e i componenti correlati. Per altre informazioni, vedere l'articolo della Microsoft Knowledge Base \(KB\) [Come disinstallare Visual Studio](https://support.microsoft.com/en-us/kb/2771441) o il post relativo alla [rimozione dei componenti di Visual Studio lasciati dopo una disinstallazione](http://blogs.msdn.com/b/heaths/archive/2015/07/17/removing-visual-studio-components-left-behind-after-an-uninstall.aspx) sul sito Web Microsoft Server & Tools Blogs.  
  
##  <a name="relatedTopics"></a> Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Installazione di versioni affiancate di Visual Studio](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md)|Vengono fornite informazioni sull'installazione di più versioni di Visual Studio nello stesso computer.|  
|[Libreria di immagini di Visual Studio](../designers/the-visual-studio-image-library.md)|Vengono fornite informazioni sull'installazione di immagini che possono essere usate nelle applicazioni di Visual Studio.|  
|[Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)|Fornisce informazioni sulle opzioni di distribuzione per Visual Studio.|  
|[Installazione di più versioni in lingue diverse di Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)|Fornisce informazioni sull'installazione di versioni in lingue diverse di Visual Studio.|  
|[Procedura: individuare il codice Product Key di Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md)|Fornisce informazioni sull'individuazione del codice Product Key per l'installazione di Visual Studio.|  
|[Introduzione](../ide/get-started-developing-with-visual-studio.md)|Vengono forniti collegamenti a documenti che agevolano l'uso efficace di Visual Studio.|  
  
## Vedere anche  
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3)