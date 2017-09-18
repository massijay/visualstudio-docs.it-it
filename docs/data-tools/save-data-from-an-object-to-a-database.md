---
title: "Procedura: salvare dati da un oggetto in un database | Microsoft Docs"
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
  - "accesso ai dati [Visual Studio], oggetti"
  - "salvataggio di dati"
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: salvare dati da un oggetto in un database
È possibile salvare i dati dagli oggetti in un database passando i valori dall'oggetto in uso a uno dei metodi DBDirect del TableAdapter \(ad esempio, `TableAdapter.Insert`\).  Per ulteriori informazioni, vedere [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md).  
  
 Per salvare i dati di una raccolta di oggetti, scorrere la raccolta di oggetti \(ad esempio, utilizzando un ciclo For\-Next\) e inviare i valori per ciascun oggetto al database utilizzando uno dei metodi DBDirect del TableAdapter.  
  
 Per impostazione predefinita, i metodi DBDirect vengono creati in un TableAdapter che è possibile eseguire direttamente nel database.  Tali metodi possono essere chiamati direttamente e non richiedono oggetti <xref:System.Data.DataSet> o <xref:System.Data.DataTable> per riconciliare le modifiche al fine di inviare gli aggiornamenti a un database.  
  
> [!NOTE]
>  Quando si configura un TableAdapter, la query principale dovrà fornire informazioni sufficienti alla creazione dei metodi DBDirect.  Se, ad esempio, un TableAdapter è configurato per l'esecuzione di query di dati da una tabella in cui non è presente una colonna di chiave primaria definita, i metodi DBDirect non saranno generati.  
  
|Metodo DBDirect di TableAdapter|Descrizione|  
|-------------------------------------|-----------------|  
|`TableAdapter.Insert`|Aggiunge nuovi record a un database e consente di passare singoli valori di colonna come parametri di metodo.|  
|`TableAdapter.Update`|Aggiorna i record esistenti in un database  Il metodo `Update` accetta valori di colonna originali e quelli nuovi come parametri di metodo.  I valori originali sono utilizzati per individuare il record originale, mentre i valori nuovi sono utilizzati per aggiornarlo.<br /><br /> Il metodo `TableAdapter.Update` è anche utilizzato per risolvere le differenze tra le modifiche apportate a un dataset e il database utilizzando un oggetto <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, oppure una matrice di oggetti <xref:System.Data.DataRow> come parametri di metodo.|  
|`TableAdapter.Delete`|Elimina i record esistenti dal database in base ai valori di colonna originali passati come parametri di metodo.|  
  
### Per salvare i nuovi record da un oggetto a un database  
  
-   Creare i record passando i valori al metodo `TableAdapter.Insert`.  
  
     Nell'esempio riportato di seguito nella tabella `Customers` viene creato un nuovo record cliente mediante il passaggio dei valori dell'oggetto `currentCustomer` al metodo `TableAdapter.Insert`.  
  
     [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### Per aggiornare i record esistenti da un oggetto a un database  
  
-   Modificare i record chiamando il metodo `TableAdapter.Update` e passando i nuovi valori per aggiornare il record e passando i valori originali per individuare il record.  
  
    > [!NOTE]
    >  Per passare i valori originali al metodo `Update`, sarà necessario mantenere tali valori nell'oggetto in uso.  In questo esempio vengono utilizzate le proprietà con un prefisso `orig` per memorizzare i valori originali.  
  
     Nell'esempio riportato di seguito viene aggiornato un record esistente nella tabella `Customers` mediante il passaggio dei valori nuovi e di quelli originali dell'oggetto `Customer` al metodo `TableAdapter.Update`.  
  
     [!code-cs[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### Per eliminare i record esistenti da un database  
  
-   Eliminare i record chiamando il metodo `TableAdapter.Delete` e passando i valori originali per individuare il record.  
  
    > [!NOTE]
    >  Per passare i valori originali al metodo `Delete`, sarà necessario mantenere tali valori nell'oggetto in uso.  In questo esempio vengono utilizzate le proprietà con un prefisso `orig` per memorizzare i valori originali.  
  
     Nell'esempio riportato di seguito viene eliminato un record dalla tabella `Customers` mediante il passaggio dei valori originali dell'oggetto `Customer` al metodo `TableAdapter.Delete`.  
  
     [!code-cs[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## Sicurezza di .NET Framework  
 Per eseguire le istruzioni INSERT, UPDATE o DELETE selezionate sulla tabella del database è necessario disporre dell'autorizzazione appropriata.  
  
## Vedere anche  
 [Associazione di oggetti in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)   
 [Procedura: connettersi ai dati negli oggetti](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [Procedura dettagliata: connessione ai dati negli oggetti \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [Procedura: accedere direttamente al database mediante un oggetto TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)