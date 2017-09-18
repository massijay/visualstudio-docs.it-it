---
title: "Salvataggio dei dati nei dataset | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], salvataggio"
  - "convalida dei dati, dataset"
  - "dataset [Visual Basic], informazioni sui dataset"
  - "dataset [Visual Basic], vincoli"
  - "dataset [Visual Basic], unione"
  - "dataset [Visual Basic], convalida dei dati"
  - "versione righe"
  - "salvataggio di dati, informazioni sul salvataggio di dati"
  - "TableAdapters"
  - "aggiornamenti, vincoli in dataset"
  - "aggiornamento di dataset, vincoli"
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 27
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Salvataggio dei dati nei dataset
Il salvataggio dei dati è il processo mediante il quale i dati modificati di un'applicazione vengono salvati in modo permanente nell'archivio dati originale, in genere un database relazionale come SQL Server.  
  
 Poiché un dataset è in pratica una cache, cioè una copia in memoria, di dati, la scrittura delle informazioni nell'origine dati iniziale e la modifica dei dati nel dataset costituiscono processi distinti.  Per inviare i dati aggiornati nei dataset al database, è possibile chiamare uno dei metodi `Update` di un oggetto TableAdapter oppure chiamare uno dei metodi DBDirect di TableAdapter.  
  
 Per ulteriori informazioni sull'invio delle modifiche presenti in un dataset al database, vedere [Procedura: aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) e [Procedura: salvare le modifiche di un dataset in un database](../data-tools/how-to-save-dataset-changes-to-a-database.md).  
  
 In Visual Studio è disponibile un componente `TableAdapterManager` che semplifica la procedura di salvataggio dei dati nelle tabelle correlate,  garantendo che i salvataggi vengano eseguiti nell'ordine corretto in base ai vincoli di chiave esterna definiti nel database.  Per ulteriori informazioni, vedere [Cenni preliminari sull'aggiornamento gerarchico](../Topic/Hierarchical%20Update%20Overview.md).  
  
 Per informazioni sulla modifica di dati nel dataset, vedere [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md).  
  
## Aggiornamenti in due fasi  
 L'aggiornamento di un'origine dati mediante un dataset è un processo in due fasi:  la consiste nell'aggiornare il dataset con nuove informazioni, ovvero nuovi record, record modificati o record eliminati.  Se l'applicazione riguarda esclusivamente il dataset, cioè se, ad esempio, dopo aver aggiornato il dataset, lo si invia a un'altra applicazione, che ne svolgerà un'ulteriore elaborazione, l'aggiornamento può considerarsi terminato.  
  
> [!NOTE]
>  Grazie all'architettura di associazione dei dati dei Windows Form è possibile inviare le modifiche da controlli associati a dati al dataset e pertanto non è più necessario aggiornare esplicitamente il dataset con il proprio codice.  Per ulteriori informazioni, vedere [Associazione ai dati di Windows Form](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
 Se si sta aggiornando un'origine dati, quale un database, il secondo passaggio consiste nell'inviare le modifiche dal dataset all'origine dati iniziale.  In altre parole, tramite il processo di aggiornamento del dataset le modifiche non vengono scritte anche in un'origine dati sottostante, ma è necessario effettuare questo secondo passaggio in modo esplicito.  In genere, tale operazione viene svolta chiamando il metodo Update dello stesso TableAdapter o adattatore dati utilizzato per compilare il dataset. È anche possibile, tuttavia, utilizzare altri adattatori, ad esempio per spostare i dati da un'origine dati all'altra o per aggiornare più origini dati.  
  
 ![Aggiornamenti di Dataset di Visual Basic](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
Processo di aggiornamento in due fasi e ruolo di DataRowVersion in un aggiornamento eseguito correttamente  
  
 Dal punto di vista strutturale, i dati di un dataset sono disponibili come set di raccolte.  Nei dataset sono contenute raccolte di tabelle,  che, a loro volta, contengono raccolte di righe.  Le tabelle vengono esposte come una raccolta dell'oggetto <xref:System.Data.DataSet> e i record sono disponibili nella raccolta <xref:System.Data.DataTable.Rows%2A> degli oggetti <xref:System.Data.DataTable>.  È possibile apportare delle modifiche ai dati di un dataset semplicemente modificando queste raccolte mediante i relativi metodi base. Tuttavia, se si desidera aggiornare un'origine dati sottostante, sarà necessario utilizzare i metodi progettati specificamente per la modifica del dataset.  
  
 Per rimuovere un record da una tabella dati, ad esempio, è possibile chiamare il metodo [RemoveAt](https://msdn.microsoft.com/en-us/library/system.data.datarowcollection.removeat.aspx) della raccolta <xref:System.Data.DataTable.Rows%2A> della tabella, che elimina fisicamente il record dal dataset.  Se si sta utilizzando il dataset solo come un archivio strutturato per i dati e non si ha intenzione di trasmettere le informazioni di modifica a un'altra applicazione, questo tipo di modifica delle raccolte è un metodo accettabile per l'aggiornamento di un dataset.  
  
 Tuttavia, per inviare le modifiche a un'origine dati o a un'altra applicazione, è necessario conservare le informazioni relative alla modifica, ovvero i metadati, per ciascun aggiornamento.  In seguito, una volta inviate le modifiche all'origine dati o all'applicazione, il processo disporrà delle informazioni necessarie per l'individuazione e l'aggiornamento dei record appropriati.  Se ad esempio si elimina un record dal dataset, sarà necessario conservarne comunque le informazioni nel dataset.  In questo modo, quando viene richiamato il metodo `DeleteCommand` del TableAdapter, le informazioni della cronologia saranno sufficienti a individuare il record originale nell'origine dati per consentirne l'eliminazione.  Per ulteriori informazioni, vedere più avanti la sezione "Gestione delle informazioni sulle modifiche" e  
  
## Unione di dataset  
 È possibile aggiornare il contenuto di un dataset *unendo*, cioè copiando il contenuto di un dataset, definito dataset *di origine*, nel dataset chiamante, definito dataset *di destinazione*.  Quando si uniscono i dataset, al dataset di destinazione vengono aggiunti i nuovi record del dataset di origine.  Inoltre, le colonne supplementari del dataset di origine vengono aggiunte al dataset di destinazione.  L'unione dei dataset è particolarmente utile quando si dispone di un dataset locale e si ottiene un secondo dataset da un'altra applicazione o da un componente quale un servizio Web XML.  È utile inoltre quando si desidera integrare dati da più dataset.  
  
 Quando si uniscono i dataset, è anche possibile passare un argomento Boolean facoltativo \(`preserveChanges`\) che indichi al metodo <xref:System.Data.DataSet.Merge%2A> se conservare o meno le modifiche esistenti nel dataset di destinazione.  Poiché i dataset mantengono più versioni dei record, è importante tenere presente che l'unione interessa più versioni dei record.  Nella tabella seguente è riportato un record presente in due dataset che verranno uniti:  
  
|DataRowVersion|Dataset di destinazione|Dataset di origine|  
|--------------------|-----------------------------|------------------------|  
|Originale|James Wilson|James C.  Wilson|  
|Corrente|Jim Wilson|James C.  Wilson|  
  
 La chiamata al metodo <xref:System.Data.DataSet.Merge%2A> presente nella tabella sopra riportata con `preserveChanges=false targetDataset.Merge(sourceDataset)` determina la situazione che segue:  
  
|DataRowVersion|Dataset di destinazione|Dataset di origine|  
|--------------------|-----------------------------|------------------------|  
|Originale|James C.  Wilson|James C.  Wilson|  
|Corrente|James C.  Wilson|James C.  Wilson|  
  
 La chiamata al metodo <xref:System.Data.DataSet.Merge%2A> con `preserveChanges = true targetDataset.Merge(sourceDataset, true)` determina la situazione che segue:  
  
|DataRowVersion|Dataset di destinazione|Dataset di origine|  
|--------------------|-----------------------------|------------------------|  
|Originale|James C.  Wilson|James C.  Wilson|  
|Corrente|Jim Wilson|James C.  Wilson|  
  
> [!CAUTION]
>  Nello scenario `preserveChanges = true`, se in un record del dataset di destinazione viene chiamato il metodo <xref:System.Data.DataSet.RejectChanges%2A>, verranno ripristinati i dati originali del dataset *di origine*,  il che significa che, se si tenta di aggiornare l'origine dati iniziale con il dataset di destinazione, potrebbe non essere possibile trovare la riga originale da aggiornare.  È tuttavia possibile evitare che si verifichi una violazione di concorrenza compilando un altro dataset con i record aggiornati dall'origine dati e quindi eseguendo un'unione. Una violazione di concorrenza si verifica quando un altro utente modifica un record nell'origine dati dopo la compilazione del dataset.  
  
## Vincoli di aggiornamento  
 Per apportare delle modifiche a una riga di dati esistente, si aggiungono o si aggiornano i dati nelle singole colonne.  Se il dataset contiene dei vincoli, quali chiavi esterne o vincoli non nullable, è possibile che durante l'aggiornamento di un record, dopo aver terminato di aggiornare una colonna, ma prima di passare alla successiva, il record si trovi temporaneamente in stato di errore.  
  
 Per impedire violazioni anomale dei vincoli, è possibile sospendere temporaneamente i vincoli di aggiornamento,  ottenendo un duplice effetto:  
  
-   Si impedisce che venga generato un errore quando una colonna viene aggiornata prima di passare a un'altra.  
  
-   Si sospende la generazione di determinati eventi di aggiornamento, che vengono spesso utilizzati per la convalida.  
  
 Una volta completato un aggiornamento, è possibile riabilitare il controllo dei vincoli. In questo modo verranno riabilitati e generati anche gli eventi di aggiornamento.  
  
> [!NOTE]
>  Tramite l'architettura di associazione dati incorporata nella griglia dei dati in Windows Form, il controllo dei vincoli viene sospeso finché lo stato attivo non passa all'esterno di una riga. Di conseguenza, non è più necessario chiamare esplicitamente i metodi <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> o <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Quando viene richiamato il metodo <xref:System.Data.DataSet.Merge%2A> in un dataset, i vincoli vengono disabilitati automaticamente.  Quando l'unione è completa, se nel dataset sono presenti dei vincoli che non possono essere abilitati, verrà generata un'eccezione <xref:System.Data.ConstraintException>.  In questa situazione, la proprietà <xref:System.Data.DataSet.EnforceConstraints%2A> viene impostata su `false` e tutte le violazioni dei vincoli dovranno essere risolte prima di reimpostare la proprietà <xref:System.Data.DataSet.EnforceConstraints%2A> su `true`.  
  
 Una volta completato un aggiornamento, è possibile riabilitare il controllo dei vincoli. In questo modo verranno riabilitati e generati anche gli eventi di aggiornamento.  
  
 Per ulteriori informazioni sulla sospensione degli eventi, vedere [Procedura: disattivare i vincoli durante il riempimento di un dataset](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## Errori di aggiornamento dei dataset  
 Quando si aggiorna un record di un dataset, è possibile che si verifichi un errore.  Può accadere ad esempio che i dati vengano scritti inavvertitamente in una colonna troppo lunga o appartenente al tipo di dati non corretto o con altri problemi di integrità.  È inoltre possibile che i controlli di convalida specifici dell'applicazione generino degli errori personalizzati durante qualsiasi fase di un evento di aggiornamento.  Per ulteriori informazioni, vedere [Convalida dei dati nei dataset](../data-tools/validate-data-in-datasets.md).  
  
## Conservazione delle informazioni sulle modifiche  
 Le informazioni sulle modifiche apportate a un dataset vengono conservate in due modi: contrassegnando la riga che indica se il dataset è stato modificato \(<xref:System.Data.DataRow.RowState%2A>\) e conservando più copie di uno stesso record \(<xref:System.Data.DataRowVersion>\).  Utilizzando queste informazioni, i processi saranno in grado di individuare le modifiche apportate al dataset e di inviare all'origine dati gli aggiornamenti appropriati.  
  
### Proprietà RowState  
 La proprietà <xref:System.Data.DataRow.RowState%2A> di un oggetto <xref:System.Data.DataRow> è un valore che fornisce informazioni sullo stato di una determinata riga di dati.  
  
 Nella tabella che segue sono riportati in modo dettagliato i possibili valori dell'enumerazione <xref:System.Data.DataRowState>.  
  
|Valore di DataRowState|Descrizione|  
|----------------------------|-----------------|  
|<xref:System.Data.DataRowState>|La riga è stata aggiunta come elemento all'insieme <xref:System.Data.DataRowCollection>. Una riga che presenta questo stato non ha una versione originale corrispondente, in quanto non esisteva nel momento in cui è stato chiamato l'ultimo metodo <xref:System.Data.DataRow.AcceptChanges%2A>.|  
|<xref:System.Data.DataRowState>|La riga è stata eliminata utilizzando il metodo <xref:System.Data.DataRow.Delete%2A> di un oggetto <xref:System.Data.DataRow>.|  
|<xref:System.Data.DataRowState>|La riga è stata creata ma non fa parte di alcun insieme <xref:System.Data.DataRowCollection>.  Un oggetto <xref:System.Data.DataRow> presenta questo stato immediatamente dopo essere stato creato e prima di essere aggiunto a una raccolta oppure se è stato rimosso da una raccolta.|  
|<xref:System.Data.DataRowState>|Un valore di colonna presente nella riga è stato modificato.|  
|<xref:System.Data.DataRowState>|La riga non è stata modificata dal momento dell'ultima chiamata del metodo <xref:System.Data.DataRow.AcceptChanges%2A>.|  
  
### Enumerazione DataRowVersion  
 Nei dataset sono conservate più versioni dei record.  L'enumerazione <xref:System.Data.DataRowVersion> di un oggetto <xref:System.Data.DataRow> è un valore utilizzabile per restituire una determinata versione di un oggetto <xref:System.Data.DataRow>.  
  
 Nella tabella che segue sono riportati in modo dettagliato i possibili valori dell'enumerazione <xref:System.Data.DataRowVersion>.  
  
|Valore di DataRowVersion|Descrizione|  
|------------------------------|-----------------|  
|<xref:System.Data.DataRowVersion>|La versione corrente di un record contiene tutte le modifiche apportate al record dall'ultima volta in cui è stato chiamato il metodo <xref:System.Data.DataRow.AcceptChanges%2A>.  Se la riga è stata eliminata, non vi sarà alcuna versione corrente.|  
|<xref:System.Data.DataRowVersion>|Valore predefinito di un record, definito dall'origine dati o dallo schema del dataset.|  
|<xref:System.Data.DataRowVersion>|La versione originale di un record è una copia del record con lo stato che il record presentava dopo l'ultima applicazione delle modifiche nel dataset.  In pratica, si tratta di solito della versione di un record letto da un'origine dati.|  
|<xref:System.Data.DataRowVersion>|Versione proposta di un record disponibile temporaneamente, mentre è ancora in corso un aggiornamento, cioè tra la chiamata del metodo <xref:System.Data.DataRow.BeginEdit%2A> e la chiamata del metodo <xref:System.Data.DataRow.EndEdit%2A>.  In genere si accede alla versione proposta di un record in un gestore per un evento quale <xref:System.Data.DataTable.RowChanging>.  Richiamando il metodo <xref:System.Data.DataRow.CancelEdit%2A> vengono annullate le modifiche e viene eliminata la versione proposta della riga di dati.|  
  
 La versione originale e quella corrente sono utili quando le informazioni sull'aggiornamento vengono trasmesse a un'origine dati.  In genere, quando viene inviato un aggiornamento all'origine dati, le nuove informazioni per il database sono contenute nella versione corrente di un record  e le informazioni della versione originale vengono utilizzate per individuare il record da aggiornare.  Nel caso in cui, ad esempio, viene modificata la chiave primaria di un record, è necessario un metodo per individuare il record appropriato nell'origine dati, in modo da aggiornarlo con le modifiche.  Se non esistesse alcuna versione originale, il record verrebbe molto probabilmente aggiunto all'origine dati, determinando così non solo la presenza di un record supplementare indesiderato, ma anche di un record impreciso e non aggiornato.  Le due versioni vengono utilizzate inoltre per il controllo di concorrenza: è possibile confrontare la versione originale con un record dell'origine dati per determinare se il record ha subito delle modifiche dal momento in cui è stato caricato nel dataset.  
  
 La versione proposta è utile quando è necessario eseguire una convalida prima di applicare effettivamente le modifiche al dataset.  
  
 Anche se i record sono stati modificati, non sempre sono presenti le versioni originali o correnti della riga in questione.  Quando si inserisce una nuova riga nella tabella non è presente alcuna versione originale, ma solo una versione corrente.  Allo stesso modo, se si elimina una riga chiamando il metodo `Delete` della tabella, sarà presente una versione originale, ma non una versione corrente.  
  
 È possibile verificare l'esistenza di una determinata versione di un record eseguendo una query relativa al metodo <xref:System.Data.DataRow.HasVersion%2A> della riga di dati.   Per accedere a una o all'altra versione di un record, passare il valore di enumerazione <xref:System.Data.DataRowVersion> come argomento facoltativo quando si richiede il valore di una colonna.  
  
## Recupero dei record modificati  
 È normale che non tutti i record di un dataset vengano aggiornati.  È ad esempio possibile che un utente utilizzi un controllo <xref:System.Windows.Forms.DataGridView> di Windows Form nel quale vengono visualizzati molti record,  ma che ne aggiorni solo alcuni, ne elimini uno e inserisca un nuovo record.  Per i dataset e le tabelle dati è disponibile un metodo \(`GetChanges`\) per restituire solo le righe che sono state modificate.  
  
 È possibile creare subset dei record modificati utilizzando il metodo `GetChanges` della tabella dati \(<xref:System.Data.DataTable.GetChanges%2A>\) o dello stesso dataset \(<xref:System.Data.DataSet.GetChanges%2A>\).  Se si chiama il metodo per la tabella dati, verrà restituita una copia della tabella contenente solo i record modificati.  Allo stesso modo, chiamando il metodo nel dataset, verrà restituito un nuovo dataset contenente esclusivamente i record modificati.   Utilizzando `GetChanges` da solo verranno restituiti tutti i record modificati.  Al contrario, passando al metodo `GetChanges` l'enumerazione <xref:System.Data.DataRowState> desiderata come parametro, sarà possibile specificare il sottoinsieme di record modificati desiderato: nuovi record aggiunti, record contrassegnati per l'eliminazione, record disconnessi o record modificati.  
  
 Il recupero di un sottoinsieme di record modificati è particolarmente utile quando si desidera inviare i record a un altro componente per l'elaborazione.  Anziché inviare l'intero dataset, è possibile ridurre il sovraccarico di comunicazione con l'altro componente recuperando solo i record necessari.  Per ulteriori informazioni, vedere [Procedura: recuperare le righe modificate](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  
  
## Applicazione delle modifiche nel dataset  
 Quando vengono apportate modifiche al dataset, viene impostata la proprietà <xref:System.Data.DataRow.RowState%2A> delle righe modificate.  La versione originale e quella corrente dei record vengono definite, gestite e rese disponibili all'utente mediante la proprietà <xref:System.Data.DataRowView.RowVersion%2A>.  I metadati memorizzati in queste proprietà e che rappresentano le modifiche sono necessari per inviare all'origine dati gli aggiornamenti appropriati.  
  
 Se le modifiche riflettono lo stato corrente dell'origine dati, non sarà più necessario conservare queste informazioni.  In genere esistono due situazioni in cui il dataset e la relativa origine sono sincronizzati:  
  
-   Immediatamente dopo aver caricato le informazioni nel dataset, vale a dire quando i dati vengono letti dall'origine.  
  
-   Dopo aver inviato le modifiche dal dataset all'origine dati, ma non prima, poiché in questo caso andrebbero perdute le informazioni di modifica necessarie per inviare le modifiche al database.  
  
 È possibile applicare le modifiche in sospeso al dataset chiamando il metodo <xref:System.Data.DataSet.AcceptChanges%2A>.  Di solito in un'applicazione il metodo <xref:System.Data.DataSet.AcceptChanges%2A> viene chiamato nei casi seguenti:  
  
-   Dopo che il dataset è stato caricato.  Se si carica un dataset chiamando il metodo `Fill` di un oggetto TableAdapter, l'adattatore eseguirà automaticamente il commit delle modifiche.  Tuttavia, se si carica un dataset unendovi un altro dataset, sarà necessario eseguire manualmente il commit delle modifiche.  
  
    > [!NOTE]
    >  Per impedire che l'adattatore esegua il commit automatico delle modifiche quando si chiama il metodo `Fill`, è possibile impostare su `false` la proprietà `AcceptChangesDuringFill` dell'adattatore.  Se impostata su `false`, la proprietà <xref:System.Data.DataRow.RowState%2A> di ciascuna riga inserita durante la compilazione verrà impostata su <xref:System.Data.DataRowState>.  
  
-   Dopo aver inviato le modifiche del dataset a un altro processo, ad esempio a un servizio Web.  
  
    > [!CAUTION]
    >  Se viene eseguito il commit delle modifiche in questo modo, tutte le informazioni di modifica verranno eliminate.  Non applicare le modifiche finché non sono state svolte eventuali operazioni per le quali è necessario conoscere le modifiche apportate al dataset.  
  
 Con questo metodo vengono effettuate le seguenti operazioni:  
  
-   Scrittura della versione <xref:System.Data.DataRowVersion> di un record nella versione <xref:System.Data.DataRowVersion>, sovrascrivendola.  
  
-   Rimozione delle righe la cui proprietà <xref:System.Data.DataRow.RowState%2A> sia impostata su <xref:System.Data.DataRowState>.  
  
-   Impostazione della proprietà <xref:System.Data.DataRow.RowState%2A> di un record su <xref:System.Data.DataRowState>.  
  
 Il metodo <xref:System.Data.DataSet.AcceptChanges%2A> è disponibile a tre livelli.  È possibile chiamarlo su un oggetto <xref:System.Data.DataRow>, applicando così le modifiche solo alla riga in questione.  È inoltre possibile chiamarlo su un oggetto <xref:System.Data.DataTable> per applicare le modifiche a tutte le righe di una tabella, oppure sull'oggetto <xref:System.Data.DataSet> per applicare tutte le modifiche in sospeso di tutti i record di tutte le tabelle del dataset.  
  
 Nella tabella seguente vengono descritte le modifiche applicate a seconda dell'oggetto sul quale viene chiamato il metodo.  
  
|Metodo|Risultato|  
|------------|---------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Le modifiche vengono applicate solo alla riga specifica|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Le modifiche vengono applicate a tutte le righe della tabella specifica|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Le modifiche vengono applicate a tutte le righe di tutte le tabelle del dataset|  
  
> [!NOTE]
>  Se si carica un dataset chiamando il metodo `Fill` di un oggetto TableAdapter, non è necessario accettare in modo esplicito le modifiche. Per impostazione predefinita, infatti, il metodo `Fill` chiama il metodo `AcceptChanges` dopo aver terminato l'inserimento dei dati nella tabella dati.  
  
 Un metodo correlato, `RejectChanges`, annulla l'effetto delle modifiche copiando di nuovo la versione <xref:System.Data.DataRowVersion> sulla versione <xref:System.Data.DataRowVersion> dei record e impostando nuovamente la proprietà <xref:System.Data.DataRow.RowState%2A> di ciascun record su <xref:System.Data.DataRowState>.  
  
## Convalida dei dati  
 Per verificare che i dati presenti nell'applicazione soddisfino i requisiti dei processi ai quali vengono passati, è spesso necessario aggiungere un processo di convalida,  in modo da assicurarsi che l'immissione dei dati in un form da parte di un utente sia corretta, convalidare i dati inviati all'applicazione da un'altra applicazione o persino verificare che le informazioni calcolate all'interno del componente rispettino i vincoli dell'origine dati e i requisiti dell'applicazione.  
  
 È possibile convalidare i dati in diversi modi:  
  
-   A livello aziendale, aggiungendo all'applicazione il codice per la convalida dei dati.  Il dataset è uno degli oggetti in cui è possibile eseguire questa operazione.  La scelta di utilizzare il dataset offre alcuni dei vantaggi della convalida back\-end, quali la possibilità di convalidare le modifiche man mano che i valori di righe e di colonne vengono modificati.  Per ulteriori informazioni, vedere [Convalida dei dati nei dataset](../data-tools/validate-data-in-datasets.md).  
  
-   A livello di presentazione, aggiungendo la convalida ai form.  Per ulteriori informazioni, vedere [User Input Validation in Windows Forms](../Topic/User%20Input%20Validation%20in%20Windows%20Forms.md).  
  
-   Nel back\-end dei dati, inviando i dati all'origine dati, ad esempio al database, e consentendo all'origine dati di accettarli o rifiutarli.  Se si sta utilizzando un database che dispone di funzionalità complesse per la convalida dei dati e la visualizzazione delle informazioni sugli errori, questo può essere un approccio pratico, poiché consente di convalidare i dati indipendentemente dalla loro provenienza.  Tuttavia, tale approccio potrebbe non soddisfare i requisiti di convalida specifici dell'applicazione.  Inoltre, se si utilizza l'origine dati per convalidare i dati, potrebbero determinarsi numerosi percorsi di andata e ritorno all'origine dati, a seconda del modo in cui l'applicazione facilita la risoluzione degli errori di convalida generati dal back\-end.  
  
    > [!IMPORTANT]
    >  Quando si utilizzano comandi dati con una proprietà <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> impostata su <xref:System.Data.CommandType>, controllare attentamente le informazioni inviate da un client prima di passarle al database.  Utenti malintenzionati potrebbero tentare di inviare istruzioni SQL modificate o aggiuntive con l'obiettivo di ottenere un accesso non autorizzato o di danneggiare il database.  Prima di trasferire l'input di un utente in un database, si consiglia di verificare sempre che le informazioni siano valide. È opportuno utilizzare, quando possibile, query con parametri o stored procedure.  Per ulteriori informazioni, vedere [Script Exploits Overview](../Topic/Script%20Exploits%20Overview.md).  
  
 Dopo aver modificato un dataset, è possibile trasmettere le modifiche apportate a un'origine dati.  Nella maggior parte dei casi questa operazione viene eseguita chiamando il metodo `Update` di un TableAdapter \(o adattatore dati\).  Il metodo scorre in un ciclo ciascun record presente in una tabella dati, per determinare l'eventuale tipo di aggiornamento necessario, quali aggiornamento, inserimento o eliminazione; viene quindi eseguito il comando appropriato.  
  
## Trasmissione di un aggiornamento all'origine dati  
 Per comprendere il modo in cui vengono effettuati gli aggiornamenti, si supponga che nell'applicazione venga utilizzato un dataset contenente una singola tabella dati.  Nell'applicazione vengono recuperate due righe dal database.  Dopo il recupero, la tabella dati in memoria presenterà questa struttura:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Lo stato di Nancy Buchanan viene modificato in "Preferred". In seguito a questa modifica, il valore della proprietà <xref:System.Data.DataRow.RowState%2A> per quella riga passa da <xref:System.Data.DataRowState> a <xref:System.Data.DataRowState>.  Il valore della proprietà <xref:System.Data.DataRow.RowState%2A> per la prima riga rimane invece <xref:System.Data.DataRowState>.  La nuova struttura della tabella dati sarà la seguente:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 L'applicazione chiama ora il metodo `Update` per trasmettere il dataset al database.  Il metodo analizza una riga per volta.  Per la prima riga, il metodo non trasmette alcuna istruzione SQL al database, poiché quella riga non ha subito modifiche da quando è stata recuperata originariamente dal database.  
  
 Per la seconda riga, invece, il metodo `Update` richiama automaticamente il comando dati corretto e lo trasmette al database.  La sintassi specifica dell'istruzione SQL dipende dal sottolinguaggio SQL supportato dall'archivio dati sottostante.  Tuttavia, è necessario notare le seguenti caratteristiche dell'istruzione SQL trasmessa:  
  
-   L'istruzione SQL trasmessa è un'istruzione UPDATE.  L'adattatore riconosce l'utilizzo di un'istruzione UPDATE in quanto il valore della proprietà <xref:System.Data.DataRow.RowState%2A> è <xref:System.Data.DataRowState>.  
  
-   L'istruzione SQL trasmessa comprende una clausola WHERE, che indica che l'obiettivo dell'istruzione UPDATE è la riga con `CustomerID = 'c400'`.  Questa parte dell'istruzione SELECT riconosce la riga di destinazione tra tutte le altre, poiché `CustomerID` è la chiave primaria della tabella di destinazione.  Nel caso in cui valori necessari a identificare la riga fossero stati modificati, le informazioni per la clausola WHERE verranno derivate dalla versione originale del record \(`DataRowVersion.Original`\).  
  
-   L'istruzione SQL trasmessa comprende la clausola SET, che consente di impostare i nuovi valori delle colonne modificate.  
  
    > [!NOTE]
    >  Se la proprietà `UpdateCommand` dell'oggetto TableAdapter è stata impostata sul nome di una stored procedure, l'adattatore non creerà un'istruzione SQL.  Al contrario, esso richiamerà la stored procedure con i parametri appropriati che sono stati passati.  
  
## Passaggio di parametri  
 In genere i valori relativi ai record da aggiornare nel database vengono passati utilizzando i parametri.  Quando il metodo `Update` dell'oggetto TableAdapter esegue un'istruzione UPDATE, è necessario che vengano inseriti i valori del parametro.  Il metodo recupera tali valori dalla raccolta `Parameters` per il comando dati appropriato, in questo caso l'oggetto `UpdateCommand` presente nell'oggetto TableAdapter.  
  
 Se sono stati utilizzati gli strumenti di Visual Studio per generare un adattatore dati, nell'oggetto `UpdateCommand` sarà contenuta una raccolta di parametri che corrisponderanno a ciascun segnaposto di parametro presente nell'istruzione.  
  
 La proprietà <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> di ogni parametro punta a una colonna nella tabella dati.   La proprietà `SourceColumn` per i parametri `au_id` e `Original_au_id`, ad esempio, è impostata sulla colonna della tabella dati contenente l'ID dell'autore.  Quando viene eseguito il metodo `Update` dell'adattatore, la colonna dell'ID dell'autore viene letta dal record in fase di aggiornamento e vengono inseriti i valori nell'istruzione.  
  
 In un'istruzione UPDATE è necessario specificare sia i nuovi valori, cioè quelli che verranno scritti sul record, che i vecchi valori, per poter localizzare nel database il record che si desidera aggiornare.  Esistono perciò due parametri per ciascun valore: uno per la clausola SET e un altro per la clausola WHERE.  Per entrambi i parametri i dati vengono letti dal record che viene aggiornato, ma sono recuperate versioni diverse del valore della colonna, a seconda della [proprietà SqlParameter.SourceVersion](https://msdn.microsoft.com/en-us/library/system.data.sqlclient.sqlparameter.sourceversion.aspx) del parametro.  Il parametro per la clausola SET recupera la versione corrente, mentre il parametro per la clausola WHERE recupera la versione originale.  
  
> [!NOTE]
>  È inoltre possibile impostare direttamente nel codice i valori della raccolta `Parameters`, come generalmente accade in un gestore eventi per l'evento <xref:System.Data.DataTable.RowChanging> dell'adattatore dati.  
  
## Aggiornamento di tabelle correlate  
 Se nel dataset sono contenute più tabelle, sarà necessario aggiornarle singolarmente chiamando separatamente il metodo `Update` di ciascun adattatore dati.  Se le tabelle presentano una relazione padre\-figlio, potrebbe essere necessario inviare gli aggiornamenti al database in un determinato ordine.  Uno scenario comune è quello nel quale sono stati aggiunti sia i record padre che i record figlio correlati a un dataset, ad esempio, un nuovo record cliente e uno o più record di ordini correlati.  Se nello stesso database sono attivate le regole di integrità relazionale, verranno generati degli errori nel caso in cui i nuovi record figlio vengano inviati al database prima della creazione del record padre.  
  
 Al contrario, se si eliminano i record correlati dal dataset, in genere sarà necessario inviare gli aggiornamenti in ordine inverso: prima per la tabella figlio e quindi per la tabella padre.  In caso contrario, è probabile che nel database venga generato un errore, in quanto le regole di integrità referenziale impediranno l'eliminazione un record padre quando sono ancora presenti i record figlio correlati.  
  
 Una regola generale per inviare gli aggiornamenti relativi alle tabelle correlate consiste nel seguire questo ordine:  
  
1.  Tabella figlio: eliminare i record.  
  
2.  Tabella padre: inserire, aggiornare ed eliminare i record.  
  
3.  Tabella figlio: inserire e aggiornare i record.  
  
4.  Per ulteriori informazioni, vedere [Procedura dettagliata: salvataggio di dati in un database \(a più tabelle\)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
## Controllo della concorrenza  
 Poiché i dataset sono disconnessi dall'origine dati, non vengono mantenuti blocchi sui record dell'origine dati.  Di conseguenza, se si desidera aggiornare il database e se è importante per l'applicazione mantenere il controllo di concorrenza, sarà necessario risolvere le differenze tra i record del dataset con quelli presenti nel database.  Sarebbe ad esempio possibile scoprire che i record del database sono stati modificati dopo l'ultima compilazione del dataset.  In tal caso, è necessario eseguire una logica appropriata all'applicazione per specificare in che modo si desidera utilizzare i record del database o i record modificati presenti nel dataset.  
  
## Vedere anche  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)