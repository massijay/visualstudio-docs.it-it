---
title: "Procedura: inserire nuovi record in un database | Microsoft Docs"
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
  - "database, inserimento di nuovi record"
  - "record, inserimento"
  - "salvataggio di dati"
  - "TableAdapters, inserimento di nuovi record"
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: inserire nuovi record in un database
Per inserire nuovi record in un database, è possibile utilizzare il metodo `TableAdapter.Update` oppure uno dei metodi DBDirect del TableAdapter \(in modo specifico il metodo `TableAdapter.Insert`\).  Per ulteriori informazioni, vedere [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md).  
  
 Se nell'applicazione non sono utilizzati TableAdapter, sarà possibile utilizzare oggetti Command per interagire e inserire nuovi record nel database in uso \(ad esempio, <xref:System.Data.SqlClient.SqlCommand>\).  
  
 Utilizzare il metodo `TableAdapter.Update` quando nell'applicazione vengono utilizzati i dataset per la memorizzazione dei dati.  Il metodo `Update` consente di inviare tutte le modifiche \(aggiornamenti, inserimenti ed eliminazioni\) al database.  
  
 Utilizzare il metodo `TableAdapter.Insert` quando nell'applicazione vengono utilizzati gli oggetti per la memorizzazione dei dati oppure se si desidera un maggiore controllo sulla creazione di nuovi record nel database.  
  
 Se nel TableAdapter non è presente un metodo `Insert`, il TableAdapter è stato configurato per utilizzare stored procedure oppure la relativa proprietà `GenerateDBDirectMethods` è impostata su `false`.  Provare a impostare la proprietà `GenerateDBDirectMethods` del TableAdapter su `true` dalla [Progettazione DataSet](../data-tools/creating-and-editing-typed-datasets.md), quindi salvare il dataset per rigenerare il TableAdapter.  Se, dopo tale procedura, nel TableAdapter non è ancora presente un metodo `Insert`, nella tabella non vengono fornite informazioni di schema sufficienti per distinguere tra le righe singole \(ad esempio, sulla tabella non è impostata alcuna chiave primaria\).  
  
## Inserimento di nuovi record mediante i TableAdapter  
 I TableAdapter forniscono diversi metodi per inserire nuovi record in un database a seconda dei requisiti dell'applicazione.  
  
 Se nell'applicazione sono utilizzati dataset per memorizzare i dati, è sufficiente nuovi record all'oggetto <xref:System.Data.DataTable> desiderato nel dataset e quindi chiamare il metodo `TableAdapter.Update`.  Il metodo `TableAdapter.Update` accetta tutte le modifiche apportate all'oggetto <xref:System.Data.DataTable> e le invia al database \(inclusi i record modificati ed eliminati\).  
  
#### Per inserire nuovi record in un database utilizzando il metodo TableAdapter.Update  
  
1.  Aggiungere nuovi record all'oggetto <xref:System.Data.DataTable> desiderato creando un nuovo oggetto <xref:System.Data.DataRow> e aggiungendolo alla raccolta <xref:System.Data.DataTable.Rows%2A>.  Per ulteriori informazioni, vedere [Procedura: aggiungere righe a una DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).  
  
2.  Dopo l'aggiunta delle righe all'oggetto <xref:System.Data.DataTable>, chiamare il metodo `TableAdapter.Update`.  È possibile controllare la quantità di dati da modificare passando un oggetto <xref:System.Data.DataSet> intero, un oggetto <xref:System.Data.DataTable>, una matrice di oggetti <xref:System.Data.DataRow> oppure un oggetto <xref:System.Data.DataRow> singolo.  
  
     Nel codice riportato di seguito viene illustrato come aggiungere un nuovo record a un oggetto <xref:System.Data.DataTable> e quindi chiamare il metodo `TableAdapter.Update` per salvare la nuova riga nel database.  In questo esempio viene utilizzata la tabella `Region` del database Northwind.  
  
     [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
 Se nell'applicazione sono utilizzati oggetti per la memorizzazione dei dati, è possibile utilizzare il metodo `TableAdapter.Insert` per creare nuove righe direttamente nel database.  Il metodo `Insert` accetta i valori singoli per ciascuna colonna come parametri.  La chiamata al metodo consente di inserire un nuovo record nel database con i valori di parametro passati.  
  
 Nella procedura riportata di seguito viene utilizzata come esempio la tabella `Region` del database Northwind.  
  
#### Per inserire nuovi record in un database utilizzando il metodo TableAdapter.Insert  
  
-   Chiamare il metodo `Insert` del TableAdapter passando i valori per ciascuna colonna come parametri.  
  
    > [!NOTE]
    >  Se non è disponibile alcuna istanza, creare un'istanza del TableAdapter da utilizzare.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## Inserimento di nuovi record mediante oggetti Command  
 Nell'esempio riportato di seguito vengono inseriti nuovi record direttamente in un database utilizzando oggetti Command.  Per ulteriori informazioni sull'utilizzo di oggetti Command per eseguire comandi e stored procedure, vedere [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md).  
  
 Nella procedura riportata di seguito viene utilizzata come esempio la tabella `Region` del database Northwind.  
  
#### Per inserire i nuovi record in un database utilizzando oggetti Command  
  
-   Creare un nuovo oggetto Command e impostarne le proprietà `Connection`, `CommandType` e `CommandText`.  
  
     [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## Sicurezza di .NET Framework  
 È necessario disporre di un accesso al database a cui si tenta di connettersi e dell'autorizzazione a eseguire l'inserimento nella tabella desiderata.  
  
## Vedere anche  
 [Procedura: eliminare record da un database](../data-tools/how-to-delete-records-in-a-database.md)   
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
 [Recupero dei valori di identità o del contatore](../Topic/Retrieving%20Identity%20or%20Autonumber%20Values.md)