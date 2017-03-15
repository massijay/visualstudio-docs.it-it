---
title: "Inserimento di dati nei dataset | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "dati [Visual Studio], dataset"
  - "dati [Visual Studio], recupero"
  - "recupero dei dati"
  - "dataset [Visual Basic]"
  - "dataset [Visual Basic], riempimento"
  - "dataset [Visual Basic], caricamento di dati"
  - "recupero dei dati"
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 32
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Inserimento di dati nei dataset
Il meccanismo utilizzato generalmente in Visual Studio per l'esecuzione di query Transact\-SQL e per la compilazione dei dataset è il TableAdapter.  
  
 È possibile eseguire istruzioni SQL o stored procedure in un'origine dati utilizzando oggetti TableAdapter o oggetti di comando, ad esempio <xref:System.Data.SqlClient.SqlCommand>.  Per caricare i dati in dataset creati mediante gli strumenti di progettazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], utilizzare i TableAdapter.   Per caricare i dati in dataset creati a livello di codice, si utilizzano gli adattatori dati.  Se nell'applicazione non vengono utilizzati i dataset, usare gli oggetti comando per eseguire le istruzioni SQL o le stored procedure direttamente in un database.  
  
 Negli argomenti seguenti vengono forniti i dettagli per inserire dati nei dataset in Visual Studio:  
  
|Argomento|Descrizione|  
|---------------|-----------------|  
|[Procedura: riempire un dataset](../data-tools/how-to-fill-a-dataset-with-data.md)|Vengono fornite informazioni dettagliate sul caricamento dei dati nei dataset mediante TableAdapter e DataAdapter.|  
|[Procedura: creare ed eseguire un'istruzione SQL che restituisce righe](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)|Vengono illustrate in dettaglio la creazione e l'esecuzione di istruzioni SQL che restituiscono righe mediante query TableAdapter e oggetti comando.|  
|[Procedura: creare ed eseguire un'istruzione SQL che restituisce un valore](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)|Vengono fornite informazioni dettagliate sulla creazione e l'esecuzione di istruzioni SQL che restituiscono valori singoli mediante query TableAdapter e oggetti comando.|  
|[Procedura: creare ed eseguire un'istruzione SQL che non restituisce valori](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)|Vengono fornite informazioni dettagliate sulla creazione e l'esecuzione di istruzioni SQL che non restituiscono alcun valore mediante query TableAdapter e oggetti comando.|  
|[Procedura: eseguire una stored procedure che restituisce righe](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)|Viene illustrata in dettaglio l'esecuzione di stored procedure che restituiscono righe mediante query TableAdapter e oggetti comando.|  
|[Procedura: eseguire una stored procedure che restituisce un valore singolo](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)|Viene illustrata in dettaglio l'esecuzione di stored procedure che restituiscono singoli valori mediante query TableAdapter e oggetti comando.|  
|[Procedura: eseguire una stored procedure che non restituisce valori](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)|Vengono fornite informazioni dettagliate sull'esecuzione di stored procedure che non restituiscono valori mediante query TableAdapter e oggetti comando.|  
|[Procedura: ottenere e impostare parametri per oggetti comando](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)|Vengono forniti dettagli sull'assegnazione di valori ai parametri di query e stored procedure e sulla lettura dei valori dei parametri restituiti dai comandi eseguiti.|  
|[Procedura dettagliata: riempimento di un dataset](../Topic/Walkthrough:%20Filling%20a%20Dataset%20with%20Data.md)|Vengono fornite istruzioni dettagliate per la creazione di un dataset e il suo popolamento con i dati di un database.|  
|[Procedura dettagliata: lettura dei dati XML in un dataset](../data-tools/read-xml-data-into-a-dataset.md)|Vengono fornite informazioni dettagliate sulla creazione di un'applicazione Windows che consenta il caricamento dei dati XML in un dataset e la successiva visualizzazione del dataset in un controllo <xref:System.Windows.Forms.DataGridView>.|  
  
## Riempimento di dataset  
 Se si crea un dataset con uno strumento di progettazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], come [Progettazione DataSet](../data-tools/creating-and-editing-typed-datasets.md) o la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png), utilizzare un TableAdapter per compilarlo.   I TableAdapter consentono di eseguire le istruzioni SQL o le stored procedure.  
  
 Se si crea un dataset senza gli strumenti di progettazione, è necessario utilizzare gli adattatori dati per riempire e aggiornare i dati.  Gli oggetti TableAdapter non sono classi vere e proprie in [.NET Framework 4.6 e 4.5](../Topic/.NET%20Framework%204.6%20and%204.5.md), di conseguenza non sono idonei ad essere utilizzati con dataset creati senza utilizzare strumenti di progettazione.  Per ulteriori informazioni sul caricamento dei dati nei dataset utilizzando TableAdapter o adattatori dati, vedere [Procedura: riempire un dataset](../data-tools/how-to-fill-a-dataset-with-data.md).  
  
## Query TableAdapter  
 È possibile eseguire query TableAdapter per riempire di dati i dataset e, in maniera più specifica, per caricare i dati nelle DataTable che costituiscono un dataset.  È possibile creare query TableAdapter utilizzando la [TableAdapter \(query, configurazione guidata\)](../data-tools/editing-tableadapters.md) in **Progettazione DataSet**.  Le query TableAdapter vengono visualizzate come metodi denominati su un TableAdapter e vengono eseguite chiamando il metodo TableAdapter.  Per ulteriori informazioni sulla creazione e l'esecuzione di query TableAdapter, vedere le pagine seguenti:  
  
-   [Procedura: creare ed eseguire un'istruzione SQL che restituisce righe](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)  
  
-   [Procedura: creare ed eseguire un'istruzione SQL che restituisce un valore](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)  
  
-   [Procedura: creare ed eseguire un'istruzione SQL che non restituisce valori](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)  
  
-   [Procedura: eseguire una stored procedure che restituisce righe](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)  
  
-   [Procedura: eseguire una stored procedure che restituisce un valore singolo](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)  
  
-   [Procedura: eseguire una stored procedure che non restituisce valori](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)  
  
## Oggetti comando  
 Gli oggetti comando consentono di eseguire istruzioni SQL e stored procedure direttamente in un database, senza ricorrere a <xref:System.Data.DataSet>, TableAdapter o <xref:System.Data.Common.DataAdapter>.  Il termine *oggetto comando* si riferisce al comando specifico per il Provider di dati .NET Framework utilizzato dall'applicazione.  Se, ad esempio, è in uso il Provider di dati .NET Framework per SQL Server, l'oggetto comando sarà <xref:System.Data.SqlClient.SqlCommand>.  
  
 È possibile configurare i comandi per eseguire query sui dati mediante istruzioni SQL o stored procedure impostando la proprietà `CommandType` del comando dati su uno dei valori dell'enumerazione <xref:System.Data.IDbCommand.CommandType%2A>.  Impostare `CommandType` su <xref:System.Data.CommandType> per l'esecuzione di istruzioni SQL oppure impostarlo su <xref:System.Data.CommandType> per l'esecuzione di stored procedure.  Successivamente, impostare la proprietà `CommandText` su un'istruzione SQL o sul nome della stored procedure.  Per eseguire il comando dati, effettuare quindi la chiamata a uno dei relativi metodi Execute \(`ExecuteReader`, `ExecuteScalar`, `ExecuteNonQuery`\).  
  
 Ciascuno dei [Provider di dati .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md) offre un oggetto comando ottimizzato per database specifici.  
  
 I comandi dati consentono di effettuare le seguenti operazioni nell'applicazione:  
  
-   Esecuzione di comandi Select che restituiscono un risultato leggibile dall'utente in modo diretto, senza doverlo caricare nel dataset.  Per leggere i risultati è possibile ricorrere a un lettore dati \(oggetto <xref:System.Data.OleDb.OleDbDataReader>, <xref:System.Data.SqlClient.SqlDataReader>, <xref:System.Data.Odbc.OdbcDataReader> o <xref:System.Data.OracleClient.OracleDataReader>\), il cui funzionamento è analogo a quello di un cursore di tipo forward only di sola lettura al quale possono essere associati i controlli.  Si tratta di un'efficace strategia per contenere l'utilizzo di memoria e caricare in modo rapido dati in sola lettura.  
  
-   Esecuzione di comandi DDL per creare, modificare e rimuovere tabelle, stored procedure e altre strutture del database.  Per eseguire queste operazioni è tuttavia necessario disporre delle autorizzazioni appropriate.  
  
-   Esecuzione di comandi per ottenere le informazioni sul catalogo del database.  
  
-   Esecuzione di comandi SQL dinamici per aggiornare, inserire o eliminare record, anziché aggiornare tabelle dataset e copiare quindi le modifiche nel database.  
  
-   Esecuzione di comandi che restituiscono un valore scalare, ovvero un valore singolo, quali i risultati di una funzione aggregata \(SUM, COUNT, AVG e così via\).  
  
-   Esecuzione di comandi che restituiscono dati da un database di SQL Server \(versione 7.0 o successiva\) in formato XML.  Un tipico utilizzo di questi comandi consiste nell'eseguire una query e ottenere i dati in formato XML, applicare ai dati una trasformazione XSLT per convertirli in formato HTML, quindi inviare i risultati a un browser.  
  
 Nelle proprietà di un comando sono presenti tutte le informazioni necessarie a eseguire un comando in un database,  vale a dire:  
  
-   **Una connessione** Il comando fa riferimento a una connessione utilizzata per comunicare con il database.  
  
-   **Il nome o il testo di un comando** Nel comando è incluso il testo effettivo di un'istruzione SQL o il nome di una stored procedure da eseguire.  
  
-   **I parametri** Potrebbe essere necessario passare insieme al comando i valori dei relativi parametri \(parametri di input\).  Il comando potrebbe anche restituire valori sotto forma di valore restituito oppure di valori dei parametri di output.  In ciascun comando è disponibile una raccolta di parametri che possono essere impostati o letti singolarmente per passare o per ricevere i valori.  Per ulteriori informazioni, vedere [Procedura: ottenere e impostare parametri per oggetti comando](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Per eseguire un comando è necessario scegliere un metodo in base al risultato che si desidera ottenere.  Se, ad esempio, si prevede di ottenere delle righe, sarà necessario chiamare il metodo `ExecuteReader` del comando che restituisce i record di un lettore dati.  Se si esegue un comando UPDATE, INSERT o DELETE, sarà necessario chiamare il metodo `ExecuteNonQuery` del comando che restituisce un valore che indica il numero di righe interessate.  Per eseguire una funzione di aggregazione, ad esempio restituire il conteggio degli ordini di un cliente, viene chiamato il metodo `ExecuteScalar`.  
  
### Più set di risultati  
 Un utilizzo tipico dell'oggetto comando prevede la restituzione di una tabella di dati \(un set di righe\).  Tuttavia, i comandi possono anche consentire l'esecuzione di routine che restituiscono più set di risultati  in svariati modi.  Uno dei modi prevede che nel comando venga inserito un riferimento a una stored procedure che restituisce più set di risultati  ma, in alternativa, nel comando possono essere presenti due o più istruzioni o stored procedure.  In tal caso le istruzioni o le stored procedure verranno eseguite in sequenza e con una singola chiamata verranno restituiti più set di risultati.  
  
 Se per un comando si specificano più istruzioni o stored procedure, è necessario che siano tutte dello stesso tipo.  È possibile, ad esempio, eseguire istruzioni SQL o stored procedure consecutive  mentre non è possibile combinare chiamate a stored procedure e istruzioni SQL nello stesso comando.  Per ulteriori informazioni, vedere [Recupero di dati mediante un DataReader](../Topic/Retrieving%20Data%20Using%20a%20DataReader.md).  
  
> [!NOTE]
>  Per Oracle il provider di dati .NET Framework non supporta le istruzioni SQL in batch.  Consente, tuttavia, di utilizzare più parametri di output REF CURSOR per riempire un dataset, ciascuno nella propria tabella dati.  È necessario definire i parametri, contrassegnarli come parametri di output e indicare che si tratta di tipi di dati REF CURSOR.  Si tenga presente che non sarà possibile utilizzare il metodo `Update` quando l'oggetto <xref:System.Data.OracleClient.OracleDataAdapter> viene riempito con parametri REF CURSOR per una stored procedure, in quanto in Oracle non vengono fornite le informazioni necessarie per determinare quali devono essere il nome della tabella e i nomi delle colonne al momento dell'esecuzione dell'istruzione SQL.  
  
## Sicurezza  
 Quando si utilizzano comandi dati con una proprietà `CommandType` impostata su <xref:System.Data.CommandType>, controllare attentamente le informazioni inviate da un client prima di passarle al database.  Utenti malintenzionati potrebbero tentare di inviare istruzioni SQL modificate o aggiuntive con l'obiettivo di ottenere un accesso non autorizzato o di danneggiare il database.  Prima di trasferire l'input di un utente in un database, si consiglia di verificare sempre che le informazioni siano valide.  È opportuno utilizzare, quando possibile, query con parametri o stored procedure.  
  
## Vedere anche  
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)   
 [Strumenti per l'utilizzo delle origini dati in Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)