---
title: "Procedura dettagliata: creazione di un database semplice di piccole dimensioni | Microsoft Docs"
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: creazione di un database semplice di piccole dimensioni
In questa procedura dettagliata, viene utilizzato Visual Studio per creare un piccolo database contenente il codice di esempio in [Procedura dettagliata: creazione di un'applicazione dati semplice tramite ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **In questo argomento**  
  
-   [Creare uno script in cui è contenuto uno schema di database](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Creare un progetto di database e importare uno schema](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Distribuire il database](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## Prerequisiti  
 Per completare questa procedura dettagliata è necessario avere installato [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  Si potrebbe inoltre essere in grado di connettersi a un server database o a un database LocalDB per il quale si dispone delle autorizzazioni per la creazione e la distribuzione di un database.  
  
##  <a name="CreateScript"></a> Creare uno script in cui è contenuto uno schema di database  
  
#### Per creare uno script da cui sia possibile importare uno schema  
  
1.  Nella barra dei menu di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]scegliere **File**, **Nuovo**, **File**.  
  
     Viene visualizzata la finestra di dialogo **Nuovo file**.  
  
2.  Nell'elenco **Categorie** scegliere **Generale**.  
  
3.  Nell'elenco **Modelli** selezionare **File SQL**, quindi fare clic sul pulsante **Apri**.  
  
     Viene visualizzato l'editor Transact\-SQL.  
  
4.  Copiare il seguente codice Transact\-SQL, quindi incollarlo nell'editor Transact\-SQL.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  Nella barra dei menu, scegliere **File**, **Salva SqlQuery\_1.sql con nome**.  
  
     Verrà visualizzata la finestra di dialogo **Salva file con nome**.  
  
6.  Nella casella **Nome file** immettere `SampleImportScript.sql`, prendere nota della posizione in cui verrà salvato il file, quindi scegliere il pulsante **Salva**.  
  
7.  Nella barra dei menu, scegliere **File**, **Chiudi soluzione**.  
  
     A questo punto è possibile creare un progetto di database e quindi importare lo schema dallo script creato.  
  
##  <a name="CreateProject"></a> Creare un progetto di database e importare uno schema  
  
#### Per creare un progetto di database  
  
1.  Nella barra dei menu, scegliere **File**, **Nuovo**, **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
2.  In **Installato**, espandere il nodo **Modelli**, espandere il nodo **Altri linguaggi**, scegliere la categoria **SQL Server** e quindi scegliere il modello **Progetto di database SQL Server**.  
  
    > [!NOTE]
    >  Il nodo **Altri linguaggi** non viene visualizzato in tutte le installazioni di Visual Studio.  
  
3.  Nella casella **Nome** immettere `Small Database`.  
  
4.  Selezionare la casella di controllo **Crea directory per soluzione**, se non è già selezionata.  
  
5.  Deselezionare la casella di controllo **Aggiungi al controllo del codice sorgente**, se non è già deselezionata, quindi scegliere il pulsante **OK**.  
  
     Il progetto di database verrà creato e visualizzato in **Esplora soluzioni**.  
  
     A questo punto, è possibile procedere all'importazione dello schema di database dallo script.  
  
#### Per importare uno schema di database da uno script  
  
1.  Nella barra dei menu, scegliere **Progetto**, **Importa**, **Script**.  
  
2.  Nella pagina di benvenuto, rivedere il testo e scegliere **Avanti**.  
  
3.  Selezionare il pulsante di opzione **Singolo file**, quindi selezionare il pulsante **Esplora**.  
  
     Viene visualizzata la finestra di dialogo **Importa script SQL**.  
  
4.  Aprire la cartella in cui è stato salvato il file SampleImportScript.sql, scegliere il file, quindi scegliere il pulsante **Apri**.  
  
5.  Selezionare il pulsante **Fine** per chiudere la finestra di dialogo **Importa script SQL**.  
  
     Lo script viene importato e gli oggetti che vi sono definiti vengono aggiunti al progetto di database.  
  
6.  Esaminare il riepilogo e quindi scegliere il pulsante **Fine** per chiudere la finestra di dialogo **File di script SQL di importazione**.  
  
7.  In **Esplora soluzioni** espandere le cartelle Vendite, Script e Sicurezza del progetto e verificare che contengano file SQL.  
  
8.  In **Esplora oggetti di SQL Server** verificare che il database venga visualizzato nel nodo **Progetti**.  
  
     A questo punto, il database contiene solo gli oggetti di sistema, ad esempio tabelle e stored procedure.  Dopo aver distribuito il database, questo conterrà le tabelle utente e le stored procedure che definiscono gli script.  
  
##  <a name="DeployDatabase"></a> Distribuire il database  
 Per impostazioni predefinita, quando si preme F5, si distribuisce \(o si pubblica\) il database in un database LocalDB.  È possibile distribuire il database in un percorso diverso dalla pagina delle proprietà per il progetto, scegliendo la scheda **Debug** e quindi modificando la stringa di connessione.