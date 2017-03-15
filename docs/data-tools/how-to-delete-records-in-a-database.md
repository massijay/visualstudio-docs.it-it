---
title: "Procedura: eliminare record da un database | Microsoft Docs"
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
  - "database, eliminazione di record"
  - "eliminazione di dati"
  - "record, eliminazione"
  - "salvataggio di dati"
  - "TableAdapter.Delete (metodo)"
  - "TableAdapter.Update (metodo)"
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: eliminare record da un database
Per eliminare i record da un database, utilizzare il metodo `TableAdapter.Update` oppure il metodo `TableAdapter.Delete`.  In alternativa, se nell'applicazione non sono utilizzati TableAdapter, è possibile utilizzare oggetti Command di un database \(ad esempio, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  
  
 In genere, il metodo `TableAdapter.Update` è utilizzato quando i dati vengono memorizzati nell'applicazione mediante i dataset, mentre il metodo `TableAdapter.Delete` è utilizzato quando i dati vengono memorizzati nell'applicazione mediante gli oggetti.  
  
 Se nel TableAdapter in uso non è presente un metodo `Delete`, il TableAdapter è stato configurato per utilizzare stored procedure oppure la relativa proprietà `GenerateDBDirectMethods` è impostata su `false`.  Provare a impostare la proprietà `GenerateDBDirectMethods` del TableAdapter su `true` dalla [Progettazione DataSet](../data-tools/creating-and-editing-typed-datasets.md), quindi salvare il dataset per rigenerare il TableAdapter.  Se dopo tale procedura, nel TableAdapter non è ancora presente un metodo `Delete`, nella tabella non vengono fornite informazioni di schema sufficienti per distinguere tra le righe singole \(ad esempio, sulla tabella non è impostata alcuna chiave primaria\).  
  
## Eliminazione dei record mediante i TableAdapter  
 Nei TableAdapters sono forniti vari metodi per eliminare i record da un database a seconda dei requisiti dell'applicazione.  
  
 Se nell'applicazione sono utilizzati dataset per memorizzare i dati, è possibile eliminare in modo semplice i record dall'oggetto <xref:System.Data.DataTable> desiderato nell'oggetto <xref:System.Data.DataSet>e quindi chiamare il metodo `TableAdapter.Update`.  Il metodo `TableAdapter.Update` accetta tutte le modifiche apportate alla tabella dati e le invia al database \(inclusi i record inseriti, aggiornati ed eliminati\).  
  
#### Per eliminare i record da un database utilizzando il metodo TableAdapter.Update  
  
-   Eliminare i record dall'oggetto <xref:System.Data.DataTable> desiderato eliminando gli oggetti <xref:System.Data.DataRow> dalla tabella.  Per ulteriori informazioni, vedere [Procedura: eliminare righe in un oggetto DataTable](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md).  Dopo l'eliminazione delle righe dall'oggetto <xref:System.Data.DataTable>, chiamare il metodo `TableAdapter.Update`.  È possibile controllare la quantità di dati da modificare passando un oggetto <xref:System.Data.DataSet> intero, un oggetto <xref:System.Data.DataTable>, una matrice di oggetti <xref:System.Data.DataRow> oppure un oggetto <xref:System.Data.DataRow> singolo.  Nel codice riportato di seguito viene illustrato come eliminare un record da un oggetto <xref:System.Data.DataTable> e chiamare il metodo `TableAdapter.Update` per comunicare le modifiche ed eliminare la riga dal database.  In questo esempio viene utilizzata la tabella `Region` del database Northwind.  
  
     [!code-vb[VbRaddataSaving#20](../data-tools/codesnippet/VisualBasic/how-to-delete-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#20](../data-tools/codesnippet/CSharp/how-to-delete-records-in-a-database_1.cs)]  
  
 Se nell'applicazione vengono utilizzati gli oggetti per la memorizzazione dei dati, per eliminare i dati direttamente dal database è possibile utilizzare i metodi DBDirect del TableAdapter.  La chiamata al metodo `Delete` consente di rimuovere i record dal database in base ai valori di parametro passati.  
  
#### Per eliminare i record da un database utilizzando il metodo TableAdapter.Update  
  
-   Chiamare il metodo `Delete` del TableAdapter passando i valori per ciascuna colonna come parametri del metodo `Delete`.  In questo esempio viene utilizzata la tabella `Region` del database Northwind.  
  
    > [!NOTE]
    >  Se non è disponibile alcuna istanza, creare un'istanza del TableAdapter da utilizzare.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/how-to-delete-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/how-to-delete-records-in-a-database_2.cs)]  
  
## Eliminazione di record mediante oggetti Command  
 Nell'esempio riportato di seguito vengono eliminati i record direttamente da un database utilizzando oggetti Command.  Per ulteriori informazioni sull'utilizzo di oggetti Command per eseguire comandi e stored procedure, vedere [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md).  
  
#### Per eliminare i record da un database utilizzando oggetti Command  
  
-   Creare un nuovo oggetto Command e impostarne le proprietà `Connection`, `CommandType` e `CommandText`.  In questo esempio viene utilizzata la tabella `Region` del database Northwind.  
  
     [!code-vb[VbRaddataSaving#22](../data-tools/codesnippet/VisualBasic/how-to-delete-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#22](../data-tools/codesnippet/CSharp/how-to-delete-records-in-a-database_3.cs)]  
  
## Sicurezza di .NET Framework  
 È necessario disporre di accesso al database a cui si tenta di connettersi e dell'autorizzazione all'eliminazione dei record dalla tabella desiderata.  
  
## Vedere anche  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md)   
 [Procedura: aggiornare record in un database](../data-tools/how-to-update-records-in-a-database.md)   
 [Procedura: salvare dati da un oggetto in un database](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)