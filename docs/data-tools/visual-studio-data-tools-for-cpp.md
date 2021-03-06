---
title: Gli strumenti di dati di Visual Studio per C++ | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: c5952c4ab8e8adac0338d406800a15a8a0b12989
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-data-tools-for-c"></a>Strumenti di dati di Visual Studio per C++
C++ nativo può spesso fornire la velocità delle prestazioni quando si accede a origini dati. Tuttavia, dati gli strumenti per le applicazioni C++ in Visual Studio non avanzati, come nel caso di applicazioni .NET. Ad esempio, è Impossibile utilizzare le finestre di origini dati di trascinamento della selezione di origini dati in un'area di progettazione di C++. Se è necessario un livello relazionale a oggetti, è necessario scrivere la propria oppure usare un prodotto di terze parti.  Lo stesso vale per la funzionalità di associazione dati, sebbene le applicazioni che utilizzano la libreria Microsoft Foundation Class è possono utilizzare alcune classi di database, insieme a documenti e visualizzazioni, per archiviare i dati in memoria e la visualizza all'utente. Per ulteriori informazioni, vedere [accesso ai dati in Visual C++](https://msdn.microsoft.com/en-us/library/7wtdsdkh.aspx) .  
  
 Per connettersi al database SQL, è possono utilizzare le applicazioni C++ native i driver ODBC e OLE DB e il provider ADO che sono inclusi in Windows. Questi possono connettersi a qualsiasi database che supporta tali interfacce. Il driver ODBC è lo standard. OLE DB viene fornita per compatibilità con le versioni precedenti. Per ulteriori informazioni su queste tecnologie di dati, vedere [Windows Data Access Components](https://msdn.microsoft.com/en-us/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 Per sfruttare le funzionalità personalizzate in SQL Server 2005 e versioni successive, usare il [SQL Server Native Client](https://msdn.microsoft.com/en-us/sqlserver/aa937733). Il client nativo contiene anche il driver ODBC di SQL Server e il provider OLE DB per SQL Server in una libreria a collegamento dinamico (DLL). Applicazioni che usano API in codice nativo (ODBC, OLE DB e ADO) per Microsoft SQL Server è supportata.  SQL Server Native Client viene installato con SQL Server Data Tools. La Guida di programmazione è qui: [SQL Server Native Client Programming](https://msdn.microsoft.com/en-us/library/ms130892.aspx).  
  
## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Per la connessione a localDB mediante ODBC e SQL Native Client da un'applicazione C++  
  
1.  Installare SQL Server Data Tools.  
  
2.  Se è necessario un database SQL di esempio a cui connettersi, scaricare il database Northwind e decomprimerlo in una nuova posizione.  
  
3.  Utilizzare SQL Server Management Studio per collegare il file mdf decompresso a localDB. All'avvio di SQL Server Management Studio, connettersi a (localdb) \MSSQLLocalDB.  
  
     ![Finestra di dialogo di connessione SQL Server Management Studio](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS connettersi finestra di dialogo")  
  
     Pulsante destro del mouse sul nodo del database locale nel riquadro a sinistra, quindi scegliere **collegamento**.  
  
     ![SQL Server Management Studio Collega database](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS Collega database")  
  
4.  Scaricare l'esempio di SDK di Windows di ODBC e decomprimerlo in una nuova posizione. Questo esempio mostra i comandi di base di ODBC utilizzata per connettersi a un database e di eseguire query e comandi. Maggiori informazioni su queste funzioni nel [Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms710252\(v=vs.85\).aspx). Quando si carica innanzitutto la soluzione (si trova nella cartella C++), Visual Studio offre aggiornare la soluzione per la versione corrente di Visual Studio. Scegliere **Sì**.  
  
5.  Per utilizzare il client nativo, è necessario un file di intestazione e un file lib. Questi file contengono le funzioni e le definizioni specifiche di SQL Server, oltre a funzioni ODBC definite in SQL. In **progetto** > **proprietà** > **directory di VC + +**, aggiungere le seguenti directory di inclusione:  
  
 **\<unità di sistema >: \Programmi\Microsoft SQL Server\110\SDK\Include** e la directory di libreria:  
  
 **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**  
  
6.  Aggiungere le righe seguenti in odbcsql.cpp. Il #define impedisce irrilevanti definizioni OLE DB che si sta compilando.  
  
    ```C++  
    #define _SQLNCLI_ODBC_  
    #include <sqlncli.h>  
    ```  
  
     Si noti che il codice di esempio non effettivamente utilizzare tutte le funzionalità native client, pertanto i passaggi precedenti non sono necessari per compilare ed eseguire. Ma il progetto è ora configurato per l'utilizzo di questa funzionalità. Per ulteriori informazioni, vedere [SQL Server Native Client Programming](https://msdn.microsoft.com/en-us/library/ms130892\(v=sql.130\).aspx).  
  
7.  Specificare i driver da utilizzare nel sottosistema ODBC. L'esempio passa l'attributo di stringa di connessione del DRIVER in come un argomento della riga di comando. In **progetto** > **proprietà** > **debug**, aggiungere questo argomento di comando:  
  
    ```C++  
    DRIVER="SQL Server Native Client 11.0"  
    ```  
  
8.  Premere F5 per compilare ed eseguire l'applicazione. Si noterà una finestra di dialogo del driver che viene richiesto di immettere un database. Immettere `(localdb)\MSSQLLocalDB`e controllare **Usa connessione Trusted**. Press **OK**. Verrà visualizzata una console con i messaggi che indicano una connessione riuscita. Verrà inoltre visualizzato un prompt dei comandi in cui è possibile digitare in un'istruzione SQL. La schermata seguente mostra un esempio di query e i risultati:  
  
     ![Output della query di esempio ODBC](../data-tools/media/raddata-odbc-sample-query-output.png "output della query di esempio ODBC raddata")  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)