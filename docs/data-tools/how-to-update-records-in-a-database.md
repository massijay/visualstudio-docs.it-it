---
title: "Procedura: aggiornare record in un database | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "database, aggiornamento"
  - "record, modifica"
  - "record, aggiornamento"
  - "TableAdapter.Update (metodo)"
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: aggiornare record in un database
È possibile utilizzare il metodo `TableAdapter.Update` per aggiornare \(modificare\) i record in un database.  Il metodo `TableAdapter.Update` fornisce diversi overload che eseguono operazioni differenti a seconda dei parametri passati.  È importante conoscere i risultati delle chiamate alle diverse firme del metodo.  
  
> [!NOTE]
>  Se nell'applicazione non sono utilizzati TableAdapter, sarà possibile utilizzare oggetti Command per aggiornare i record nel database personalizzato \(ad esempio, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  Per ulteriori informazioni sull'aggiornamento dei dati mediante oggetti Command, vedere la sezione "Aggiornamento dei record mediante oggetti Command", di seguito.  
  
 Nella tabella riportata di seguito viene descritto il comportamento dei vari metodi `TableAdapter.Update`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Prova a salvare nel database tutte le modifiche apportate all'oggetto <xref:System.Data.DataTable>.  Tali modifiche includono la rimozione delle righe eliminate dalla tabella, l'aggiunta delle righe inserite nella tabella e l'aggiornamento delle righe modificate nella tabella.|  
|`TableAdapter.Update(DataSet)`|Sebbene un parametro accetti un dataset, il TableAdapter tenta di salvare sul database tutte le modifiche presenti nell'oggetto <xref:System.Data.DataTable> associato al TableAdapter.  Tali modifiche includono la rimozione delle righe eliminate dalla tabella, l'aggiunta delle righe inserite nella tabella e l'aggiornamento delle righe modificate nella tabella. **Note:**  Un oggetto <xref:System.Data.DataTable> associato al TableAdapter rappresenta l'oggetto <xref:System.Data.DataTable> creato durante la configurazione originale del TableAdapter.|  
|`TableAdapter.Update(DataRow)`|Prova a salvare nel database tutte le modifiche dell'oggetto <xref:System.Data.DataRow> indicato.|  
|`TableAdapter.Update(DataRows())`|Prova a salvare nel database tutte le modifiche alle righe della matrice dell'oggetto <xref:System.Data.DataRow>.|  
|`TableAdapter.Update("new column values", "original column values")`|Prova a salvare tutte le modifiche in una singola riga identificata dai valori di colonna originali.|  
  
 In genere, si utilizza il metodo `TableAdapter.Update` che accetta un oggetto <xref:System.Data.DataSet>, <xref:System.Data.DataTable> oppure <xref:System.Data.DataRow> quando nell'applicazione i dataset sono utilizzati esclusivamente per memorizzare i dati.  
  
 In genere, si utilizza il metodo `TableAdapter.Update` che accetta valori di colonna quando nell'applicazione si utilizzano oggetti per memorizzare i dati.  
  
 Se nel TableAdapter non è presente un metodo `Update` che accetta valori di colonna, il TableAdapter è configurato per utilizzare le stored procedure oppure la relativa proprietà `GenerateDBDirectMethods` è impostata su `false`.  Provare a impostare la proprietà `GenerateDBDirectMethods` del TableAdapter su `true` dalla [Progettazione DataSet](../data-tools/creating-and-editing-typed-datasets.md), quindi salvare il dataset per rigenerare il TableAdapter.  Se, dopo tale procedura, nel TableAdapter non è ancora presente un metodo `Update` che accetta valori di colonna, è probabile che la tabella non fornisca informazioni di schema sufficienti per distinguere tra le righe singole \(ad esempio, sulla tabella non è impostata alcuna chiave primaria\).  
  
## Aggiornamento dei record esistenti mediante i TableAdapter  
 Nei TableAdapter sono forniti vari metodi per aggiornare i record in un database, a seconda dei requisiti dell'applicazione.  
  
 Se nell'applicazione sono utilizzati dataset per archiviare i dati, è possibile aggiornare semplicemente i record nell'oggetto <xref:System.Data.DataTable> desiderato, quindi chiamare il metodo `TableAdapter.Update` e passare l'oggetto <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> oppure la matrice di <xref:System.Data.DataRow>.  Nella tabella precedente sono descritti i diversi metodi `Update`.  
  
#### Per aggiornare i record in un database con il metodo TableAdapter.Update che accetta DataSet, DataTable, DataRow o DataRows\(\)  
  
1.  Modificare i record nell'oggetto <xref:System.Data.DataTable> desiderato modificando direttamente l'oggetto <xref:System.Data.DataRow> nell'oggetto <xref:System.Data.DataTable>.  Per ulteriori informazioni, vedere [Procedura: modificare le righe in un oggetto DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).  
  
2.  Dopo la modifica delle righe nell'oggetto <xref:System.Data.DataTable>, chiamare il metodo `TableAdapter.Update`.  È possibile controllare la quantità di dati da modificare passando un oggetto <xref:System.Data.DataSet> intero, un oggetto <xref:System.Data.DataTable>, una matrice di oggetti <xref:System.Data.DataRow> oppure un oggetto <xref:System.Data.DataRow> singolo.  
  
     Nel codice riportato di seguito viene illustrato come modificare un record in un oggetto <xref:System.Data.DataTable> e chiamare il metodo `TableAdapter.Update` per salvare le modifiche nel database.  In questo esempio viene utilizzata la tabella Region del database Northwind.  
  
     [!code-vb[VbRaddataSaving#17](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#17](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_1.cs)]  
  
 Se nell'applicazione sono utilizzati gli oggetti per memorizzare i dati, è possibile utilizzare i metodi `DBDirect` del TableAdapter per inviare i dati dagli oggetti direttamente al database.  Questi metodi consentono di passare i valori singoli per ciascuna colonna come parametri di metodo.  Con la chiamata a questo metodo si aggiorna un record esistente nel database con i valori di colonna passati nel metodo.  
  
 Nella procedura riportata di seguito viene utilizzata come esempio la tabella `Region` Northwind.  
  
#### Per aggiornare i record in un database utilizzando il metodo TableAdapter.Update che accetta valori di colonna.  
  
-   Chiamare il metodo `Update` del TableAdapter passando i valori nuovi e originali per ciascuna colonna come parametri.  
  
    > [!NOTE]
    >  Se non è disponibile alcuna istanza, creare un'istanza del TableAdapter da utilizzare.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_2.cs)]  
  
## Aggiornamento dei record mediante oggetti Command  
 Nell'esempio riportato di seguito vengono aggiornati i record esistenti direttamente in un database utilizzando oggetti Command.  Per ulteriori informazioni sull'utilizzo di oggetti Command per eseguire comandi e stored procedure, vedere [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md).  
  
 Nella procedura riportata di seguito viene utilizzata come esempio la tabella `Region` Northwind.  
  
#### Per aggiornare i record esistenti in un database utilizzando oggetti Command  
  
-   Creare un nuovo oggetto Command, impostarne le proprietà `Connection`, `CommandType` e `CommandText`, quindi aprire una connessione ed eseguire il comando.  
  
     [!code-vb[VbRaddataSaving#19](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#19](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_3.cs)]  
  
## Sicurezza di .NET Framework  
 È necessario disporre di un accesso al database a cui si tenta di connettersi e dell'autorizzazione all'aggiornamento dei record nella tabella desiderata.  
  
## Vedere anche  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: eliminare record da un database](../data-tools/how-to-delete-records-in-a-database.md)   
 [Procedura: inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md)   
 [Procedura: salvare dati da un oggetto in un database](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)