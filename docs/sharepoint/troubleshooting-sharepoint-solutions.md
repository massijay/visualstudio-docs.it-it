---
caps.handback.revision: 41
---
# Risoluzione dei problemi relativi alle soluzioni SharePoint
  I seguenti problemi o avvisi che potrebbero verificarsi quando si esegue il debug di soluzioni SharePoint utilizzando il  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]debugger.  Per ulteriori informazioni, vedere  [NIB: Debugging SharePoint 2007 Workflow Solutions](http://msdn.microsoft.com/it-it/3a5392f3-66f3-48be-956e-02de23fa6247).  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Token restrizioni nella Web part Visual in modalità sandbox  
 Visual web part nelle soluzioni in modalità sandbox non può elaborare un token standard, ad esempio $SPUrl, che supporta il runtime di SharePoint.  Di conseguenza, non si risolve l'URL e Impossibile visualizzare in anteprima il contenuto nella visualizzazione Progettazione nella finestra di progettazione di visual web part se si fa riferimento a essa direttamente in un elemento script, come nell'esempio riportato di seguito:  
  
```  
<script src=”<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Per aggirare questa limitazione e risolvere il token, fare riferimento a esso tramite valori letterali:  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## Restrizioni dei caratteri nei nomi di progetti ed elementi di progetto  
 I nomi dei progetti ed elementi di progetto possono contenere solo caratteri validi in un percorso di distribuzione in SharePoint 2010.  Altri caratteri non consentiti.  
  
### Messaggio di errore  
 Messaggio di errore "Caratteri non validi".  
  
### Risoluzione  
 Per i nomi dei progetti di SharePoint e gli elementi di progetto, utilizzare solo i seguenti caratteri:  
  
-   Caratteri ASCII alfanumerici  
  
-   Spazio  
  
-   Punto \(.\)  
  
-   Virgola \(\)  
  
-   Carattere di sottolineatura \(\_\)  
  
-   Trattino \(\-\)  
  
-   Barra rovesciata \(\\\)  
  
 Quando un progetto viene assemblato, una regola di convalida per verificare che la proprietà percorso di distribuzione per ogni file che si sta distribuendo contenga solo i caratteri validi.  
  
## Errori durante la creazione di campi personalizzati  
 In  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], i campi personalizzati definiti in XML.  Se un campo non è definito o viene fatto riferimento utilizzando un formato specifico, possono verificarsi errori.  
  
### Messaggio di errore  
 Messaggio di errore "Caratteri non validi" in fase di assemblaggio.  
  
### Risoluzione  
 L'ID per una definizione di campo deve essere un GUID racchiuso tra parentesi graffe, come illustrato nell'esempio riportato di seguito:  
  
```  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Come illustrato nell'esempio riportato di seguito, un riferimento di campo in un tipo di contenuto deve essere definito utilizzando il formato di elemento vuoto \(\< FieldRef \/ \>\), non tramite elementi iniziali o finali \(\< FieldRef \>\< \/ FieldRef \>\):  
  
```  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Se l'origine XML per il campo non è corretto, non è un file XML valido o presenta altri problemi, l'errore "Impossibile analizzare il file" si verifica.  
  
## Nuove definizioni di sito Non in lingua inglese non sono visualizzate nella pagina di creazione del sito dopo la distribuzione  
 Dopo aver creato e distribuire una definizione di sito utilizzando una versione non in lingua inglese di  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\(, ovvero una versione con impostazioni locali  [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]diverso da 1033\), il   **Personalizzazioni di SharePoint** scheda non viene visualizzata nella  **Selezione modello** casella e il nuovo modello di sito non viene visualizzato nel  **Nuovo sito di SharePoint** pagina.  
  
### Messaggio di errore  
 Nessuno.  
  
### Risoluzione  
 Questo problema si verifica a causa di un valore non corretto nel  **percorso** proprietà per il sito definizione file di configurazione webtemp, ad esempio webtemp\_SiteDefinitionProject1.  Nella  **percorso** proprietà per il file webtemp, posizionato sotto il  **Percorso di distribuzione**, modificare le impostazioni locali 1033  [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)].  Ad esempio, per utilizzare le impostazioni internazionali giapponesi modificare il valore su 1041.  Per ulteriori informazioni, vedere  [Locale IDs Assigned by Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561) sul sito Web MSDN.  
  
## Quando un progetto flusso di lavoro viene distribuito in un sistema pulito viene visualizzato un errore  
 Questo problema si verifica se si distribuisce un progetto flusso di lavoro in  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]in un sistema pulito.  Un sistema pulito è un computer con una nuova installazione di  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e di SharePoint ma non sono presenti progetti flusso di lavoro distribuiti.  
  
### Messaggio di errore  
 Impossibile trovare l'elenco di SharePoint: Storico del flusso di lavoro.  
  
### Risoluzione  
 Questo errore si verifica a causa di mancanza di un elenco di cronologia del flusso di lavoro.  Poiché l'ambiente di sviluppo è un sistema pulito, nessun flusso di lavoro viene distribuiti e l'elenco della cronologia del flusso di lavoro non esiste ancora.  Per risolvere questo problema, riaprire la procedura guidata del flusso di lavoro, che fa sì che l'elenco della cronologia del flusso di lavoro da creare.  
  
##### Immettere di nuovo la procedura guidata del flusso di lavoro  
  
1.  In  **Esplora**, scegliere il nodo del flusso di lavoro.  
  
2.  Nella  **proprietà** finestra, scegliere il pulsante con puntini di sospensione \(...\) in qualsiasi proprietà che dispone di un pulsante.  
  
## Utente necessario aggiornare la pagina dell'applicazione nel Browser durante il debug per visualizzare l'immagine aggiornata  
 Se si esegue il debug di una soluzione SharePoint che contiene una pagina dell'applicazione con un controllo che visualizza un'immagine, ad esempio un  [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)]controllo immagine, è necessario aggiornare la pagina nel browser per visualizzare le modifiche apportate all'immagine.  
  
## Errore: Il percorso del sito non è valido  
 Questo problema può verificarsi se  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]non è installato.  Potrebbe verificarsi anche se non è amministratore accedere al sito Web di SharePoint specificato nel  **Personalizzazione guidata SharePoint**.  
  
### Messaggio di errore  
  
-   Percorso del sito di SharePoint non è valido.  
  
### Risoluzione  
  
-   Installare  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Assicurarsi di avere accesso come amministratore al sito Web di SharePoint.  Per ulteriori informazioni, vedere la  [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)]Online l'articolo   [concedere l'accesso al sito portale](http://go.microsoft.com/fwlink/?LinkId=98310).  
  
## Evento di eliminazione del sito Web non presente nel progetto ricevitore di eventi  
 Quando si crea un progetto ricevitore di eventi e si selezionano determinati eventi di Web come "un sito venga eliminato" l'evento si verifica mai.  
  
### Messaggio di errore  
 Nessuno.  
  
### Risoluzione  
 Questo problema si verifica perché l'ambito della funzionalità deve essere "Sito" per gestire gli eventi a livello di sito, ma il valore predefinito ambito della funzionalità per i progetti del ricevitore di eventi è "Web".  Gli eventi Web interessati sono:  
  
-   Un sito viene eliminato \(WebDeleting\)  
  
-   È stato eliminato un sito \(WebDeleted\)  
  
-   Un sito viene spostato \(WebMoving\)  
  
-   È stato spostato un sito \(WebMoved\)  
  
 Per risolvere il problema, modificare l'ambito della funzionalità del ricevitore di eventi, come segue.  
  
##### Per modificare l'ambito della funzionalità del ricevitore di eventi  
  
1.  In  **Esplora**, aprire file con estensione feature del ricevitore di eventi il  **Di progettazione della funzionalità** di doppio clic sul file o aprire il menu di scelta rapida e quindi scegliere  **aprire**.  
  
2.  Fare clic sulla freccia accanto a  **ambito**, quindi scegliere  **sito** nell'elenco visualizzato.  
  
## Dopo avere modificato il nome di un identificatore in un progetto modello di integrazione applicativa dei dati viene visualizzato un errore di distribuzione  
 Questo problema si verifica se si modifica il nome dell'identificatore di un'entità in un modello di integrazione applicativa dei dati \(BDC\) e quindi si tenta di distribuire la soluzione.  
  
### Messaggi di errore  
  
-   \<*nome modello*\> ha i seguenti errori di attivazione del tipo di contenuto esterno...  
  
-   IMetadataObject con nome ' \<*nome modello*\>' ha un valore nel campo 'nome' che sono duplicati...  
  
### Risoluzione  
 Per risolvere questo problema, eliminare manualmente il modello e quindi distribuire nuovamente la soluzione.  È possibile eliminare il modello utilizzando uno dei seguenti strumenti:  
  
-   Amministrazione centrale SharePoint 2010.  Per ulteriori informazioni, vedere  [Gestione del modello di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkID=181472) sul sito Web Microsoft TechNet.  
  
-   Windows PowerShell.  È possibile eliminare il modello digitando il seguente comando al prompt dei comandi: **Remove\-SPBusinessDataCatalogModel**.  Per ulteriori informazioni, vedere  [cmdlet generali \(SharePoint Server 2010\)](http://go.microsoft.com/fwlink/?LinkID=182375) sul sito Web Microsoft TechNet.  
  
## Viene visualizzato un errore quando si tenta di visualizzare una Web Part visiva in SharePoint  
 Questo problema si verifica quando il  **percorso** proprietà del controllo utente non inizia con la stringa "CONTROLTEMPLATES\\".  
  
### Messaggi di errore  
  
-   Il file ' \/\_CONTROLTEMPLATES\/*\< nome progetto \>*\/*\< nome Web Part \>*\/*\< nome del controllo utente \>*ascx ' non esiste.  
  
-   Errore del server in '\/' Applicazione.  
  
### Risoluzione  
  
##### Per risolvere il problema  
  
1.  In  **Esplora**, scegliere il file del controllo utente, con estensione del nome file è ascx.  
  
2.  Sulla barra dei menu, scegliere  **visualizzazione**,  **Finestra Proprietà**.  
  
3.  Nella  **proprietà** finestra, espandere la  **Percorso di distribuzione** nodo.  
  
4.  Assicurarsi che il valore della  **percorso** proprietà inizia con la stringa "CONTROLTEMPLATES\\".  
  
## Viene visualizzato un errore durante l'esecuzione di un flusso di lavoro riutilizzabile importato contenente un campo del modulo attività  
 Questo problema si verifica se si importa un flusso di lavoro che contiene un modulo di attività che dispone di un campo e quindi esecuzione il nuovo flusso di lavoro del sistema stesso da cui è stato importato.  
  
### Messaggio di errore  
 Si è verificato un errore in fase di distribuzione 'Attiva funzionalità': Il campo con Id *Guid*\] definito nella funzionalità \[*Guid*\] è stato trovato nella raccolta siti corrente o in un sito secondario.  
  
### Risoluzione  
 Questo errore è il risultato di conflitti di ID di campo che si verificano perché il flusso di lavoro riutilizzabile Importa progetto nel  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]non modifica l'ID di campo del modulo attività.  Se si distribuisce un flusso di lavoro importato nello stesso server che contiene il flusso di lavoro originale, si verificano conflitti di ID di campo.  
  
 Per risolvere questo problema, utilizzare la funzione Trova e Sostituisci per modificare il valore dell'attributo ID del campo in tutti i file di flusso di lavoro importato.  
  
## Errore viene visualizzato quando un importata rinominata viene eseguita l'istanza di elenco  
 Questo problema si verifica se si rinomina un'istanza di elenco importata e quindi eseguirlo  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### Messaggio di errore  
 Errore di compilazione: Si è verificato un errore in fase di distribuzione 'Attiva funzionalità': Il file Template\\Features\\ *import project* *feature* *name*\] \\Files\\Lists\\ \[*old* *list name*\] \\Schema.xml non esiste.  
  
### Risoluzione  
 Quando si importa un'istanza di elenco, un attributo denominato CustomSchema viene aggiunto al file Elements. XML dell'istanza di elenco.  Elements. XML include il percorso di un file schema. XML personalizzato per l'istanza di elenco.  Quando si rinomina l'istanza di elenco in  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], viene modificato il percorso di distribuzione per il file schema. XML personalizzato, ma non viene aggiornato il valore del percorso dell'attributo CustomSchema.  Di conseguenza, l'istanza di elenco Impossibile trovare il file schema XML nel percorso precedente specificato dall'attributo CustomSchema quando la funzionalità è attivata.  
  
 Per risolvere questo problema, aggiornare il percorso di distribuzione del file schema. XML nell'attributo CustomSchema.  
  
## Sessione terminata da IIS di debug di SharePoint  
 Questo problema si verifica se si imposta un punto di interruzione un  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]soluzione SharePoint, selezionare il tasto F5 per eseguirla e quindi rimanere in un punto di interruzione più di 90 secondi.  
  
### Messaggio di errore  
 Il processo del server Web in fase di debug è stato terminato da Internet Information Services \(IIS\).  Per evitare questo problema, configurare le impostazioni ping del Pool di applicazioni in IIS.  Vedere Guida in linea per ulteriori dettagli.  
  
### Risoluzione  
 Per impostazione predefinita, il pool di applicazioni IIS attende 90 secondi per un'applicazione di rispondere prima della chiusura dell'applicazione.  Questo processo è noto come il "ping" l'applicazione.  Per risolvere questo problema, è possibile aumentare il tempo di attesa o disabilitare completamente il ping di applicazione.  
  
##### Per accedere alle impostazioni del pool di applicazioni IIS  
  
1.  Aprire Gestione IIS.  
  
2.  Nella  **connessioni** riquadro, espandere il nodo server di SharePoint e quindi scegliere il  **Pool di applicazioni** nodo.  
  
3.  Nella  **Pool di applicazioni** , selezionare il pool di applicazioni di SharePoint \(in genere "SharePoint \- 80"\), quindi nel  **Azioni** riquadro, scegliere il  **Impostazioni avanzate** collegamento.  
  
4.  Per aumentare il tempo di attesa prima del timeout IIS, è necessario modificare il valore di  **Tempo di risposta massimo di Ping \(secondi\)** su un valore maggiore di 90 secondi.  
  
5.  Per disattivare il ping di IIS, impostare  **Ping abilitato** a  **False**.  
  
## Ritrazione automatica lascia istanza di elenco orfana in SharePoint  
 Questo problema si verifica se si adotta la seguente procedura.  
  
1.  Creare una definizione di elenco con un'istanza di elenco in  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere il tasto F5 per eseguire la soluzione.  
  
3.  Interrompere il debug o chiusura del sito di SharePoint.  
  
4.  Riaprire il sito di SharePoint e aprire l'istanza di elenco.  
  
### Messaggio di errore  
 Errore del server in '\/' Applicazione.  
  
### Risoluzione  
 In questo caso perché dopo la chiusura di una sessione di debug di una soluzione SharePoint, la ritrazione automatica funzionalità ritrae la soluzione.  Il ritiro Elimina la definizione di elenco da SharePoint, ma l'istanza dell'elenco.  La definizione di elenco sottostante è obbligatoria per l'istanza di elenco.  
  
 Per risolvere questo problema, distribuire la soluzione, sulla barra dei menu, scegliere  **Build**,  **distribuzione**. \(Non eseguire il debug della soluzione scegliendo il tasto F5.\) Quindi, eliminare l'istanza di elenco in SharePoint.  
  
## Soluzione SharePoint originale viene sostituita da una versione esportata  
 Se si esporta una soluzione SharePoint, importare la soluzione in  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e quindi distribuire la soluzione al sito stesso da cui è stato esportato, la soluzione SharePoint originale viene sostituita.  Questo problema si verifica se si distribuisce la soluzione a un server che non è la soluzione originale in esso attivata.  
  
### Messaggio di errore  
 Nessuno.  
  
### Risoluzione  
 Per evitare di sovrascrivere una soluzione sul sito da cui è stato esportato, modificare i GUID di SolutionID e gli ID di funzionalità di tutte le funzionalità importate nel  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]project.  
  
## Viene visualizzato un errore all'avvio del debug  
 Quando si avvia il debug di una soluzione SharePoint in Visual Studio, un errore indica che Visual Studio Impossibile caricare il file Web. config perché la chiave specificata non era nel dizionario.  
  
### Messaggio di errore  
 Impossibile caricare il file di configurazione Web. config.  Controllare il file per tutti gli elementi XML non valido e riprovare.  Si è verificato il seguente errore: La chiave specificata non era presente nel dizionario.  
  
### Risoluzione  
 Per risolvere il problema, assicurarsi che il valore della proprietà URL del sito del progetto SharePoint in Visual Studio corrisponde all'URL assegnato all'area predefinita per il mapping di accesso alternativo dell'applicazione web.  È possibile correggere l'errore utilizzando un'altra area, ad esempio Intranet, per l'URL.  Il sito URL per il progetto e l'URL nella zona predefinita devono corrispondere.  Per accedere a mapping di accesso alternativo, aprire l'utilità di amministrazione centrale SharePoint 2010, scegliere il  **Application Management** collegamento, quindi in  **Le applicazioni Web**, scegliere il  **Configura mapping di accesso alternativo** collegamento.  Per ulteriori informazioni, vedere  [creare aree per le applicazioni Web](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## Vedere anche  
 [Risoluzione dei problemi relativi alla creazione di pacchetti e alla distribuzione di SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)  
  
  