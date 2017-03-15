---
title: "Procedura: installare database di esempio | Microsoft Docs"
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
  - "database di esempio di Adventure Works"
  - "dati [Visual Studio], database di esempio"
  - "Northwind (database di esempio)"
  - "database di esempio, Adventure Works"
  - "database di esempio, Northwind"
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: installare database di esempio
Diversi esempi di dati prevedono come requisito la connessione ai database di esempio Northwind, Pubs e AdventureWorks.  È possibile installare e connettersi a questi database tramite le procedure riportate di seguito.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Installazione dei database  
 Molti esempi di dati richiedono la disponibilità dei database di esempio che possono essere scaricati da siti Web.  I database di esempio includono AdventureWorks, Northwind e Pubs.  
  
#### Per installare i database di SQL Server di esempio Northwind e Pubs  
  
1.  Passare al sito Web relativo ai [database di esempio Northwind e Pubs](http://go.microsoft.com/fwlink?linkid=64296).  
  
2.  Scaricare ed eseguire il programma di installazione.  
  
     Il programma di installazione aggiunge una cartella **SQL Server 2000 Sample Databases** nella cartella radice del computer.  Ad esempio: **C:\\SQL Server 2000 Sample Databases**.  
  
3.  Individuare lo script SQL per il database desiderato, Northwind o Pubs.  
  
    > [!WARNING]
    >  Il file di database .MDF non può essere facilmente convertito in un formato utilizzabile nelle versioni correnti di SQL Server, è preferibile usare lo script per creare il database.  
  
4.  In **Esplora server**, creare una connessione a un'istanza di SQL Server in cui si desidera installare il database.  Se non si dispone di un'istanza specifica di SQL Server che si desidera usare, è possibile usare il database che viene installato automaticamente con Visual Studio.  A tale scopo, specificare `(localdb)\v11.0` come nome del server.  
  
     Per creare la connessione, effettuare le operazioni seguenti.  
  
    ###### Per creare una connessione a un'istanza di SQL Server  
  
    1.  In **Esplora server**, aprire il menu di scelta rapida del nodo **Connessioni dati** e scegliere **Aggiungi connessione**.  
  
         Verrà visualizzata la finestra di dialogo **Aggiungi connessione**.  
  
    2.  Immettere il nome dell'istanza di SQL Server in cui si desidera creare il database Pubs o Northwind o immettere \(localdb\)\\v11.0.  
  
    3.  In **Seleziona o immetti un nome database**, scegliere qualsiasi database dall'elenco, ad esempio, tempdb.  
  
    4.  Scegliere il pulsante **Test connessione** per assicurarsi che la connessione funzioni, quindi scegliere il pulsante **OK**.  
  
         Il nodo della nuova connessione verrà visualizzato in **Esplora server**.  
  
5.  Nel menu di scelta rapida per il nodo della connessione per il server, scegliere **Nuova query**.  
  
     Verrà visualizzata una finestra dell'editor con un file di script .sql.  
  
6.  Incollare il contenuto di instnwnd.sql o di instpubs.sql nella finestra dell'editor.  
  
7.  Scegliere il pulsante Esegui query \(l'icona del triangolo verde aperto nella parte superiore destra della finestra della query\).  
  
     Se la query ha esito positivo, viene visualizzato il messaggio **Il comando o i comandi sono stati completati**.  Ciò significa che il database Northwind o pubs è stato creato.  
  
     È comunque necessario aggiungere una connessione al database di esempio.  In **Esplora server**, aprire il menu di scelta rapida del nodo **Connessioni dati** e scegliere **Aggiungi connessione**.  
  
8.  Scegliere lo stesso database del server che si è scelto in precedenza, ma questa volta scegliere il database Northwind in Seleziona o immetti nome di database e scegliere il pulsante **OK**.  
  
     Verrà visualizzato un nuovo nodo in Connessioni dati per il database di esempio.  
  
9. Chiudere la finestra dell'editor e confermare che non si vuole salvare il file di query.  Non è necessario salvare lo script di creazione del database dopo aver creato il database.  
  
#### Per installare il database di esempio AdventureWorks  
  
-   Scaricare i database di esempio AdventureWorks dal [sito Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### Per installare il database di esempio Northwind per Microsoft Access  
  
1.  In Microsoft Access 2010 o versione successiva, cercare online i modelli Northwind e scegliere il **database di esempio Northwind 2007**.  
  
2.  In Microsoft Access salvare il file di database come Northwind.accdb.  
  
 La nuova estensione per i database di Access è .accdb.  Vedere [Programmazione dei dati con Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx).  Per connettersi al database Northwind tramite Access, vedere [Procedura dettagliata: connettersi al database Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## Sicurezza di .NET Framework  
 I database di esempio sono forniti a fini illustrativi e non necessariamente presentano le procedure di sicurezza ottimali.  
  
## Vedere anche  
 [Come determinare la versione e l'edizione di SQL Server e dei relativi componenti](http://support.microsoft.com/kb/321185)   
 [Procedura dettagliata: creazione di un file di database locale in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Procedura dettagliata: connettersi al database Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)