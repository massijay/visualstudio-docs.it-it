---
title: "Utilizzo di Web browser diversi con i test dell&#39;interfaccia utente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "mlearned"
manager: "douge"
---
# Utilizzo di Web browser diversi con i test dell&#39;interfaccia utente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I test codificati dell'interfaccia utente possono automatizzare il test delle applicazioni Web registrando i test tramite Internet Explorer.  È quindi possibile personalizzare il test e riprodurlo usando Internet Explorer o un altro tipo di browser per queste applicazioni Web.  
  
 **Requisiti**  
  
-   Visual Studio Enterprise  
  
-   Sistemi operativi:  
  
    -   Microsoft Windows 7  
  
    -   Microsoft Windows 8  
  
    -   Microsoft Windows Server 2008 R2 SP1  
  
-   Versioni del Web browser:  
  
    -   Windows Internet Explorer 9  
  
    -   Windows Internet Explorer 10  
  
    -   Per le versioni supportate di Mozilla Firefox e Google Chrome, andare [qui](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)  
  
-   Installare i [componenti Selenium per i test codificati dell'interfaccia utente tra browser](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 **Quali sono i Web browser supportati?**  
  
-   [Aggiungere il codice personalizzato per le funzionalità di controllo](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) ad esempio waiter di riproduzione, ricerca e proprietà.  
  
-   Popup e finestre di dialogo  
  
-   [Eseguire JavaScript di base senza tipo restituito](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
-   Resilienza di ricerca \(tramite la corrispondenza intelligente\) e [miglioramenti delle prestazioni](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## Perché usare i test codificati dell'interfaccia utente per più tipi di Web browser?  
 Testando l'applicazione Web con vari tipi di Web browser si emula meglio l'esperienza dell'interfaccia utente degli utenti che possono eseguire diversi browser.  Ad esempio, l'applicazione potrebbe includere un controllo o un codice in Internet Explorer non compatibile con altri Web browser.  L'esecuzione dei test codificati dell'interfaccia utente in altri browser consente di individuare e risolvere i problemi prima dell'impatto sui clienti.  
  
## Come registrare e riprodurre i test codificati dell'interfaccia utente nelle applicazioni web usando i Web browser supportati  
 **Registrazione:** è necessario usare il Generatore di test codificati dell'interfaccia utente per registrare il test di un'applicazione Web usando Internet Explorer.  È possibile aggiungere la convalida e il codice personalizzato per i controlli testati usando un set predefinito di proprietà come generalmente accade per i test codificati dell'interfaccia utente.  Per altre informazioni, vedere [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md).  
  
> [!NOTE]
>  Non è possibile registrare i test codificati dell'interfaccia utente usando i browser Mozilla Firefox o Google Chrome.  
  
 **Riproduzione con Internet Explorer:** quando non è specificato alcun browser in modo esplicito, i test vengono eseguiti in Internet Explorer per impostazione predefinita.  È possibile dichiarare in modo esplicito il browser da usare impostando la proprietà **BrowserWindow.CurrentBrowser** nel codice del test.  Per Internet Explorer, questa proprietà deve essere impostata su **IE** o **Internet Explorer**.  
  
 **Riproduzione con Web browser diversi da Internet Explorer:** per riprodurre in Web browser diversi da Internet Explorer, modificare le proprietà BrowserWindow.CurrentBrowser nel codice del test su **Firefox** o **Chrome**.  
  
 Per riprodurre i test su Web browser diversi da IE, è necessario installare i **Selenium components for Coded UI Cross Browser Testing**.  
  
#### Installazione di Selenium Components  
  
1.  Nel menu **Strumenti** scegliere **Estensioni e aggiornamenti**.  
  
2.  Nella finestra di dialogo dell'estensione e degli aggiornamenti, individuare i `componenti Selenium per il test tra più browser`.  
  
3.  Evidenziare l'estensione e scegliere **Download**.  
  
    > [!TIP]
    >  È anche possibile scaricare i componenti Selenium per i test codificati dell'interfaccia utente tra browser [qui](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 Per ulteriori informazioni sulla creazione e l'utilizzo di test codificati dell'interfaccia utente, vedere [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
### Abilita debug  
 Per abilitare il debug dell'applicazione Web è necessario completare le opzioni di configurazione seguenti:  
  
1.  Abilitare Just My Code:  
  
    1.  Dal menu **Strumenti** scegliere **Opzioni**, quindi **Debug**.  
  
    2.  Selezionare **Abilita Just My Code** .  
  
2.  Disabilitare le eccezioni CLR:  
  
    1.  Scegliere **Eccezioni** dal menu **Debug**.  
  
    2.  Per **Eccezioni Common Language Runtime**, deselezionare **Non gestita dall'utente**.  
  
##  <a name="generate"></a> *L'opzione per modificare BrowserWindow.CurrentBrowser non è presente nel test codificato dell'interfaccia utente.*  
 È possibile che si usi una versione di [!INCLUDE[vs2011_first](../test/includes/vs2011_first_md.md)] che non supporta i test codificati dell'interfaccia utente tramite Web browser differenti.  Per usare questi test codificati dell'interfaccia utente, è necessario usare Visual Studio Enterprise.  
  
 *Altre informazioni*  
 **Note**  
  
-   ![Prerequisito](../test/media/prereq.png "Prereq") Il Web browser Apple Safari non è supportato.  
  
-   ![Prerequisito](../test/media/prereq.png "Prereq") L'azione di avvio del Web browser deve far parte del test codificato dell'interfaccia utente.  
  
     Se il Web browser è già aperto e si desidera eseguire i passaggi, la riproduzione avrà esito negativo a meno che non si usi Internet Explorer.  Pertanto è consigliabile includere l'avvio del Web browser come parte dei test codificati dell'interfaccia utente.  
  
-   ![Prerequisito](../test/media/prereq.png "Prereq") L'automazione di azioni dell'interfaccia utente specifiche del browser quali l'ingrandimento, la riduzione al minimo e il ripristino non è supportata.  
  
 **Suggerimenti**  
  
-   ![Suggerimento](../test/media/tip.png "Tip") È possibile configurare l'output in modo da includere le schermate nei log codificati dell'interfaccia utente.  A tale scopo, è necessario impostare alcune impostazioni di configurazione nel file QTAgent32.exe.config.  Per impostazione predefinita, questo file è installato nel percorso seguente:  
  
     **C:\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\Common7\\IDE**  
  
     Impostare i seguenti valori:  
  
    -   `EqtTraceLevel` nella sezione `system.diagnostics`.  
  
    -   `<add name="EqtTraceLevel" value="4" />`  
  
         Impostando 3 o un valore superiore verrà catturata una schermata per ogni azione.  Quando il valore è impostato su 1 o 2, le schermate vengono catturate solo per azioni che causano errore.  
  
     Per altre informazioni, vedere [Analisi dei test codificati dell'interfaccia utente utilizzando i log dei test codificati dell'interfaccia utente](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
## Risorse esterne  
  
### Video  
 [Registrazione in IE e riproduzione ovunque](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)  
  
 [Creazione di test in più browser con il generatore di test codificati dell'interfaccia utente](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)  
  
 [Creazione di test tra più browser usando la normale codifica manuale senza mappa dell'interfaccia utente](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)  
  
 [Esecuzione di test tra più browser in sequenza in più browser](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)  
  
 [Risoluzione degli errori dei test tra più browser](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)  
  
### Istruzioni utili  
 [Test per la distribuzione continua con Visual Studio 2012 – Capitolo 2: Unit Testing: Test interni](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Test per la distribuzione continua con Visual Studio 2012 – Capitolo 5: automazione dei test di sistema](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### Domande frequenti  
 [Domande frequenti sui test codificati dell'interfaccia utente \- 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Domande frequenti sui test codificati dell'interfaccia utente \-2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### Forum  
 [Test di automazione dell'interfaccia utente di Visual Studio \(include test codificati dell'interfaccia utente\)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## Vedere anche  
 [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)   
 [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Analisi dei test codificati dell'interfaccia utente utilizzando i log dei test codificati dell'interfaccia utente](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)