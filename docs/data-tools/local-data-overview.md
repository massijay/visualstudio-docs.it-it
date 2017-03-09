---
title: "Cenni preliminari sui dati locali | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "Access, .file mdb in Visual Studio"
  - "dati [Visual Studio], locali"
  - "accesso ai dati [Visual Studio], risoluzione dei problemi"
  - "dati locali"
  - "LocalDB"
  - "SQL Express"
  - "SQL Server Compact"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQL Server, dati locali"
  - "SQLEXPRESS"
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
caps.handback.revision: 66
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Cenni preliminari sui dati locali
Quando si utilizzano i dati locali, si connette l'applicazione a un file di database nel computer locale, anziché a un database in un server separato.  Ad esempio, è possibile connettere un'applicazione sviluppata in Visual Studio ai seguenti file di database locali:  
  
-   File di database LocalDB di SQL Server Express \(.mdf\).  
  
-   File di database SQL Server Express \(.mdf\)  
  
-   File di database di Microsoft Access \(.mdb\)  
  
 Nella tabella seguente sono forniti i collegamenti agli argomenti che descrivono come connettere l'applicazione ai dati locali:  
  
|Argomento|Descrizione|  
|---------------|-----------------|  
|[Procedura dettagliata: creazione di un file di database locale in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md)|Vengono fornite istruzioni dettagliate per la creazione di un file di database locale che può essere utilizzato per verificare le funzionalità dei dati e la compilazione di applicazioni.|  
|[Procedura dettagliata: connessione ai dati in un file di database lodale \(Windows Form\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Vengono fornite istruzioni dettagliate per la connessione a un database LocalDB di SQL Server Express durante la creazione di una semplice applicazione per Windows.|  
|[Procedura dettagliata: connessione ai dati in un database di Access \(Windows Form\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Vengono fornite istruzioni dettagliate per la connessione a un database di Microsoft Access.|  
|[Procedura dettagliata: connettersi al database Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Vengono fornite istruzioni per la connessione al database di esempio Northwind [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)], SQL Server Compact, SQL Server Express e Access.|  
  
 Una volta creata un'origine dati e averla configurata per accedere a un file di dati locale, è possibile operare con i dati utilizzando le stesse tecnologie e oggetti utilizzati quando si opera con dati provenienti di un'altra origine.  Per ulteriori informazioni, vedere [Creazione di applicazioni dati](../data-tools/creating-data-applications.md).  
  
## Integrazione del database nell'applicazione  
 Connettendosi ai dati locali, sarà possibile non solo connettersi a un file di database, ma anche integrarlo nell'applicazione in uso.  Ad esempio, è possibile aprire il menu **Progetto**, individuare un file con estensione sdf, mdf o mdb esistente e aggiungerlo al progetto.  
  
 Se si aggiungono file di dati locali, si crea un dataset tipizzato e una stringa di connessione dinamica che punta al file di database dell'applicazione.  Quando si aggiunge un file di un database al progetto, per specificare gli oggetti da includere viene utilizzata la **Configurazione guidata origine dati**.  
  
> [!NOTE]
>  È possibile configurare automaticamente la propria connessione e avviare la **Configurazione guidata origine dati** trascinando un file sdf, mdf o mdb da Esplora file in **Esplora soluzioni**.  È quindi ora possibile specificare gli oggetti da utilizzare nell'applicazione.  
  
 Se si utilizza **Configurazione guidata origine dati** per creare l'origine dati per un file di dati locali, verrà richiesto se si desidera includere il file nel progetto.  Se non lo si include, nell'applicazione sarà contenuta soltanto la stringa di connessione a cui punta il percorso hardcoded e non il file di dati effettivo.  Per ulteriori informazioni, vedere [Procedura: gestire file di dati locali nel progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
 Dopo aver completato la configurazione guidata, il file di database e il dataset vengono visualizzati in **Esplora soluzioni**\/**Esplora database** e gli oggetti di database specificati appaiono nella finestra **Origini dati**.  Trascinando gli elementi dalla finestra **Origini dati** al form, è possibile creare controlli associati ai dati sottostanti.  Per aprire la finestra**Origini dati**, aprire il menu **Dati**, quindi scegliere **Mostra origini dati**.  Per ulteriori informazioni, vedere [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Utilizzo di un file di database  
 Prima di poter utilizzare un file di database esistente \(mdf\) in Visual Studio, è probabile che sia necessario convertire il file in un file di database di [!INCLUDE[sql_Denali_short](../data-tools/includes/sql_denali_short_md.md)].  Quando ci si connette a un file di database esistente, una finestra di messaggio chiede se si desidera eseguire l'aggiornamento.  
  
> [!IMPORTANT]
>  Se si aggiorna il file di database \(con estensione mdf\), non sarà possibile aprirlo in una versione precedente di SQL Server.  
  
 Non è necessario convertire il file di database \(con estensione mdf\) se il valore di **Nome istanza di SQL Server** è impostato su SQLEXPRESS e se SQL Server 2008 Express è installato.  SQL Server 2008 Express viene installato se Visual Studio 2010 è installato.  Per modificare il nome dell'istanza per questo file di database, aprire Visual Studio, aprire la finestra di dialogo **Aggiungi connessione**, specificare `.\SQLEXPRESS` come nome del server, quindi specificare il database o il nome file del database.  
  
## LocalDB di SQL Server Express e SQL Server Express  
 È possibile aggiungere un file di database basato su servizi \(mdf\) a qualsiasi progetto in Visual Studio.  È possibile utilizzare le finestre di progettazione di Visual Studio per la progettazione di tabelle e altri oggetti di database ed è possibile eseguire query.  
  
 Quando si crea un database basato su servizi in Visual Studio, questo utilizza il motore LocalDB di SQL Server Express per accedere al file di database \(mdf\) mentre le versioni precedenti di Visual Studio utilizzano il motore di SQL Server Express.  
  
 LocalDB di SQL Server Express è una versione semplificata di SQL Server che è possibile programmare in molti dei modi in cui è possibile programmare un database di SQL Server.  LocalDB di SQL Server Express viene eseguito in modalità utente ed è possibile installarlo più rapidamente con meno prerequisiti e nessuna configurazione.  
  
> [!NOTE]
>  Per ulteriori informazioni su LocalDB di SQL Server Express, vedere le pagine relative all'[introduzione a LocalDB, un SQL Express migliore](http://go.microsoft.com/fwlink/?LinkId=234375) e a [LocalDB: Dov'è il database?](http://go.microsoft.com/fwlink/?LinkId=234376) sul sito Web Microsoft.  
  
 In Visual Studio è possibile utilizzare SQL Server Express per impostazione predefinita invece del database locale di SQL Server Express.  Sulla barra dei menu, scegliere **Strumenti**, **Opzioni**.  Nel nodo **Strumenti di database** scegliere **Connessioni dati**.  Nella casella di testo **Nome istanza di SQL Server** immettere `SQLEXPRESS`.  In alternativa, è possibile immettere altri valori per il nome dell'istanza di SQL Server, ad esempio `SQL2008`.  
  
 Nella tabella seguente vengono descritte le differenze tra i motori di SQL Server Express LocalDB e di SQL Server Express.  
  
||LocalDB di SQL Server Express|SQL Server Express|  
|-|-----------------------------------|------------------------|  
|Tipo di database quando si crea un database basato su servizi|In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] e [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], LocalDB di SQL Server Express|In Visual Studio 2010 e versioni precedenti, SQL Server Express|  
|Nome dell'istanza di SQL Server in Strumenti\/Opzioni|\(LocalDB\)\\v11.0|SQLEXPRESS|  
|Valore dell'origine dati nella stringa di connessione|\(LocalDB\)\\v11.0|.\\SQLEXPRESS|  
|Valore di AttachDbFilename nella stringa di connessione|percorso file|percorso file|  
|L'istanza utente è obbligatoria \("User Instance\=True" nella stringa di connessione\)|No|Sì|  
|Estensione del file di database|MDF|MDF|  
  
## Vantaggi di LocalDB di SQL Server Express  
  
-   LocalDB di SQL Server Express è compatibile con le edizioni basate su servizi di SQL Server per le funzionalità disponibili.  In SQL Server, è possibile spostare qualsiasi database o il codice Transact\-SQL da LocalDB di SQL Server Express a SQL Server o SQL Azure senza alcun passaggio di aggiornamento.  Pertanto, è possibile utilizzare LocalDB di SQL Server Express per sviluppare applicazioni destinate a tutte le versioni di SQL Server.  
  
-   LocalDB di SQL Server Express supporta le stesse utilità Query Optimizer e Query Processor delle versioni superiori di SQL Server.  
  
## Ciascun progetto contiene due copie del database  
 Quando si compila un progetto, il file di database può essere copiato dalla cartella del progetto radice nella cartella di output \(**bin**\).  Questo comportamento dipende dalla proprietà **Copia in directory di output** del file e il valore predefinito di tale proprietà dipende dal tipo di file di database in uso.  
  
 Per visualizzare la cartella **bin** in **Esplora soluzioni**, fare clic sul pulsante **Mostra tutti i file** sulla barra degli strumenti.  
  
> [!NOTE]
>  La proprietà **Copia nella directory di output** non riguarda i progetti Web o i progetti C\+\+.  
  
 Il file di database nella cartella radice del progetto viene modificato solo in caso di modifica dello schema o dei dati del database tramite **Esplora server**\/**Esplora database** o [Visual Database Tools](http://msdn.microsoft.com/it-it/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Mentre si modificano i dati durante lo sviluppo di applicazioni, il database nella cartella **bin** viene modificato.  Se, ad esempio, si preme il tasto F5 per eseguire il debug dell'applicazione, si verrà connessi al database nella cartella.  
  
|Valore della proprietà **Copia nella directory di output**|Comportamento|  
|----------------------------------------------------------------|-------------------|  
|**Copia se più recente** \(valore predefinito per i file sdf\)|Il file di database viene copiato dalla directory del progetto alla directory **bin** alla prima compilazione del progetto.  La proprietà **Data ultima modifica** dei file viene confrontata a ogni successiva compilazione del progetto.  Se il file contenuto nella cartella di progetto è il più recente, viene copiato nella cartella **bin** e sostituisce il file precedente.  In caso contrario, non viene copiato alcun file. **Caution:**  Questo valore non è consigliabile per i file mdb o mdf.  Il file di database può essere modificato anche se i dati non cambiano.  Il file può essere contrassegnato come più recente semplicemente aprendo una connessione \(ad esempio, espandendo il nodo **Tabelle** in **Esplora server**\).|  
|**Copia sempre** \(valore predefinito per i file mdf e mdb\)|Il file di database viene copiato dalla directory del progetto alla directory **bin** a ogni compilazione dell'applicazione.  Tutte le modifiche apportate al file di dati nella cartella di output vengono sovrascritte durante la successiva esecuzione dell'applicazione.|  
|**Non copiare**|Il file nella directory **bin** non viene mai sovrascritto dal sistema.  L'applicazione crea una stringa di connessione dinamica che punta al file di database nella directory di output.  Pertanto, è necessario copiare manualmente il file nella directory di output se si desidera che i dati nella directory di output corrispondano ai dati nella directory del progetto.|  
  
## Problemi comuni dei dati locali  
 Nella tabella riportata di seguito sono fornite spiegazioni sui problemi comuni che potrebbero verificarsi quando si utilizzano file di dati locali.  
  
|Problema|Descrizione|  
|--------------|-----------------|  
|Ogni volta che viene eseguito il test dell'applicazione e vengono modificati i dati, le modifiche vengono perse quando si esegue nuovamente l'applicazione.|Il valore della proprietà **Copia nella directory di output** è impostato su **Copia se più recente** oppure su **Copia sempre**.  Il database della cartella di output verrà sovrascritto \(il database che è stato modificato durante il test dell'applicazione\) tutte le volte che si compila un progetto.  Per ulteriori informazioni, vedere [Procedura: gestire file di dati locali nel progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Viene visualizzato un messaggio che indica che il file di dati è bloccato.|Access \(file mdb\): verificare che il file non sia aperto in un altro programma, ad esempio Access.<br /><br /> SQL Server Express \(file mdf\): in SQL Express il file di dati viene bloccato se si tenta di copiare, spostare o rinominare lo stesso file di dati all'esterno dell'IDE di Visual Studio.|  
|L'accesso viene negato se il tentativo di accesso allo stesso database viene effettuato da più utenti contemporaneamente.|Visual Studio sfrutta la capacità di *istanze utente*, una funzionalità di SQL Server Express, in cui viene creata un'istanza separata di un server SQL per ogni utente.  Dopo che un utente ha eseguito l'accesso al file, nessun utente successivo sarà in grado di effettuare la connessione.  Questo problema può verificarsi se, ad esempio, si tenta di eseguire un'applicazione Web in ASP.NET Development Server e IIS \(Internet Information Service\) contemporaneamente, dal momento che IIS in genere viene eseguito con un diverso account.|  
  
## Vedere anche  
 [Procedura dettagliata: connessione ai dati in un file di database lodale \(Windows Form\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Procedura dettagliata: connessione ai dati in un database di Access \(Windows Form\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)