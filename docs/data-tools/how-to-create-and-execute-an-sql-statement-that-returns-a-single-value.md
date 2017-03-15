---
title: "Procedura: creare ed eseguire un&#39;istruzione SQL che restituisce un valore | Microsoft Docs"
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
  - "comandi di dati, restituzione di valori scalari"
  - "visualizzatore dati"
  - "DataReader (oggetto)"
  - "valori scalari"
  - "SQL (istruzioni), comandi di dati"
  - "stored procedure, restituzione di un valore singolo"
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: creare ed eseguire un&#39;istruzione SQL che restituisce un valore
Per eseguire un'istruzione SQL che restituisca un singolo valore, è possibile utilizzare una query TableAdapter configurata in modo da eseguire un'istruzione SQL, come ad esempio `CustomersTableAdapter.CustomerCount()`.  
  
 Se nell'applicazione non vengono utilizzati TableAdapter, chiamare il metodo `ExecuteScalar` su un oggetto comando, impostando la relativa proprietà `CommandType` su <xref:System.Data.CommandType>.  Per oggetto comando si intende il comando specifico del [Provider di dati .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md) utilizzato dall'applicazione.  Se, ad esempio, è in uso il Provider di dati .NET Framework per SQL Server, l'oggetto comando sarà <xref:System.Data.SqlClient.SqlCommand>.  
  
 Negli esempi che seguono viene illustrato come eseguire istruzioni SQL che restituiscono singoli valori da un database utilizzando TableAdapter oppure oggetti comando.  Per ulteriori informazioni sull'esecuzione di query con TableAdapter e comandi, vedere [Inserimento di dati nei dataset](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Esecuzione di istruzioni SQL che restituiscono singoli valori utilizzando un TableAdapter  
 Nell'esempio che segue viene illustrato come creare una query TableAdapter utilizzando la [TableAdapter \(query, configurazione guidata\)](../data-tools/editing-tableadapters.md), quindi vengono fornite informazioni su come dichiarare un'istanza di TableAdapter ed eseguire la query.  
  
#### Per creare un'istruzione SQL che restituisce un valore utilizzando un TableAdapter  
  
1.  Aprire un dataset in **Progettazione DataSet**.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Se non è già disponibile un TableAdapter, crearne uno.  Per ulteriori informazioni sulla creazione di TableAdapter, vedere [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Se esiste già una query su un determinato TableAdapter che utilizza un'istruzione SQL per la restituzione di un singolo valore, passare direttamente alla procedura successiva "Per dichiarare un'istanza del TableAdapter ed eseguire la query". In caso contrario, procedere con il passaggio 4 per creare una nuova query che restituisca un valore.  
  
4.  Fare clic con il pulsante destro del mouse sull'oggetto TableAdapter desiderato e aggiungere una query mediante il menu di scelta rapida.  
  
     Viene aperta la **Configurazione guidata query TableAdapter**.  
  
5.  Lasciare il valore predefinito **Usa istruzioni SQL**, quindi scegliere **Avanti**.  
  
6.  Selezionare l'opzione **SELECT che restituisce un valore**, quindi scegliere **Avanti**.  
  
7.  Digitare l'istruzione SQL o utilizzare il **Generatore di query** per crearne una, quindi scegliere **Avanti**.  
  
8.  Immettere un nome per la query.  
  
9. Completare la procedura guidata. La query verrà aggiunta al TableAdapter.  
  
10. Compilazione del progetto.  
  
#### Per dichiarare un'istanza del TableAdapter ed eseguire la query  
  
1.  Dichiarare un'istanza del TableAdapter che contiene la query da eseguire.  
  
    -   Per creare un'istanza con gli strumenti di progettazione, trascinare il TableAdapter prescelto dalla **Casella degli strumenti**.  I componenti del progetto sono ora visualizzati nella **Casella degli strumenti** sotto a un'intestazione che corrisponde al nome del progetto. Se nella **Casella degli strumenti** non viene visualizzato il TableAdapter, potrebbe essere necessario compilare il progetto.  
  
         In alternativa  
  
    -   Per creare un'istanza nel codice, sostituire il codice riportato di seguito con i nomi della classe <xref:System.Data.DataSet> e del TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  I TableAdapter non si trovano all'interno delle classi di dataset associate.  Per ogni dataset esiste una raccolta corrispondente di TableAdapter nel relativo spazio dei nomi.  Per un dataset denominato `SalesDataSet`, ad esempio, esiste uno spazio dei nomi `SalesDataSetTableAdapters` che contiene i rispettivi TableAdapter.  
  
2.  Chiamare la query procedendo come per qualsiasi altro metodo nel codice.  La query è un metodo eseguito sull'oggetto TableAdapter.  Sostituire il codice che segue con i nomi del TableAdapter e della query.  È anche necessario passare i parametri richiesti dalla query e utilizzare in qualche modo il valore restituito, ad esempio assegnandolo a una variabile.  In caso di dubbi sulla necessità di parametri per la query o sul tipo di parametri richiesti, verificare che in IntelliSense sia presente la firma richiesta della query.  A seconda che la query accetti o meno parametri, il codice risulterà simile a uno degli esempi riportati di seguito.  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Potrebbe essere necessario assegnare il valore restituito dalla query a una variabile.  Diversamente dal metodo `ExecuteScalar` che restituisce un oggetto, il tipo di dati restituito dalle query TableAdapter che producono un singolo valore dipenderà dalla query.  Se, ad esempio, la query TableAdapter determina la selezione di una singola colonna con tipo di dati integer, il valore da essa restituito sarà di questo tipo.  Se nella colonna sono consentiti valori Null, il valore restituito corrisponderà a uno dei tipi nullable, quale `Nullable(Of Integer)`.  Per ulteriori informazioni sui tipi nullable, vedere <xref:System.Nullable>.  Il codice completo necessario per la dichiarazione di un'istanza di un TableAdapter e l'esecuzione di una query sarà simile a quello riportato di seguito. L'esempio che segue parte dal presupposto che il valore restituito sia un valore integer. Pertanto, modificare il codice in base al tipo di dati restituito dalla query.  
  
     [!code-cs[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.vb)]  
  
## Esecuzione di istruzioni SQL che restituiscono singoli valori utilizzando un oggetto comando  
 Nell'esempio che segue viene illustrato come creare un comando ed eseguire un'istruzione SQL che restituisce un valore.  Per informazioni sull'impostazione e il recupero dei valori dei parametri per un comando, vedere [Procedura: ottenere e impostare parametri per oggetti comando](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Nell'esempio che segue viene utilizzato l'oggetto <xref:System.Data.SqlClient.SqlCommand> e devono essere soddisfatti i seguenti requisiti:  
  
-   Riferimenti agli spazi dei nomi <xref:System>, <xref:System.Data> e <xref:System.Xml>.  
  
-   Una connessione dati denominata `SqlConnection1`.  
  
-   Una tabella denominata `Customers` nell'origine dati cui è collegato `SqlConnection1`.  Altrimenti, specificare un'istruzione SQL valida per l'origine dati.  
  
#### Per eseguire un'istruzione SQL che restituisce un valore utilizzando un DataCommand  
  
-   Aggiungere il codice che segue al metodo da cui eseguirlo.  Per restituire un singolo valore, chiamare il metodo `ExecuteScalar` di un comando, ad esempio <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>.  I dati vengono restituiti in un <xref:System.Object>.  
  
     [!code-cs[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.vb)]  
  
## Sicurezza di .NET Framework  
 Per l'accesso al database e l'esecuzione dell'istruzione SQL è richiesta un'autorizzazione.  
  
## Vedere anche  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Procedura: riempire un dataset](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Inserimento di dati nei dataset](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Procedura: ottenere e impostare parametri per oggetti comando](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)