---
title: "Procedura: eseguire una stored procedure che non restituisce valori | Microsoft Docs"
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
  - "ExecuteNonQuery (metodo)"
  - "stored procedure, creazione"
  - "stored procedure, esecuzione"
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: eseguire una stored procedure che non restituisce valori
Per eseguire una stored procedure che non restituisca alcun valore, è possibile utilizzare una query TableAdapter configurata in modo da eseguire una stored procedure, come ad esempio `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`.  
  
 Se nell'applicazione non vengono utilizzati TableAdapter, chiamare il metodo `ExecuteNonQuery` su un oggetto comando impostandone la proprietà `CommandType` su <xref:System.Data.CommandType>.  Per oggetto comando si intende il comando specifico del [Provider di dati .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md) utilizzato dall'applicazione.  Nel caso in cui, ad esempio, l'applicazione utilizzi il Provider di dati .NET Framework per SQL Server, l'oggetto comando sarebbe <xref:System.Data.SqlClient.SqlCommand>.  
  
 Negli esempi che seguono viene illustrato come eseguire stored procedure che non restituiscono valori da un database utilizzando TableAdapter oppure oggetti comando.  Per ulteriori informazioni sull'esecuzione di query con TableAdapter e comandi, vedere [Inserimento di dati nei dataset](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Esecuzione di stored procedure che non restituiscono valori utilizzando un TableAdapter  
 Nell'esempio che segue viene illustrato come creare una query TableAdapter utilizzando la [TableAdapter \(query, configurazione guidata\)](../data-tools/editing-tableadapters.md), quindi vengono fornite informazioni su come dichiarare un'istanza di TableAdapter ed eseguire la query.  
  
#### Per creare una stored procedure che non restituisce valori utilizzando un TableAdapter  
  
1.  Aprire un dataset in **Progettazione DataSet**.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Se non è già disponibile un TableAdapter, crearne uno.  Per ulteriori informazioni sulla creazione di TableAdapter, vedere [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Se esiste già una query su un determinato TableAdapter che utilizza una stored procedure che non restituisce valori, passare direttamente alla procedura successiva "Per dichiarare un'istanza del TableAdapter ed eseguire la query". In caso contrario, continuare con il passaggio 4 per creare una nuova query che non restituisce valori.  
  
4.  Fare clic con il pulsante destro del mouse sull'oggetto TableAdapter desiderato e aggiungere una query mediante il menu di scelta rapida.  
  
     Viene aperta la **Configurazione guidata query TableAdapter**.  
  
5.  Selezionare **Utilizza stored procedure esistente**, quindi scegliere **Avanti**.  
  
6.  Selezionare una stored procedure dall'elenco a discesa, quindi scegliere **Avanti**.  
  
7.  Selezionare l'opzione **Nessun valore**, quindi scegliere **Avanti**.  
  
8.  Immettere un nome per la query.  
  
9. Scegliere **Avanti** o **Fine** per completare la procedura guidata. La query verrà aggiunta al TableAdapter.  
  
10. Compilazione del progetto.  
  
#### Per dichiarare un'istanza del TableAdapter ed eseguire la query  
  
1.  Dichiarare un'istanza del TableAdapter che contiene la query da eseguire.  
  
    -   Per creare un'istanza con gli strumenti di progettazione, trascinare il TableAdapter prescelto dalla **Casella degli strumenti**.  I componenti del progetto sono ora visualizzati nella **Casella degli strumenti** sotto a un'intestazione che corrisponde al nome del progetto. Se nella **Casella degli strumenti** non viene visualizzato il TableAdapter, potrebbe essere necessario compilare il progetto.  
  
         In alternativa  
  
    -   Per creare un'istanza nel codice, sostituire il codice riportato di seguito con i nomi della classe <xref:System.Data.DataSet> e del TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  I TableAdapter non si trovano all'interno delle classi di dataset associate.  Per ogni dataset esiste una raccolta corrispondente di TableAdapter nel relativo spazio dei nomi.  Per un dataset denominato `SalesDataSet`, ad esempio, esiste uno spazio dei nomi `SalesDataSetTableAdapters` che contiene i rispettivi TableAdapter.  
  
2.  Chiamare la query procedendo come per qualsiasi altro metodo nel codice.  La query è un metodo eseguito sull'oggetto TableAdapter.  Sostituire il codice che segue con i nomi del TableAdapter e della query.  Sarà anche necessario passare i parametri richiesti dalla query.  In caso di dubbi sulla necessità di parametri per la query o sul tipo di parametri richiesti, verificare che in IntelliSense sia presente la firma richiesta della query.  A seconda che la query accetti o meno parametri, il codice risulterà simile a uno degli esempi riportati di seguito.  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Il codice completo necessario per dichiarare un'istanza del TableAdapter ed eseguire la query risulterà simile al seguente:  
  
     [!code-cs[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-no-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-no-value_1.vb)]  
  
## Esecuzione di stored procedure che non restituiscono valori utilizzando un oggetto comando  
 Nell'esempio che segue viene illustrato come creare un comando ed eseguire una stored procedure che non restituisce valori.  Per informazioni sull'impostazione e il recupero dei valori dei parametri per un comando, vedere [Procedura: ottenere e impostare parametri per oggetti comando](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Nell'esempio che segue viene utilizzato l'oggetto <xref:System.Data.SqlClient.SqlCommand> e devono essere soddisfatti i seguenti requisiti:  
  
-   Riferimenti agli spazi dei nomi <xref:System>, <xref:System.Data> e <xref:System.Xml>.  
  
#### Per eseguire una stored procedure che non restituisce valori utilizzando un DataCommand  
  
-   Aggiungere il codice che segue a un metodo dal quale si desidera eseguire la stored procedure.  Chiamare il metodo `ExecuteNonQuery` di un comando per non restituire valori, ad esempio <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.  
  
     [!code-cs[VbRaddataFillingAndExecuting#15](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-no-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-no-value_2.vb)]  
  
## Sicurezza di .NET Framework  
 Per l'accesso al database e l'esecuzione dell'istruzione SQL è richiesta un'autorizzazione.  
  
## Vedere anche  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Procedura: riempire un dataset](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Inserimento di dati nei dataset](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Procedura: ottenere e impostare parametri per oggetti comando](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)