---
title: "Procedura dettagliata: creazione delle stored procedure di aggiornamento per la tabella Customers Northwind | Microsoft Docs"
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
  - "Northwind (database di esempio)"
  - "Progettazione relazionale oggetti, stored procedure"
  - "stored procedure [Visual Studio]"
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura dettagliata: creazione delle stored procedure di aggiornamento per la tabella Customers Northwind
Per alcuni argomenti della guida nella documentazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sono necessarie stored procedure aggiuntive nel database di esempio Northwind per l'esecuzione dei comandi di aggiornamento dei dati \(inserimento, aggiornamento ed eliminazione\) nella tabella Customers.  
  
 Questa procedura dettagliata illustra come creare le stored procedure aggiuntive nel database di esempio Northwind per [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  
  
 Nella sezione Passaggi successivi, più avanti in questo argomento, sono disponibili collegamenti ad argomenti in cui viene illustrato l'uso delle stored procedure aggiuntive.  
  
 In questa procedura dettagliata si apprenderà come eseguire le attività seguenti:  
  
-   Creare una connessione dati al database di esempio Northwind.  
  
-   Creare le stored procedure.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere alla versione SQL Server del database di esempio Northwind.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Connessione al database Northwind  
 Questa procedura dettagliata richiede una connessione alla versione SQL Server del database Northwind.  Nella procedura descritta di seguito vengono fornite le istruzioni per la creazione della connessione dati.  
  
> [!NOTE]
>  Se si dispone già di una connessione dati al database Northwind, è possibile passare alla sezione successiva, Creazione delle stored procedure.  
  
#### Per creare una connessione dati al database di esempio Northwind  
  
1.  Scegliere **Esplora server**\/**Esplora database** dal menu **Visualizza**.  
  
2.  Fare clic con il pulsante destro del mouse su **Connessioni dati** e scegliere **Aggiungi connessione**.  
  
3.  Nella finestra di dialogo **Scegli origine dati** fare clic su **Microsoft SQL Server**, quindi fare clic su **OK**.  
  
     Se viene visualizzata la finestra di dialogo **Aggiungi connessione** e l'**Origine dati** non è **Microsoft SQL Server \(SqlClient\)**, fare clic su **Cambia** per aprire la finestra di dialogo **Scegli\/Modifica origine dati**, fare clic su **Microsoft SQL Server** e quindi fare clic su **OK**.  
  
4.  Fare clic su un **Nome server** nell'elenco a discesa o digitare il nome del server in cui si trova il database Northwind.  
  
5.  In base ai requisiti del database o dell'applicazione, fare clic su **Usa autenticazione di Windows** oppure usare un nome utente e una password specifici per accedere al computer in cui è in esecuzione SQL Server \(**Autenticazione di SQL Server**\).  
  
6.  Fare clic sul database Northwind nell'elenco **Seleziona o immetti nome di database**.  
  
7.  Fare clic su **OK**.  
  
     La connessione dati viene aggiunta a **Esplora server**\/**Esplora database**.  
  
## Creazione delle stored procedure  
 Creare le stored procedure eseguendo lo script SQL fornito sul database Northwind mediante [Visual Database Tools](http://msdn.microsoft.com/it-it/6b145922-2f00-47db-befc-bf351b4809a1), disponibile in **Esplora server**\/**Esplora database**.  
  
#### Per creare le stored procedure mediante uno script SQL  
  
1.  Espandere il database Northwind in **Esplora server**\/**Esplora database**.  
  
2.  Fare clic con il pulsante destro del mouse sul nodo **Stored procedure** e scegliere **Aggiungi nuova stored procedure**.  
  
3.  Incollare il codice seguente nell'editor del codice, sostituendo il modello `CREATE PROCEDURE`:  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Selezionare tutto il testo nell'editor del codice, fare clic con il pulsante destro del mouse sul testo selezionato e scegliere **Esegui selezione**.  
  
     Verranno create le stored procedure SelectCustomers, InsertCustomers, UpdateCustomers e DeleteCustomers per il database Northwind.  
  
## Passaggi successivi  
 Dopo aver creato le stored procedure, provare le procedure dettagliate seguenti, in cui viene illustrato come usare le stored procedure:  
  
 [Procedura: assegnare stored procedure per l'esecuzione dei comandi di aggiornamento, inserimento ed eliminazione \(Progettazione relazionale oggetti\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [Procedura dettagliata: personalizzazione del comportamento di Insert, Update e Delete delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)