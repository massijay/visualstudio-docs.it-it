---
title: "Utilizzo di dataset in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.DataSet"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "cache [Visual Studio], dataset"
  - "distinzione tra maiuscole e minuscole, dataset"
  - "record figlio"
  - "vincoli [Visual Basic], dataset"
  - "record corrente nel dataset"
  - "adattatori dati, compilazione di dataset"
  - "memorizzazione di dati nella cache, dataset"
  - "relazioni di dati"
  - "database [Visual Basic], aggiornamento"
  - "DataRelation (oggetto), dataset"
  - "DataSet (classe)"
  - "DataSet (classe), informazioni sui dataset"
  - "dataset [Visual Basic]"
  - "dataset [Visual Basic], proprietà estese"
  - "dataset [Visual Basic], riempimento"
  - "dataset [Visual Basic], msprop"
  - "dataset [Visual Basic], namespace"
  - "dataset [Visual Basic], compilazione"
  - "dataset [Visual Basic], relazioni"
  - "proprietà estese, in dataset tipizzati"
  - "chiavi esterne, dataset"
  - "Master-Details (tabelle), dataset"
  - "msprop"
  - "record padre nei dataset"
  - "tabelle correlate"
  - "tabelle correlate, dataset"
  - "relazioni, dataset"
  - "schemi [Visual Basic], dataset"
  - "dataset tipizzati"
  - "dataset tipizzati, confronto con dataset non tipizzati"
  - "vincoli univoci (dataset)"
  - "dataset non tipizzati"
  - "dataset non tipizzati, confronto con dataset tipizzati"
  - "aggiornamento di dataset, informazioni"
  - "XML [Visual Basic], dataset"
  - "XML Schema, informazioni su dataset e XML Schema"
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 49
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizzo di dataset in Visual Studio
I dataset sono oggetti che contengono tabelle di dati in cui è possibile memorizzare temporaneamente i dati da utilizzare nell'applicazione.  Se l'applicazione prevede che vengano utilizzati dei dati, è possibile caricarli in un dataset. In questo modo viene fornita all'applicazione una cache locale in memoria dei dati da utilizzare.  I dati contenuti nel dataset possono essere utilizzati anche se l'applicazione viene disconnessa dal database.  Le informazioni relative alle modifiche apportate ai dati del dataset vengono conservate all'interno di quest'ultimo così che, quando l'applicazione verrà riconnessa, gli aggiornamenti potranno essere rilevati e inviati al database.  
  
 Negli argomenti seguenti vengono forniti i dettagli relativi all'utilizzo dei dataset in Visual Studio:  
  
|Argomento|Descrizione|  
|---------------|-----------------|  
|[Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)|Viene fornita una spiegazione degli strumenti in fase di progettazione utilizzati per la creazione dei dataset.|  
|[Procedura: creare un dataset tipizzato](../data-tools/create-and-configure-datasets-in-visual-studio.md)|Viene illustrato come creare un dataset tipizzato mediante gli strumenti di progettazione disponibili in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Procedura: estendere la funzionalità di un dataset](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|Vengono fornite le istruzioni per creare una classe parziale per il dataset in cui poter aggiungere del codice oltre a quello generato mediante la finestra di progettazione.|  
|[Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)|Viene spiegato come aprire dataset da **Esplora soluzioni** e dalla finestra **Origini dati**.|  
|[Procedura: modificare un dataset](../Topic/How%20to:%20Edit%20a%20Dataset.md)|Viene spiegato come modificare gli oggetti di un dataset mediante **Progettazione DataSet**.|  
|[Procedura dettagliata: creazione di un dataset con Progettazione DataSet](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)|Vengono fornite istruzioni dettagliate per la creazione di un dataset tipizzato senza utilizzare la **Configurazione guidata origine dati**.|  
|[Progettazione di DataTable](../data-tools/designing-datatables.md)|Vengono forniti collegamenti ad argomenti in cui viene spiegato come creare e modificare tabelle dati con strumenti in fase di progettazione.|  
|[Relazioni nei dataset](../data-tools/relationships-in-datasets.md)|Vengono forniti collegamenti ad argomenti in cui viene spiegato come creare e modificare relazioni dati con strumenti in fase di progettazione.|  
|[TableAdapters](../Topic/TableAdapters.md)|Vengono forniti collegamenti ad argomenti in cui viene spiegato come creare e modificare oggetti TableAdapter con strumenti in fase di progettazione.|  
|[Utilizzo dei dataset nelle applicazioni a più livelli](../data-tools/work-with-datasets-in-n-tier-applications.md)|Vengono illustrate le applicazioni a più livelli e le funzionalità disponibili per l'utilizzo di dataset in tali applicazioni.|  
  
 Nella struttura di un oggetto <xref:System.Data.DataSet>, analoga a quella di un database relazionale, viene esposto un modello a oggetti gerarchico costituito da tabelle, righe, colonne, vincoli e relazioni.  
  
 I dataset possono essere tipizzati o non tipizzati.  Per ulteriori informazioni, vedere la sezione seguente "Dataset tipizzati e dataset non tipizzati". I dataset tipizzati derivano lo schema \(struttura di colonna e tabella\) dai file con estensione xsd e sono più facili da utilizzare nella programmazione.  Nelle applicazioni è possibile utilizzare entrambi i tipi di dataset.  In Visual Studio è tuttavia disponibile un supporto degli strumenti più esteso per i dataset tipizzati e la programmazione con questi ultimi risulta semplificata e meno tendente agli errori.  
  
 I dataset tipizzati vengono creati eseguendo la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) oppure aggiungendo un elemento **DataSet** mediante il comando **Aggiungi nuovo elemento** del menu **Progetto**.  Per ulteriori informazioni, vedere [Procedura: creare un dataset tipizzato](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
 I dataset non tipizzati vengono creati trascinando degli elementi **DataSet** dalla **Casella degli strumenti** in [Windows Forms Designer](http://msdn.microsoft.com/it-it/3c3d61f8-f36c-4d41-b9c3-398376fabb15) o in [Component Designer](../Topic/Component%20Designer.md).  
  
 Dopo aver creato i dataset, è possibile modificarli in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
 La creazione e l'utilizzo dei dataset tipizzati e non tipizzati è possibile grazie alle parti degli spazi dei nomi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] riportate di seguito.  
  
 ![Spazio dei nomi del Dataset dei dati di sistema](../data-tools/media/vbdatasetnamspace.png "vbDataSetNamspace")  
I dataset si trovano nello spazio dei nomi System.Data  
  
 Gli oggetti di un dataset vengono esposti all'utente mediante costrutti di programmazione standard, quali proprietà e raccolte.  Di seguito è riportato un esempio:  
  
-   La classe <xref:System.Data.DataSet> comprende la raccolta <xref:System.Data.DataTableCollection> di tabelle dati e la raccolta <xref:System.Data.DataRelationCollection> di oggetti <xref:System.Data.DataRelation>.  
  
-   La classe <xref:System.Data.DataTable> comprende la raccolta <xref:System.Data.DataRowCollection> di righe tabella, la raccolta <xref:System.Data.DataColumnCollection> di colonne dati e le raccolte <xref:System.Data.DataTable.ChildRelations%2A> e <xref:System.Data.DataTable.ParentRelations%2A> di relazioni dati.  
  
-   La classe <xref:System.Data.DataRow> comprende la proprietà <xref:System.Data.DataRow.RowState%2A>, i cui valori indicano se la riga è stata modificata dopo il primo caricamento della tabella dati dal database e il tipo di modifiche apportate.  I valori possibili per la proprietà <xref:System.Data.DataRow.RowState%2A> sono <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> e <xref:System.Data.DataRowState>.  
  
## Popolamento dei dataset con i dati  
 Per impostazione predefinita un dataset non contiene dati effettivi.  Il riempimento di un dataset consiste in realtà nel caricamento dei dati nei singoli oggetti <xref:System.Data.DataTable> che costituiscono il dataset.  Le tabelle dati vengono riempite mediante l'esecuzione di query TableAdapter o di comandi dell'adattatore dati, ad esempio <xref:System.Data.SqlClient.SqlDataAdapter>.  Quando si riempie un dataset con dati, vengono generati diversi eventi, viene applicato il controllo dei vincoli e così via.  Per ulteriori informazioni sul caricamento di dati in un dataset, vedere [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md).  
  
 Il codice che consente di compilare un dataset viene aggiunto automaticamente al gestore eventi di caricamento dei form quando si trascinano elementi dalla [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md) in un form dell'applicazione Windows.  Per ulteriori informazioni, completare la seguente procedura: [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
 Esempio di compilazione di un dataset con un oggetto TableAdapter:  
  
 [!CODE [VbRaddataDatasets#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#1)]  
  
 Sono disponibili diversi modi per compilare un dataset.  
  
-   Se per la creazione del dataset sono stati utilizzati strumenti in fase di progettazione, quali le procedure guidate di gestione dei dati, chiamare il metodo `Fill` di un TableAdapter.  I TableAdapter vengono creati con un metodo `Fill` predefinito, di cui è tuttavia possibile modificare il nome, così che il nome effettivo del metodo può essere diverso. Per ulteriori informazioni, vedere la sezione "Riempimento di un dataset mediante un TableAdapter" di [Procedura: riempire un dataset](../data-tools/how-to-fill-a-dataset-with-data.md).  
  
-   Chiamare il metodo `Fill` di un <xref:System.Data.Common.DataAdapter>.  Per ulteriori informazioni, vedere [Compilazione di un DataSet da un oggetto DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
-   È possibile inserire manualmente dati nelle tabelle del dataset creando oggetti <xref:System.Data.DataRow> e aggiungendoli alla raccolta <xref:System.Data.DataRowCollection> della tabella.  Questa operazione può essere eseguita solo in fase di esecuzione. La raccolta <xref:System.Data.DataRowCollection> non può essere infatti impostata in fase di progettazione. Per ulteriori informazioni, vedere [Aggiunta di dati a una DataTable](../Topic/Adding%20Data%20to%20a%20DataTable.md).  
  
-   È possibile leggere un documento o un flusso XML nel dataset.  Per ulteriori informazioni, vedere il metodo <xref:System.Data.DataSet.ReadXml%2A>.  Per un esempio, vedere [Procedura dettagliata: lettura dei dati XML in un dataset](../data-tools/read-xml-data-into-a-dataset.md).  
  
-   È possibile unire \(copiare\) il contenuto di due dataset.  Questo metodo può rivelarsi utile se nell'applicazione vengono recuperati da origini diverse, ad esempio servizi Web diversi, dataset che devono essere consolidati in un unico dataset.  Per ulteriori informazioni, vedere [Unione del contenuto di un DataSet](../Topic/Merging%20DataSet%20Contents.md).  
  
-   È possibile unire \(copiare\) il contenuto di due <xref:System.Data.DataTable>.  
  
## Salvataggio dei dati di un dataset in un database  
 Le modifiche apportate ai record del dataset devono essere registrate nel database.  Per inserire nel database le modifiche apportate al dataset, chiamare il metodo `Update` del TableAdapter o del <xref:System.Data.Common.DataAdapter> con cui è gestita la comunicazione tra il dataset e il database corrispondente.  
  
 Quando si utilizzano gli strumenti di progettazione dati in Visual Studio, è possibile inviare i dati a un database chiamando il metodo Update di TableAdapter e passando la tabella di dati che si desidera salvare.  Di seguito è riportato un esempio:  
  
 [!CODE [VbRaddataDatasets#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#2)]  
  
 Per un maggiore controllo sul processo di aggiornamento, chiamare uno dei metodi DBDirect di TableAdapter che consente di passare valori specifici per ogni riga di dati.  Per ulteriori informazioni, vedere [Procedura: aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) e [Procedura dettagliata: salvataggio di dati con i metodi DBDirect di TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md).  
  
 La classe <xref:System.Data.DataRow> utilizzata per modificare i singoli record comprende la proprietà <xref:System.Data.DataRow.RowState%2A>, i cui valori indicano se la riga è stata modificata dopo il primo caricamento della tabella dati dal database e il tipo di modifiche apportate.  I valori possibili sono <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> e <xref:System.Data.DataRowState>.  I metodi `Update` del TableAdapter e del <xref:System.Data.Common.DataAdapter> esaminano il valore della proprietà <xref:System.Data.DataRow.RowState%2A> per determinare i record da inserire nel database e il comando di database specifico \(`InsertCommand`, `UpdateCommand` e `DeleteCommand`\) da richiamare.  
  
 Per ulteriori informazioni sull'aggiornamento dei dati, vedere [Salvataggio di dati](../data-tools/saving-data.md).  
  
## Spostamento tra i record dei dataset  
 Dal momento che si tratta di contenitori di dati completamente disconnessi, i dataset non supportano il concetto di record corrente, a differenza dei recordset ADO.  Tutti i record presenti nel dataset sono invece disponibili in qualsiasi momento.  
  
 In assenza di un record corrente, non esistono proprietà specifiche che puntano a un record corrente, né metodi o proprietà per lo spostamento tra record \(vedere la nota riportata di seguito\).  È possibile accedere a singole tabelle nel dataset come oggetti. Ogni tabella espone infatti una raccolta di righe.  Il trattamento è analogo a quello riservato a qualsiasi altra raccolta, ovvero è possibile accedere alle righe tramite l'indice della raccolta o utilizzando istruzioni specifiche della raccolta nel linguaggio di programmazione in uso.  
  
 È, ad esempio, possibile ottenere la quarta riga della tabella `Customers` con il seguente codice:  
  
 [!CODE [VbRaddataDatasets#3](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#3)]  
  
> [!NOTE]
>  Per l'associazione dei controlli di un form a un dataset, è possibile utilizzare il componente <xref:System.Windows.Forms.BindingNavigator> per semplificare l'accesso ai singoli record.  Per ulteriori informazioni, vedere [Procedura: esplorare dati in Windows Form](../Topic/How%20to:%20Navigate%20Data%20in%20Windows%20Forms.md).  
  
## Da LINQ a DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] abilita [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) su dati in un oggetto <xref:System.Data.DataSet>.  Per ulteriori informazioni, vedere [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## Dataset e linguaggio XML  
 Per dataset si intende una visualizzazione relazionale di dati che può essere rappresentata in linguaggio XML.  Questa relazione tra i dataset e XML consente di usufruire delle funzionalità dei dataset riportate di seguito.  
  
-   La struttura di un dataset, incluse tabelle, colonne, relazioni e vincoli, può essere definita in uno schema XML.  Con i dataset è possibile leggere e scrivere schemi contenenti informazioni strutturate mediante i metodi <xref:System.Data.DataSet.ReadXmlSchema%2A> e <xref:System.Data.DataSet.WriteXmlSchema%2A>.  Se non è disponibile alcuno schema, il dataset è in grado di ricavarne uno tramite il metodo <xref:System.Data.DataSet.InferXmlSchema%2A>, utilizzando i dati contenuti in un documento XML con struttura relazionale.  Per ulteriori informazioni sugli schemi XML, vedere [Compilazione di XML Schema](../Topic/Building%20XML%20Schemas.md).  
  
-   È possibile generare una classe di dataset in cui siano incorporate le informazioni sullo schema necessarie per definirne la struttura dei dati.  Tale classe viene definita dataset *tipizzato*.  Per informazioni sulla creazione di un dataset tipizzato, vedere [Procedura: creare un dataset tipizzato](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   È possibile leggere un flusso o documento XML in un dataset e scrivere quest'ultimo come XML rispettivamente utilizzando il metodo <xref:System.Data.DataSet.ReadXml%2A> e <xref:System.Data.DataSet.WriteXml%2A> del dataset stesso.  Dal momento che XML è un formato standard di interscambio dei dati tra applicazioni diverse, è possibile caricare un dataset con informazioni in formato XML inviate da altre applicazioni.  Allo stesso modo, i dati di un dataset possono essere convertiti in un flusso o in un documento XML per la condivisione con altre applicazioni o semplicemente per l'archiviazione in un formato standard.  
  
-   È possibile creare una visualizzazione XML \(un oggetto <xref:System.Xml.XmlDataDocument>\) del contenuto di un dataset o di una tabella dati, quindi visualizzare e modificare i dati utilizzando metodi relazionali, mediante il dataset, o metodi XML.  In caso di modifica, le due visualizzazioni vengono sincronizzate automaticamente.  
  
## Dataset tipizzati e dataset non tipizzati  
 Per dataset tipizzato si intende un dataset derivato inizialmente da una classe <xref:System.Data.DataSet> base, al quale vengono aggiunte successivamente le informazioni di **Progettazione DataSet**, contenute in un file XSD, per generare una nuova classe DataSet fortemente tipizzata.  Le informazioni dello schema \(tabelle, colonne e così via\) vengono generate e compilate in questa nuova classe Dataset come un set di proprietà e oggetti di prima classe.  Dal momento che un dataset tipizzato eredita dalla classe <xref:System.Data.DataSet> base, la classe tipizzata ne assume tutte le funzionalità e può essere utilizzata con i metodi che accettano come parametro un'istanza della classe <xref:System.Data.DataSet>.  
  
 Al contrario, un dataset non tipizzato non è dotato di uno schema incorporato corrispondente.  Così come i dataset tipizzati, i dataset non tipizzati contengono tabelle, colonne e così via, che tuttavia vengono esposti solo come raccolte.  Dopo aver creato manualmente le tabelle e altri elementi di dati in un dataset non tipizzato, è tuttavia possibile esportarne la struttura come schema mediante il relativo metodo <xref:System.Data.DataSet.WriteXmlSchema%2A>.  
  
### Accesso ai dati nei dataset tipizzati e non tipizzati  
 La classe di un dataset tipizzato presenta un modello a oggetti nel quale le relative proprietà hanno il nome delle tabelle e delle colonne.  Se si utilizza un dataset tipizzato, ad esempio, è possibile fare riferimento a una colonna utilizzando il seguente codice:  
  
 [!CODE [VbRaddataDatasets#4](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#4)]  
  
 Al contrario, se si utilizza un dataset non tipizzato, il codice equivalente sarà il seguente:  
  
 [!CODE [VbRaddataDatasets#5](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#5)]  
  
 Oltre a offrire una maggiore semplicità di lettura, l'accesso tipizzato è completamente supportato da IntelliSense nell'**editor di codice** di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  In aggiunta a una maggiore facilità di utilizzo, la sintassi per i dataset tipizzati consente il controllo dei tipi in fase di compilazione, riducendo significativamente la possibilità di errori nell'assegnazione dei valori ai membri del dataset.  Se si modifica il nome di una colonna nel <xref:System.Data.DataSet> e si procede alla compilazione dell'applicazione, viene visualizzato un errore di compilazione.  Facendo doppio clic su tale errore nell'**Elenco attività**, è possibile passare direttamente alla riga o alle righe di codice che fanno riferimento al nome di colonna precedente.  In un dataset tipizzato l'accesso alle tabelle e alle colonne si rivela, inoltre, leggermente più veloce in fase di esecuzione, in quanto viene determinato in fase di compilazione anziché in fase di esecuzione, tramite raccolte.  
  
 Sebbene siano numerosi i vantaggi offerti dai dataset, i dataset non tipizzati possono rivelarsi utili in numerose circostanze.  L'esempio più evidente è rappresentato dal caso in cui non sia disponibile uno schema per il dataset.  Questo può verificarsi se l'applicazione interagisce con un componente da cui viene restituito un dataset del quale non si conosce in anticipo la struttura.  Analogamente, se si utilizzano dati che non sono caratterizzati da una struttura statica prevedibile, non è opportuno utilizzare un dataset tipizzato, in quanto sarebbe necessario rigenerare la classe Dataset tipizzata per ogni modifica apportata alla struttura dei dati.  
  
 Più in generale, esistono numerosi casi in cui può essere creato un dataset in modo dinamico, in assenza di uno schema.  In tal caso, il dataset è solo una struttura utile in cui memorizzare le informazioni, a condizione che sia possibile una rappresentazione relazionale dei dati.  Allo stesso tempo, è possibile usufruire delle funzionalità offerte dal dataset, quali la possibilità di serializzare le informazioni da passare a un altro processo oppure di scrivere un file XML.  
  
## Distinzione tra maiuscole e minuscole nei dataset  
 Per impostazione predefinita, i nomi delle colonne e delle tabelle di un dataset non presentano alcuna distinzione tra maiuscole e minuscole. In altre parole, è anche possibile utilizzare "customers" per fare riferimento a una tabella di un dataset denominata "Customers". In questo caso vengono rispettate le convenzioni di denominazione di numerosi database, incluso il comportamento predefinito di SQL Server, in cui non è possibile distinguere i nomi degli elementi di dati solo in base alla combinazione di maiuscole\/minuscole.  
  
> [!NOTE]
>  A differenza dei dataset, per i documenti XML e di conseguenza per i nomi degli elementi di dati definiti negli schemi viene fatta distinzione tra maiuscole e minuscole.  A seconda del protocollo, lo schema può definire una tabella denominata "Customers" e un'altra tabella denominata "customers". Ciò può determinare conflitti di nome quando per generare una classe di dataset si utilizza uno schema che contiene elementi che si distinguono solo per la combinazione maiuscole\/minuscole.  
  
 La distinzione tra maiuscole e minuscole, tuttavia, può influire sull'interpretazione dei dati all'interno del dataset.  Se, ad esempio, si filtrano i dati in una tabella del dataset, i criteri di ricerca possono restituire risultati diversi a seconda che il confronto venga effettuato con o senza distinzione tra maiuscole o minuscole.  Per controllare la distinzione tra maiuscole e minuscole nelle operazioni di filtro, ricerca e ordinamento è possibile impostare la proprietà <xref:System.Data.DataSet.CaseSensitive%2A> del dataset.  Per impostazione predefinita, il valore di questa proprietà viene ereditato da tutte le tabelle del dataset.  Per eseguire l'override di questa proprietà per ogni tabella è possibile impostare la relativa proprietà <xref:System.Data.DataTable.CaseSensitive%2A>.  
  
## Tabelle correlate e oggetti DataRelation  
 Se in un dataset sono presenti più tabelle, le relative informazioni possono essere correlate.  Per un dataset il riconoscimento di tali relazioni non è implicito. Per gestire i dati contenuti in tabelle correlate è quindi possibile creare oggetti <xref:System.Data.DataRelation> in cui siano descritte le relazioni tra le tabelle del dataset.  Per ulteriori informazioni, vedere [Procedura: accedere ai record di DataTable correlate](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md).  Gli oggetti <xref:System.Data.DataRelation> possono essere utilizzati per recuperare a livello di codice i record figlio di un record padre e un record padre da un record figlio.   Per ulteriori informazioni, vedere [Relazioni nei dataset](../data-tools/relationships-in-datasets.md).  Se il database contiene relazioni tra due o più tabelle, gli oggetti <xref:System.Data.DataRelation> verranno creati automaticamente dagli strumenti di progettazione.  
  
 Si immagini l'esempio dei dati sul cliente \(customer\) e l'ordine \(order\) come quelli contenuti nel database Northwind.  La tabella `Customers` potrebbe contenere record simili al seguente:  
  
```  
CustomerID   CompanyName               City  
ALFKI        Alfreds Futterkiste       Berlin  
ANTON        Antonio Moreno Taquerias  Mexico D.F.  
AROUT        Around the Horn           London  
```  
  
 Il dataset può, inoltre, comprendere un'altra tabella con le informazioni relative agli ordini.  La tabella `Orders` contiene un ID cliente come colonna di chiave esterna.  Selezionando solo alcune colonne della tabella `Orders` è possibile ottenere quanto segue:  
  
```  
OrderId    CustomerID    OrderDate  
10692      ALFKI         10/03/1997  
10702      ALFKI         10/13/1997  
10365      ANTON         11/27/1996  
10507      ANTON         4/15/1997  
```  
  
 Dal momento che a un cliente possono corrispondere più ordini, tra clienti e ordini esiste una relazione uno\-a\-molti.  Nella tabella sopra riportata, ad esempio, al cliente ALFKI sono associati due ordini.  
  
 L'oggetto <xref:System.Data.DataRelation> consente di ottenere record correlati da una tabella padre o da una tabella figlio.  Se, ad esempio, si utilizza il record relativo al cliente ANTON, è possibile ottenere la raccolta dei record contenenti le descrizioni degli ordini di tale cliente.  Per ulteriori informazioni, vedere <xref:System.Data.DataRow.GetChildRows%2A>.  Analogamente, quando si utilizza il record che descrive l'ID ordine 10507, è possibile spostarsi verso l'alto nell'oggetto relazione per ottenere il record relativo all'elemento padre associato, ANTON.  Per ulteriori informazioni, vedere <xref:System.Data.DataRow.GetParentRow%2A>.  
  
## Vincoli  
 Così come nella maggior parte dei database, nei dataset sono supportati dei vincoli per garantire l'integrità dei dati.  I vincoli sono regole che vengono applicate quando si inseriscono, aggiornano o eliminano righe in una tabella.  È possibile definire due tipi di vincoli:  
  
-   Vincoli *UNIQUE* che consentono di verificare l'univocità dei nuovi valori di una colonna all'interno della tabella.  
  
-   Vincoli *foreign\-key* con cui vengono definite le regole per l'aggiornamento dei record figlio correlati quando viene aggiornato o eliminato un record di una tabella principale.  Un vincolo foreign\-key verifica, ad esempio, la presenza di un record padre prima di consentire la creazione di eventuali record figlio.  
  
 In un dataset i vincoli possono essere associati a singole tabelle \(vincoli della chiave esterna\) oppure a singole colonne \(vincoli univoci che garantiscono l'univocità dei valori della colonna\).  I vincoli vengono implementati come oggetti di tipo <xref:System.Data.UniqueConstraint> o <xref:System.Data.ForeignKeyConstraint>.  Vengono quindi aggiunti alla raccolta <xref:System.Data.DataTable.Constraints%2A> di una <xref:System.Data.DataTable>.  Un metodo alternativo per specificare un vincolo UNIQUE consiste nell'impostare la proprietà <xref:System.Data.DataColumn.Unique%2A> di una <xref:System.Data.DataColumn> su `true`.  
  
 Il dataset stesso supporta una proprietà booleana <xref:System.Data.DataSet.EnforceConstraints%2A> che consente di specificare se i vincoli verranno attivati.  Per impostazione predefinita, questa proprietà è impostata su `true`.  Talvolta però risulta più utile disattivare temporaneamente i vincoli,  soprattutto nei casi in cui si modifica un record in modo da causare temporaneamente uno stato non valido.  Al termine della modifica viene ripristinato uno stato valido ed è, quindi, possibile riabilitare i vincoli.  
  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i vincoli vengono creati implicitamente quando viene definito un dataset.  Aggiungendo una chiave primaria a un dataset, viene infatti implicitamente creato un vincolo univoco per la colonna di chiave primaria.  È, inoltre, possibile specificare vincoli UNIQUE per le altre colonne impostando la relativa proprietà <xref:System.Data.DataColumn.Unique%2A> su `true`.  
  
 I vincoli foreign\-key vengono definiti creando un oggetto <xref:System.Data.DataRelation> nel dataset.  Oltre a consentire di ottenere informazioni sui record correlati a livello di codice, un oggetto <xref:System.Data.DataRelation> permette di definire regole di vincolo foreign\-key.  
  
## Proprietà estese del dataset  
 Le proprietà estese forniscono i mapping dei nomi quando si verificano conflitti di denominazione durante il processo di generazione del dataset da un file XSD.  Quando un identificatore contenuto nel file XSD è diverso dal nome calcolato creato dal generatore del dataset, viene aggiunta una proprietà estesa al dataset nello spazio dei nomi `msprop`.  Nella tabella seguente sono riportate le proprietà estese che possono essere generate.  
  
|Object|Proprietà estesa|  
|------------|----------------------|  
|<xref:System.Data.DataSet>|msprop:Generator\_UserDSName|  
||msprop:Generator\_DataSetName|  
|<xref:System.Data.DataTable>|msprop:Generator\_UserTableName|  
||msprop:Generator\_TablePropName|  
||msprop:Generator\_TableVarName|  
||msprop:Generator\_TableClassName|  
||msprop:Generator\_RowClassName|  
||msprop:Generator\_RowEvHandlerName|  
||msprop:Generator\_RowEvArgName|  
|<xref:System.Data.DataColumn>|msprop:Generator\_UserColumnName|  
||msprop:Generator\_ColumnPropNameInTable|  
||msprop:Generator\_ColumnVarNameInTable|  
||msprop:Generator\_ColumnPropNameInRow|  
  
## Vedere anche  
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)