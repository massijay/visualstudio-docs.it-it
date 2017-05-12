---
caps.handback.revision: 24
---
# Risoluzione dei problemi relativi alla creazione di pacchetti e alla distribuzione di SharePoint
  In questo argomento vengono analizzati vari problemi che possono verificarsi durante la creazione di pacchetti e la distribuzione di soluzioni SharePoint.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Abilitazione del debug avanzato  
 Per effettuare una diagnosi dei problemi relativi a Visual Studio, SharePoint e ad altri livelli, è possibile utilizzare la chiave del Registro di sistema EnableDiagnostics per visualizzare la traccia dello stack.  Per ulteriori informazioni, vedere [Debug di soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## Aggiunta dell'output del progetto al pacchetto della soluzione  
 È possibile aggiungere l'output del progetto a un pacchetto mediante Progettazione pacchetti.  Quando tuttavia si aggiunge l'output del progetto, verificare che la piattaforma del progetto corrisponda alla piattaforma della soluzione SharePoint.  È consigliabile utilizzare la piattaforma di destinazione **Qualsiasi CPU** per gli assembly che si desidera distribuire in un server SharePoint.  Per ulteriori informazioni, vedere [Compilazione &#40;pagina&#41;, Creazione progetti &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) e [Finestra di dialogo Impostazioni del compilatore avanzate &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## Avvisi ed errori di convalida  
 Gli strumenti di sviluppo di SharePoint in Visual Studio consentono di eseguire passaggi di convalida per verificare che il pacchetto della soluzione venga creato correttamente.  È inoltre possibile creare passaggi di convalida personalizzati per le funzionalità e i pacchetti.  Per ulteriori informazioni, vedere [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## Risoluzione dei conflitti di distribuzione  
 Quando si distribuisce una soluzione SharePoint, possono verificarsi conflitti se un elemento sul server ha lo stesso nome, URL o ID di un elemento presente nel pacchetto della soluzione.  È possibile modificare la proprietà **Risoluzione conflitti di distribuzione** per risolvere, segnalare o ignorare i conflitti relativi a moduli, Web part, istanze di elenco e tipi di contenuto.  
  
 Nella tabella seguente sono elencate le impostazioni per la proprietà **Risoluzione conflitti di distribuzione**.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|Automatic|I conflitti vengono rilevati e risolti automaticamente.|  
|Prompt|I conflitti vengono rilevati e segnalati allo sviluppatore prima di essere risolti.|  
|None|I conflitti non vengono rilevati.|  
  
## Differenze rispetto alla distribuzione tramite il tasto F5  
 Quando si utilizza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per distribuire il progetto SharePoint nel server SharePoint locale per il test e l'esecuzione del debug, in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vengono eseguiti alcuni passaggi aggiuntivi.  
  
1.  Reimpostazione di Internet Information Service \(IIS\) durante il passaggio di distribuzione.  
  
2.  Associazione automatica dei flussi di lavoro.  
  
3.  Impostazione dell'ordine di attivazione delle funzionalità in base alla gerarchia di Progettazione pacchetti.  
  
 È possibile aggiungere passaggi di distribuzione personalizzati per modificare ulteriormente il comportamento del tasto F5.  Per ulteriori informazioni, vedere [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## Ritardo della visualizzazione della pagina di SharePoint durante la distribuzione di una Web part visiva  
 La visualizzazione della pagina di SharePoint richiede molto tempo quando si distribuisce una Web part visiva nella cartella Bin di [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] o [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)].  Se si modificano i file di una directory di livello superiore di [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], ad esempio la directory Bin, viene ricompilata l'intera applicazione Web.  Questo può determinare fino a 25 secondi di ritardo nel rendering della pagina di SharePoint.  
  
### Messaggio di errore  
 Nessuno.  
  
### Risoluzione  
 Per risolvere il problema, effettuare i passaggi seguenti:  
  
1.  Installare l'aggiornamento QFE KB967535 come descritto nell'articolo del supporto tecnico Microsoft [FIX: è disponibile un hotfix per correggere due problemi in ASP.NET in IIS 7.0 per Windows Vista e Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).  
  
2.  Aggiungere la riga di codice seguente al file Web.config:  
  
    ```  
    <compilation batch="false" optimizeCompilations="true">  
    ```  
  
## Distribuzione del progetto SharePoint non riuscita con generazione dell'errore "Impossibile estrarre il file cab nella soluzione"  
 Se il nome di un qualsiasi elemento di progetto SharePoint contiene parentesi, la distribuzione della soluzione non riesce generando un errore.  
  
### Messaggio di errore  
 Si è verificato un errore nel passaggio di distribuzione 'Aggiungi Soluzione': Impossibile estrarre il file cab nella soluzione.  
  
### Risoluzione  
 Per risolvere il problema, rimuovere le parentesi nei nomi degli elementi di progetto SharePoint.  
  
## Errore visualizzato durante la distribuzione di una web part visiva in un sito in un'applicazione Web diversa  
 La prima volta che viene distribuita una Web part visiva a un sito su un'applicazione Web diversa da quella sulla quale è correntemente distribuita \(modificando la proprietà SiteUrl della Web part visiva\), si ottiene un errore.  
  
### Messaggio di errore  
 Si è verificato un errore nel passaggio di distribuzione 'Aggiungi Soluzione': Una funzionalità con ID \[\#\] è già stata installata in questa farm.  Utilizzare l'attributo force per installare nuovamente in modo esplicito la funzionalità.  
  
### Risoluzione  
 Questo errore si verifica a causa della modalità con cui le funzionalità della Web part visiva vengono ritratte in SharePoint.  Per distribuire correttamente la Web part visiva, distribuire di nuovo la soluzione premendo F5.  
  
## Avviso visualizzato durante la distribuzione di controlli utente annidati  
 Questo avviso viene visualizzato quando si distribuisce una soluzione SharePoint in cui sono annidati controlli utente, quale una web part visiva contenente un controllo utente o un controllo utente contenente una web part visiva o un altro controllo utente.  L'avviso viene generato se si aggiunge un controllo a una finestra di progettazione trascinandolo dalla casella degli strumenti o utilizzando l'istruzione @Register nella visualizzazione Origine.  
  
### Messaggio di errore  
 Avviso 1: L'elemento '*Control Name*\]' non è un elemento noto.  Il problema potrebbe essere dovuto a un errore di compilazione del sito Web oppure il file web.config risulta mancante.  
  
### Risoluzione  
 Se il sistema del progetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non riconosce un controllo utente annidato, non può fornire IntelliSense e genera l'avviso.  Il sistema del progetto non riconosce un controllo utente annidato se il progetto non viene compilato e la finestra di progettazione non viene chiusa né riaperta oppure se l'opzione di ritrazione automatica è abilitata, causando la ritrazione del controllo utente dall'hive SharePoint dopo il debug.  
  
 Per rimuovere questo avviso, compilare il progetto, quindi chiudere e riaprire la finestra di progettazione oppure disabilitare l'opzione di ritrazione automatica per il progetto.  A tale scopo, deselezionare la casella di controllo **Ritrazione automatica dopo il debug** nella scheda **SharePoint** della finestra di dialogo delle proprietà del progetto.  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  