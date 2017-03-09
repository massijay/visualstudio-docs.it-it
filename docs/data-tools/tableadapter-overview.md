---
title: "Cenni preliminari sugli oggetti TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DataAccessor"
  - "vbdata.Microsoft.VSDesigner.DataSource.DataAccessor"
  - "TableAdapter"
  - "vs.data.TableAdapter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], dataset"
  - "dati [Visual Studio], adattatori di tabelle"
  - "dati [Visual Studio], TableAdapters"
  - "dati di query in Visual Studio"
  - "adattatori di tabelle"
  - "TableAdapter.Fill"
  - "TableAdapter.GetData"
  - "TableAdapters"
  - "TableAdapters, query"
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
caps.handback.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Cenni preliminari sugli oggetti TableAdapter
Gli oggetti TableAdapter consentono di stabilire una comunicazione tra l'applicazione e un database.  In particolare, un oggetto TableAdapter consente di connettersi a un database e di eseguire query o stored procedure e quindi restituisce una nuova tabella di dati popolata con i dati ottenuti oppure riempie un oggetto <xref:System.Data.DataTable> esistente con i dati ottenuti.  I TableAdapter vengono utilizzati inoltre per inviare i dati aggiornati dall'applicazione al database.  
  
 Gli utenti di versioni precedenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] possono considerare un oggetto TableAdapter come un oggetto <xref:System.Data.Common.DataAdapter> con un oggetto connessione incorporato e la capacità di contenere più query.  Ciascuna query aggiunta a un TableAdapter viene esposta come metodo pubblico che viene chiamato con la stessa semplicità con cui si chiama qualsiasi altro metodo o funzione su un oggetto.  
  
 Oltre alla funzionalità standard di un oggetto <xref:System.Data.Common.DataAdapter>, i TableAdapter offrono altri metodi tipizzati per l'incapsulamento di query che condividono uno schema comune con l'oggetto <xref:System.Data.DataTable> tipizzato associato.  In altre parole, un TableAdapter può contenere un numero qualsiasi di query, a condizione che restituiscano dati conformi al medesimo schema.  
  
 Nella versione precedente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per le comunicazioni tra un'applicazione e un database venivano utilizzati gli adattatori dati ADO.NET.  Mentre gli adattatori dati rimangono un componente principale di [Provider di dati .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md), gli oggetti TableAdapter sono componenti generati nella finestra di progettazione che migliorano la funzionalità degli oggetti <xref:System.Data.Common.DataAdapter>.  Gli oggetti TableAdapter contengono in genere metodi `Fill` e `Update` che consentono di recuperare e aggiornare dati in un database.  
  
 I TableAdapter vengono creati con **Progettazione DataSet** all'interno di dataset fortemente tipizzati.  È possibile creare oggetti TableAdapter durante la creazione di un nuovo dataset con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  La creazione può avvenire anche nei dataset esistenti con la [TableAdapter \(configurazione guidata\)](../Topic/TableAdapter%20Configuration%20Wizard.md) oppure mediante il trascinamento di oggetti di database da **Esplora server** in **Progettazione DataSet**.  Per ulteriori informazioni, vedere [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
 Sebbene i TableAdapter vengano progettati con **Progettazione DataSet**, le classi TableAdapter generate non vengono create come classi annidate di <xref:System.Data.DataSet> e si trovano in uno spazio dei nomi separato specifico di ciascun dataset.  Se, ad esempio, si dispone di un dataset denominato `NorthwindDataSet`, i TableAdapter associati agli oggetti <xref:System.Data.DataTable> nel `NorthwindDataSet` si troveranno nello spazio dei nomi `NorthwindDataSetTableAdapters`.  Per accedere a livello di codice a un determinato TableAdapter, è necessario dichiararne una nuova istanza.  Ad esempio:  
  
 [!CODE [VbRaddataTableAdapters#7](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#7)]  
  
## Schema di una DataTable associata  
 Durante la creazione di un TableAdapter, la query o la stored procedure iniziale viene utilizzata per definire lo schema della <xref:System.Data.DataTable> ad esso associata.  Per eseguire tale query o la stored procedure, chiamare il metodo `Fill` principale del TableAdapter, che determina il riempimento della <xref:System.Data.DataTable> associata.  Le modifiche apportate a una query principale del TableAdapter si riflettono nello schema della tabella dati associata.  La rimozione di una colonna dalla query principale, ad esempio, comporta la rimozione della colonna dalla tabella dati associata.  Se nell'oggetto TableAdapter sono presenti query aggiuntive in cui sono utilizzate istruzioni SQL che restituiscono colonne non incluse nella query principale, nella finestra di progettazione verrà effettuato un tentativo di sincronizzare le modifiche apportate nelle colonne tra la query principale e le eventuali query aggiuntive.  Per ulteriori informazioni, vedere [Procedura: modificare oggetti TableAdapter](../Topic/How%20to:%20Edit%20TableAdapters.md).  
  
## Comandi di aggiornamento dei TableAdapter  
 La funzionalità di aggiornamento di un oggetto TableAdapter dipende dalla quantità di informazioni disponibili sulla base della query principale fornita nella Configurazione guidata query TableAdapter.  Ad esempio, i TableAdapter configurati per il recupero di valori da più tabelle \(JOIN\), valori scalari, visualizzazioni o i risultati di funzioni aggregate non vengono creati inizialmente con la capacità di inviare aggiornamenti al database sottostante.  È tuttavia possibile configurare manualmente i comandi INSERT, UPDATE e DELETE nella finestra **Proprietà**.  
  
## Query TableAdapter  
 ![TableAdapter con più query](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 A differenza degli adattatori dati standard, i TableAdapter possono contenere più query per riempire le tabelle dati associate.  È possibile definire tutte le query relative a un oggetto TableAdapter richieste dall'applicazione, purché ciascuna di esse restituisca dati conformi allo stesso schema della tabella dati associata.  In questo modo diventa possibile caricare dati che soddisfano criteri diversi.  Se, ad esempio, l'applicazione contiene una tabella di clienti, è possibile creare due query, una per inserire nella tabella i nomi dei clienti che iniziano con una determinata lettera e l'altra per inserirvi tutti i clienti che risiedono nello stesso stato.  Per compilare una tabella `Customers` con i nomi dei clienti di un determinato stato, è possibile creare una `FillByState` che accetta un parametro per il valore dello stato: `SELECT * FROM Customers WHERE State = @State`.  Per eseguire la query, chiamare il metodo `FillByState` e passare il valore del parametro in questo modo: `CustomerTableAdapter.FillByState("WA")`.  Per ulteriori informazioni, vedere [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
 Oltre alle query che restituiscono dati dello stesso schema della tabella dati del TableAdapter, è possibile aggiungere query che restituiscono valori scalari \(singoli\).  La creazione di una query che restituisce un numero di clienti \(`SELECT Count(*) From Customers`\), ad esempio, è considerata valida per un oggetto `CustomersTableAdapter` sebbene i dati restituiti non siano conformi allo schema della tabella.  
  
## Proprietà ClearBeforeFill  
 TableAdapter aggiunge una proprietà non disponibile nella classe <xref:System.Data.Common.DataAdapter> di base.  Per impostazione predefinita, ogni volta che si esegue una query per riempire una tabella dati del TableAdapter, i dati vengono cancellati e nella tabella vengono caricati solo i risultati della query.  Impostare la proprietà `ClearBeforeFill` del TableAdapter su `false` per aggiungere o unire i dati restituiti da una query ai dati esistenti in una tabella dati.  Indipendentemente dalla cancellazione dei dati, è necessario inviare esplicitamente gli aggiornamenti al database, se lo si desidera.  È importante quindi salvare le modifiche apportate ai dati nella tabella prima di eseguire un'altra query che determina il riempimento della tabella.  Per ulteriori informazioni, vedere [Procedura: aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## Ereditarietà dei TableAdapter  
 I TableAdapter estendono la funzionalità di adattatori dati standard mediante l'incapsulamento di un <xref:System.Data.Common.DataAdapter> configurato.  Per impostazione predefinita, l'oggetto TableAdapter eredita da <xref:System.ComponentModel.Component> e non può eseguire il cast sulla classe <xref:System.Data.Common.DataAdapter>.  Il cast di un TableAdapter su un <xref:System.Data.Common.DataAdapter> genera un <xref:System.InvalidCastException>.  Per modificare la classe di base di un TableAdapter, è possibile specificare una classe derivante da <xref:System.ComponentModel.Component> nella proprietà **Base Class** del TableAdapter in **Progettazione DataSet**.  
  
## Metodi e proprietà dei TableAdapter  
 Dal momento che la classe TableAdapter non fa parte di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], non è possibile cercarla nella documentazione o nel **Visualizzatore oggetti**.  La classe viene creata in fase di progettazione quando si utilizza una delle procedure guidate sopra indicate.  Il nome assegnato a un TableAdapter durante la creazione si basa sul nome della tabella utilizzata.  Quando ad esempio si crea un TableAdapter basato su una tabella in un database denominato `Orders`, a tale TableAdapter viene assegnato il nome `OrdersTableAdapter`.  Il nome di classe dell'oggetto TableAdapter può essere modificato utilizzando la proprietà **Name** in **Progettazione DataSet**.  
  
 Di seguito sono riportati i metodi e le proprietà degli oggetti TableAdapter utilizzati più di frequente:  
  
|Membro|Descrizione|  
|------------|-----------------|  
|`TableAdapter.Fill`|Consente di popolare la tabella di dati associata al TableAdapter con i risultati del comando SELECT del TableAdapter.  Per ulteriori informazioni, vedere [Procedura: riempire un dataset](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Consente di restituire le modifiche al database e di restituire un numero intero che rappresenta il numero di righe interessate dall'aggiornamento.  Per ulteriori informazioni, vedere [Procedura: aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Restituisce un nuovo oggetto <xref:System.Data.DataTable> completo di dati.|  
|`TableAdapter.Insert`|Consente di creare una nuova riga nella tabella di dati.  Per ulteriori informazioni, vedere [Procedura: aggiungere righe a una DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).|  
|`TableAdapter.ClearBeforeFill`|Determina se una tabella di dati viene svuotata prima di chiamare uno dei metodi `Fill`.|  
  
## Metodo di aggiornamento dei TableAdapter  
 I TableAdapter utilizzano comandi dati per l'esecuzione di operazioni di lettura e scrittura nel database.  La query iniziale `Fill` \(principale\) del TableAdapter viene utilizzata come base per la creazione dello schema della tabella dati associata, oltre ai comandi `InsertCommand`, `UpdateCommand` e `DeleteCommand` associati al metodo `TableAdapter.Update`.  Ciò significa che la chiamata di un metodo `Update` del TableAdapter consente di eseguire le istruzioni create al momento della configurazione originale del TableAdapter e non una delle altre query aggiunte con la **Configurazione guidata query TableAdapter**.  
  
 L'utilizzo di un oggetto TableAdapter consente di eseguire con efficacia mediante i comandi le stesse operazioni che generalmente vengono effettuate dall'utente.  Quando ad esempio si chiama il metodo `Fill` dell'adattatore, quest'ultimo esegue il comando dati nella relativa proprietà `SelectCommand` e utilizza un lettore di dati, ad esempio, <xref:System.Data.SqlClient.SqlDataReader>, per caricare il set dei risultati nella tabella dati.  Allo stesso modo, quando si chiama il metodo `Update` dell'adattatore, verrà eseguito il comando appropriato \(nelle proprietà `UpdateCommand`, `InsertCommand` e `DeleteCommand`\) per ciascun record modificato nella tabella dati.  
  
> [!NOTE]
>  Se la query principale contiene una quantità di informazioni sufficiente, i comandi `InsertCommand`, `UpdateCommand` e `DeleteCommand` vengono creati per impostazione predefinita durante la generazione dell'oggetto TableAdapter.  Se la query principale di TableAdapter non è solo un'istruzione SELECT di una singola tabella, è possibile che nella finestra di progettazione non vengano generati i comandi `InsertCommand`, `UpdateCommand` e `DeleteCommand`.  In tal caso, potrebbe essere visualizzato un errore durante l'esecuzione del metodo `TableAdapter.Update`.  
  
## Proprietà GenerateDbDirectMethods dei TableAdapter  
 Oltre a `InsertCommand`, `UpdateCommand` e `DeleteCommand`, gli oggetti TableAdapter vengono creati con metodi che è possibile eseguire direttamente nel database.  Tali metodi \(`TableAdapter.Insert`, `TableAdapter.Update` e `TableAdapter.Delete`\) possono essere chiamati direttamente per la modifica dei dati nel database.  Ciò significa che è possibile chiamare questi metodi singoli dal codice anziché TableAdapter.Update per gestire inserimenti, aggiornamenti ed eliminazioni in sospeso per la tabella dati associata.  
  
 Se non si desidera creare questi metodi diretti, impostare la proprietà **GenerateDbDirectMethods** dell'oggetto TableAdapter su `false` nella finestra **Proprietà**.  Le altre query che vengono aggiunte all'oggetto TableAdapter sono autonome, ovvero non generano tali metodi.  
  
## Supporto dei TableAdapter per i tipi nullable  
 Gli oggetti TableAdapter supportano i tipi nullable `Nullable(Of T)` e `T?`.  Per ulteriori informazioni sui tipi nullable in Visual Basic, vedere [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).  Per ulteriori informazioni sui tipi nullable in C\#, vedere [Utilizzo dei tipi nullable](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Procedura dettagliata: connessione ai dati in un database \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)