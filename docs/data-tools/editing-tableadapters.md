---
title: "TableAdapter (query, configurazione guidata) | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.dbtablefunctionwizard"
  - "vs.datasource.datacomponentquerywizard"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], query di componente dati"
  - "dati [Visual Studio], query di adattatore tabelle"
  - "dati [Visual Studio], TableAdapters"
  - "TableAdapter (query, configurazione guidata)"
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# TableAdapter (query, configurazione guidata)
La **Configurazione guidata query TableAdapter** consente di creare e modificare le ulteriori query che è possibile aggiungere agli oggetti TableAdapter.  Una query TableAdapter è una qualsiasi query SQL o stored procedure valida che restituisce dati conformi allo schema della tabella dati associata dell'oggetto TableAdapter o che restituisce un valore scalare.  Al termine della procedura guidata, all'oggetto TableAdapter verrà aggiunto un metodo chiamando il quale verrà eseguita la query,  ad esempio `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.  
  
## Esecuzione della procedura guidata  
 Trascinare le query in **Progettazione DataSet** oppure configurare quelle esistenti, ovvero quelle elencate al di sotto della prima query.  
  
 La prima query in un oggetto TableAdapter è la query TableAdapter principale.  Modificando questa query viene aperta la **Configurazione guidata query TableAdapter** e viene modificato lo schema della tabella dati dell'oggetto TableAdapter.  Tutte le query elencate al di sotto di quella principale sono query aggiuntive e vengono configurate usando la **Configurazione guidata query TableAdapter**.  Per altre informazioni sull'esecuzione della procedura guidata, vedere [Procedura: avviare la Configurazione guidata query TableAdapter](../Topic/How%20to:%20Start%20the%20TableAdapter%20Query%20Configuration%20Wizard.md).  
  
## Selezione della connessione dati  
 Scegliere una connessione esistente nell'elenco di connessioni disponibili oppure fare clic su **Nuova connessione** per creare una connessione al database.  
  
 Dopo aver compilato la finestra di dialogo **Proprietà connessione**, nell'area **Dettagli connessione** vengono visualizzate informazioni di sola lettura sul provider selezionato oltre alla stringa di connessione.  
  
## Salvataggio della stringa di connessione nel file di configurazione dell'applicazione  
 Scegliere **Sì, salva la connessione con nome** per archiviare la stringa di connessione nel file di configurazione dell'applicazione.  Digitare un nome per la connessione oppure usare il nome predefinito.  
  
 Salvando le stringhe di connessione nel file di configurazione dell'applicazione, è possibile semplificare il processo di gestione dell'applicazione se la connessione di database cambia.  Se la connessione al database viene modificata, è possibile modificare la stringa di connessione nel file di configurazione dell'applicazione.  In questo modo non sarà necessario modificare il codice sorgente e ricompilare l'applicazione.  Per informazioni su come modificare una stringa di connessione nel file di configurazione dell'applicazione, vedere [Procedura: salvare e modificare stringhe di connessione](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
> [!IMPORTANT]
>  Le informazioni vengono archiviate nel file di configurazione dell'applicazione come testo normale.  Per ridurre la possibilità di un accesso non autorizzato a informazioni riservate, è possibile crittografare i dati.  Per altre informazioni, vedere [Encrypting and Decrypting Data](http://msdn.microsoft.com/it-it/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## Usa istruzioni SQL  
 Questa sezione descrive come completare la **Configurazione guidata query TableAdapter** quando si seleziona l'opzione **Usa istruzioni SQL**.  
  
## Scegli tipo di query  
 La procedura guidata consente di creare diversi tipi di query in base ai requisiti dell'applicazione.  È possibile scegliere query SELECT che restituiscono righe di dati \(una tabella dati\) o query SELECT che restituiscono un valore scalare \(un singolo valore come `Count` o `Sum`\).  
  
 Nella pagina **Scegli tipo di query** selezionare il tipo di query da creare nell'elenco di query disponibili.  
  
> [!NOTE]
>  La creazione di un'istruzione INSERT, UPDATE o DELETE non comporta la sostituzione dei comandi dell'oggetto TableAdapter usati quando si chiama il relativo metodo `Update`.  Se ad esempio si seleziona il tipo di query UPDATE, verrà creata una nuova query con un nome specificato successivamente nella procedura guidata.  Per eseguire la query è necessario chiamare questo metodo denominato dell'oggetto TableAdapter.  Chiamando il metodo `Update` dell'oggetto TableAdapter verranno eseguite le istruzioni create al momento della configurazione dell'oggetto originale.  
  
## Specifica un'istruzione SQL \<Tipo Query\>  
 Nella pagina **Specifica un'istruzione SQL** digitare l'istruzione SQL da eseguire per la chiamata della query.  
  
> [!TIP]
>  La procedura guidata consente di accedere al **Generatore di query**, uno strumento visivo per la creazione di query SQL.  Per aprirlo, fare clic sul pulsante **Generatore di query**.  
  
## Scegliere i metodi per generare  
 Questa pagina contiene le opzioni per la selezione dei metodi da generare per la query mediante la procedura guidata.  
  
 **Riempi un DataTable**  
 Crea un metodo per il riempimento della tabella dati.  Quando si chiama questo metodo per riempire la tabella dati con i dati restituiti, il nome della tabella viene passato come parametro.  
  
 È anche possibile modificare il nome predefinito nella casella **Nome metodo**.  Specificare un nome significativo può risultare utile quando la query viene usata in una stringa di codice.  
  
 **Restituisci un DataTable**  
 Crea un metodo per la restituzione di una tabella dati popolata.  In alcune applicazioni è preferibile restituire una tabella dati compilata invece di riempire con dati la tabella dati esistente.  
  
 È anche possibile modificare il nome predefinito nella casella **Nome metodo**.  
  
## Scegli il nome della funzione  
 Digitare un nome per la funzione.  La creazione di una query TableAdapter comporta l'aggiunta all'oggetto TableAdapter di un metodo con il nome specificato.  Chiamare questo metodo per eseguire la query.  Specificare un nome significativo è utile quando la query viene usata in una stringa di codice.  
  
> [!NOTE]
>  Durante la creazione di nuove stored procedure, viene richiesto di immettere due nomi.  Il primo è il nome della stored procedure creata nel database, il secondo è il nome del metodo dell'oggetto TableAdapter che esegue la stored procedure quando viene chiamato.  
  
## Creare nuove stored procedure  
 Questa sezione descrive come completare la **Configurazione guidata query TableAdapter** quando si seleziona l'opzione **Crea nuove stored procedure**.  
  
1.  Nella pagina **Genera le stored procedure** digitare l'istruzione SQL da eseguire quando viene chiamata la stored procedure.  
  
    > [!NOTE]
    >  La procedura guidata consente di accedere al **Generatore di query**, uno strumento visivo per la creazione di query SQL.  Per aprirlo, fare clic sul pulsante **Generatore di query**.  
  
2.  Nella pagina **Crea le stored procedure** eseguire le operazioni seguenti:  
  
    1.  Digitare un nome per la nuova stored procedure.  
  
    2.  Specificare se creare la stored procedure nel database sottostante.  
  
        > [!NOTE]
        >  La possibilità di creare una stored procedure nel database dipende dalle impostazioni di sicurezza dello specifico database.  
  
     La pagina **Risultati procedura guidata** mostra i risultati della creazione della query TableAdapter.  Se nel corso della procedura si verificano problemi, in questa pagina vengono visualizzate le informazioni sugli errori.  
  
## Usa stored procedure esistenti  
 Questa sezione descrive come completare la **Configurazione guidata query TableAdapter** quando si seleziona l'opzione **Usa stored procedure esistenti**.  
  
1.  Selezionare una stored procedure esistente dall'elenco a discesa nella pagina **Selezionare una stored procedure esistente** della procedura guidata.  
  
     I **Parametri** e i **Risultati** relativi alla stored procedure selezionata vengono visualizzati per riferimento.  
  
2.  Scegliere **Avanti**.  
  
## Scegliere la forma dei dati restituiti dalla stored procedure  
 Il tipo di dati restituiti dalla stored procedure selezionata determina la modalità di creazione dei metodi dell'oggetto TableAdapter mediante la procedura guidata.  
  
 Selezionare il tipo di dati restituiti da questa query.  
  
-   Selezionando **Dati tabulari** verrà aperta la pagina **Scegliere i metodi da generare** descritta in una sezione precedente di questa pagina della Guida, in cui è possibile specificare i tipi di metodi, i nomi di metodo e il supporto per lo spostamento.  
  
-   Selezionando **Un valore** verrà creato un metodo tipizzato che restituisce un singolo valore.  Verrà inoltre aperta la pagina **Scegli il nome della funzione**, descritta in precedenza in questa pagina della Guida.  
  
-   Selezionando **Nessun valore** verrà creato un metodo tipizzato che esegue la stored procedure senza restituire dati.  Verrà inoltre aperta la pagina **Scegli il nome della funzione**, descritta in precedenza in questa pagina della Guida.  
  
## Risultati procedura guidata  
 La pagina **Risultati procedura guidata** mostra i risultati della creazione della query TableAdapter.  Se nel corso della procedura si verificano problemi, in questa pagina vengono visualizzate le relative informazioni.  
  
## Vedere anche  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)