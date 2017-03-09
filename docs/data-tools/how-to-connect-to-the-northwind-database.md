---
title: "Procedura dettagliata: connettersi al database Northwind | Microsoft Docs"
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
  - "connessioni [Visual Studio], database Northwind"
  - "Northwind (database di esempio)"
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura dettagliata: connettersi al database Northwind
Per comprendere come creare applicazioni di database usando Visual Studio, è necessario connettersi al database Northwind per seguire molti degli esempi forniti nella documentazione del prodotto.  A seconda dell'esempio che si sta seguendo, verrà effettuata la connessione al database di SQL Server o di un file database, ad esempio uno per Microsoft Access o SQL Server.  
  
## Creazione delle connessioni dati al database Northwind  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per creare una connessione dati al database Northwind  
  
1.  Scegliere **Esplora server**\/**Esplora database** dal menu **Visualizza**.  
  
2.  In **Esplora server**\/**Esplora database** aprire il menu di scelta rapida relativo a **Connessioni dati** e scegliere **Aggiungi connessione**.  
  
     Dopo aver scelto **Aggiungi connessione** viene visualizzata la finestra di dialogo **Scegli origine dati** o **Aggiungi connessione**.  
  
3.  Se viene visualizzata la finestra di dialogo **Scegli origine dati**, selezionare **Microsoft SQL Server** e quindi scegliere **OK**.  
  
     Se viene visualizzata la finestra di dialogo **Aggiungi connessione** e l'**Origine dati** non è **Microsoft SQL Server \(SqlClient\)**, scegliere il pulsante **Cambia** per aprire la finestra di dialogo **Modifica origine dati**, selezionare **Microsoft SQL Server** e quindi scegliere **OK**.  
  
4.  Nell'elenco **Nome server** specificare il nome del server in sui si trova il database Northwind.  
  
5.  In base ai requisiti della versione di SQL Server e del database Northwind, scegliere **Usa autenticazione di Windows** oppure **Usa autenticazione di SQL Server** e immettere un nome utente e una password per accedere al computer in cui è in esecuzione SQL Server.  
  
6.  Scegliere il database Northwind nell'elenco **Seleziona o immetti nome di database**.  
  
7.  Scegliere **Test connessione** per verificare la connessione al database Northwind.  
  
8.  Scegliere **OK**.  
  
     Una connessione dati al database Northwind viene aggiunta a **Esplora server**\/**Esplora database**.  
  
 Oltre a connettersi a un'istanza remota di un database SQL Server, è possibile anche connettersi direttamente ai file effettivi che contengono il database.  In questo modo è possibile aggiungere i file di database direttamente in un progetto dove possono essere implementati come parte dell'applicazione.  I file di database locale attualmente supportati sono i seguenti: file di database SQL Server Compact \(.sdf\), [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] e SQL Server Express \(.mdf\), e file di database Microsoft Access \(.mdb o .accdb\).  
  
#### Per creare una connessione dati al database Northwind: file di database SQL Server \(.mdf\)  
  
1.  Scegliere **Esplora server**\/**Esplora database** dal menu **Visualizza**.  
  
2.  In **Esplora server**\/**Esplora database** aprire il menu di scelta rapida relativo a **Connessioni dati** e scegliere **Aggiungi connessione**.  
  
     Dopo aver scelto **Aggiungi connessione** viene visualizzata la finestra di dialogo **Aggiungi connessione** o **Scegli origine dati**.  
  
3.  Se viene visualizzata la finestra di dialogo **Scegli origine dati**, selezionare **File di database Microsoft SQL Server** e quindi scegliere **OK**.  
  
4.  Se viene visualizzata la finestra di dialogo **Aggiungi connessione**, verificare che **Origine dati** sia impostata su **File di database Microsoft SQL Server \(SqlClient\)**.  Se non è impostata su **File di database Microsoft SQL Server \(SqlClient\)**, scegliere **Modifica** per aprire la finestra di dialogo **Modifica origine dati**, scegliere **File di database Microsoft SQL Server** e quindi scegliere **OK**.  
  
5.  Scegliere **Sfoglia** per trovare il file .mdf che contiene il database Northwind.  
  
6.  In base ai requisiti della versione del database Northwind, scegliere **Usa autenticazione di Windows** oppure **Usa autenticazione di SQL Server** e immettere un nome utente e una password per accedere al computer in cui è in esecuzione SQL Server.  
  
7.  Fare clic sul pulsante **OK**.  
  
     Una connessione dati al database Northwind viene aggiunta a **Esplora server**\/**Esplora database**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ha modifiche che si applicano al file di database Northwind database file \(.mdf\).  Per informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### Per creare una connessione dati al file di database Northwind o Access \(mdb o .accdb\)  
  
1.  Scegliere **Esplora server**\/**Esplora database** dal menu **Visualizza**.  
  
2.  In **Esplora server**\/**Esplora database** aprire il menu di scelta rapida relativo a **Connessioni dati** e scegliere **Aggiungi connessione**.  
  
     Dopo aver scelto **Aggiungi connessione** viene visualizzata la finestra di dialogo **Aggiungi connessione** o **Scegli origine dati**.  
  
3.  Se viene visualizzata la finestra di dialogo **Scegli origine dati**, selezionare **File di database Microsoft Access**, quindi scegliere **OK**.  
  
4.  Se viene visualizzata la finestra di dialogo **Aggiungi connessione**, verificare che **Origine dati** sia impostata su **File di database Microsoft SQL Server**.  Se non è impostata su **File di database Microsoft Access**, scegliere **Modifica** per aprire la finestra di dialogo **Modifica origine dati**, scegliere **File di database di Microsoft Access** e quindi scegliere **OK**.  
  
5.  Scegliere **Sfoglia** per trovare il file .mdf o .accdb che contiene il database Northwind.  
  
6.  Immettere un nome utente e una password se richiesto dalla versione del database Northwind.  
  
7.  Scegliere **OK**.  
  
     Una connessione dati al database Northwind viene aggiunta a **Esplora server**\/**Esplora database**.  
  
## Vedere anche  
 [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md)   
 [Programmazione dei dati con Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)