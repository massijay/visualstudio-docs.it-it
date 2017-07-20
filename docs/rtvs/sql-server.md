---
title: Integrazione di SQL Server con R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 919dfc34-234a-489e-91bf-74a4cefae26c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 44ae1fd825997ff5eab1448ebd86f88a130172a1
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


# <a name="working-with-sql-server-and-r"></a>Uso di SQL Server ed R

R Tools per Visual Studio (RTVS) si avvale dell'eccezionale supporto di SQL Server in Visual Studio per rendere più facile l'uso dei database SQL da parte dei data scientist, in particolare la creazione e l'esecuzione di query SQL e l'uso di stored procedure.

> [!Note]
> Per usare SQL ed R contemporaneamente, è necessario aver installato SQL Server Data Tools:
> - Visual Studio 2017: eseguire il programma di installazione di Visual Studio e selezionare il carico di lavoro Elaborazione ed archiviazione dati, che include SQL Server Data Tools.
> - Visual Studio 2015: seguire le istruzioni in [Download SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) (Scaricare SQL Server Data Tools).

Il video seguente (3 minuti 3 secondi) fornisce una breve panoramica di SQL Server e di R:

<iframe width="560" height="315" src="https://www.youtube.com/embed/n4AYr0QIwdQ" frameborder="0" allowfullscreen></iframe>

## <a name="creating-and-running-sql-queries"></a>Creazione ed esecuzione di query SQL

RTVS supporta l'aggiunta di query SQL all'interno di progetti R, consentendo di sviluppare in modo iterativo query SQL in un contesto separato fino a quando non si ottengono i risultati voluti.

Per aggiungere un file di query SQL, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, scegliere **Aggiungi > Nuovo elemento...** e selezionare il tipo di file **Query SQL**:

![Aggiungere un elemento Query SQL a un progetto](media/sql-add-item.png)

Il file verrà aperto nell'editor Transact-SQL di Visual Studio, che è dotato di funzionalità IntelliSense complete per SQL e consente di eseguire query. Perché sia possibile usare queste funzionalità, tuttavia, è necessario connettersi a un database tramite il pulsante Connetti sulla barra degli strumenti dell'editor o semplicemente tentando di eseguire una query. A tale scopo premere CTRL+MAIUSC+E. Questa combinazione di tasti funziona anche su una selezione. In entrambi i casi viene visualizzata la finestra di dialogo di connessione:

![Finestra di dialogo di connessione SQL](media/sql-connection-dialog.png)

Dopo che è stata stabilita la connessione, è possibile eseguire query e visualizzarne i risultati:

![Risultati di una query SQL](media/sql-query-results.png)

L'editor Transact-SQL supporta numerose funzionalità, ad esempio la visualizzazione del piano di esecuzione della query e il debugger di query. Per i dettagli, vedere [Utilizzare l'Editor Transact-SQL per modificare ed eseguire script](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="working-with-sql-server-stored-procedures"></a>Uso di stored procedure di SQL Server

[SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 e versioni successive) consente di incorporare ed eseguire codice R da una stored procedure T-SQL. Ciò significa che è possibile eseguire codice R da un computer SQL Server, usare dati restituiti da una query SQL e generare un set di risultati SQL che può essere elaborato da altro codice SQL o restituito al client.

Come descritto nelle sezioni seguenti, RTVS semplifica il processo di combinazione di codice SQL ed R all'interno di un'unica istruzione SQL, altrimenti macchinoso e a rischio di errore.

- [Aggiungere una connessione di database](#add-a-database-connection)
- [Scrivere e testare una stored procedure SQL](#write-and-test-a-sql-stored-procedure)
- [Pubblicare una stored procedure SQL](#publish-a-sql-stored-procedure)

Il video seguente (6 minuti 9 secondi) offre una panoramica di queste funzionalità:

<iframe width="560" height="315" src="https://www.youtube.com/embed/dFKIT2OitWQ" frameborder="0" allowfullscreen></iframe>

### <a name="add-a-database-connection"></a>Aggiungere una connessione di database

1. Selezionare **R Tools > Dati > Aggiungi connessione di database** per visualizzare la finestra di dialogo **Proprietà connessione**, in cui è possibile specificare il nome dell'origine dati (in questo caso SQL Server), del server e del database, nonché la modalità di autenticazione. È possibile selezionare **Test connessione** per verificare l'input prima di chiudere la finestra di dialogo.
 
    ![Finestra di dialogo di connessione SQL](media/sql-connection-string-dialog.png)

1. Dopo avere verificato che la connessione sia valida, selezionare **OK**. Visual Studio genera una stringa di connessione denominata `dbConnection` in un nuovo file `settings.R`. RTVS origina (esegue) automaticamente questo file. È quindi possibile usare immediatamente la connessione da script R:

![File Settings.R SQL](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Scrivere e testare una stored procedure SQL

Per aggiungere una nuova stored procedure SQL, fare clic con il pulsante destro del mouse sul progetto, selezionare **Aggiungi > Nuovo elemento...**, selezionare **Stored Procedure SQL con R** dall'elenco di modelli, assegnare un nome al file (`StoredProcedure.R` in questo esempio) e selezionare **OK**.
 
RTVS crea tre file per la stored procedure, un file `.R` per il codice R, un file `.Query.sql` per il codice SQL e un file `.Template.sql` che combina i due file precedenti. Gli ultimi due sono visualizzati in Esplora soluzioni come elementi figlio del file `.R`:

![Visualizzazione espansa della stored procedure SQL con R in Esplora soluzioni](media/sql-solution-explorer-expanded.png)

`StoredProcedure.R` (in questo esempio) è il file in cui si scriverà il codice R. Il contenuto predefinito è il seguente:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

In parole semplici, il codice riceve un dataframe R denominato `InputDataSet` e restituisce i risultati in `OutputDataSet`, con il codice del modello che si limita a copiare l'input nell'output.

> [!Note]
> I nomi di questi dataframe sono controllati dai parametri `@input_data_1_name` e `@output_data_1_name` nella chiamata alla stored procedure di sistema `sp_execute_external_script`. Per altri dettagli sulla progettazione di questa convenzione di chiamata e per alcuni esempi di utilizzo, vedere [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Il rimanente codice generato all'interno di commenti è uno script di test di piccole dimensioni che usa il [pacchetto RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) per trasmettere un'istruzione SQL a SQL Server, eseguirla e recuperare il set di risultati come dataframe R. È possibile rimuovere il commento da questo codice di test per scrivere il codice R in modo interattivo a fronte del set di risultati ottenuto da SQL Server.

Nel file `StoredProcedure.Query.sql` è possibile scrivere e testare la query SQL che genera i dati per `InputDataSet`. Poiché si tratta di un file `.sql`, sono disponibili tutte le funzionalità dell'editor Transact-SQL.

Quando si ritiene soddisfacente il codice SQL, è possibile integrarlo facilmente con il codice R in `StoredProcedure.R` semplicemente trascinando il file `.sql` nell'editor aperto per il file `.R`. Nell'immagine seguente il file `StoredProcedure.Query.sql` è stato trascinato subito dopo la virgola in `sqlQuery(channel, )`:

![Lettura di un file SQL in una variabile stringa R](media/sql-reference-sql-file-from-r.png)

Come si può notare, questo semplice passaggio genera automaticamente il codice R che consente di aprire il file `.sql`, leggerne il contenuto in una stringa e passarlo al pacchetto RODBC per inviarlo a SQL Server.

A questo punto è possibile scrivere codice R in modo interattivo per modificare il dataframe `InputDataSet` in base alle esigenze. Tenere presente che è possibile selezionare codice R nell'editor e inviarlo alla [finestra interattiva](interactive-repl.md) semplicemente premendo CTRL + Invio.

`StoredProcedure.Template.sql`, infine, contiene il modello per la generazione della stored procedure SQL:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- Il segnaposto `_RCODE_` viene sostituito dal contenuto di `StoredProcedure.R`.
- Il segnaposto `_INPUT_QUERY_` viene sostituito dal contenuto di `StoredProcedure.Query.sql`.
- È necessario descrivere lo schema del set di risultati restituito dalla stored procedure modificando la clausola `WITH RESULT SETS`. Identificare in modo specifico le colonne del dataframe `OutputDataSet` che si vogliono restituire al chiamante della stored procedure. 

Ad esempio, per la query seguente:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

è possibile usare la clausola `WITH RESULT SETS` seguente per specificare i tipi di dati dei valori restituiti:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Pubblicare una stored procedure SQL

1. Selezionare il comando di menu **R Tools > Dati > Pubblica con opzioni...**.
1. Nella finestra di dialogo visualizzata modificare il valore di **Pubblica in:** in **Database**, specificare la destinazione e selezionare **Pubblica**. RTVS compilerà e pubblicherà la stored procedure:

    ![Finestra di dialogo di pubblicazione di una stored procedure](media/sql-publish-with-options.png)

1. Per pubblicare tutte le stored procedure in un progetto, è anche possibile usare il comando **R Tools > Dati > Pubblica stored procedure**, anch'esso disponibile quando si fa clic con il pulsante destro del mouse sul progetto in Esplora soluzioni.

> [!Tip]
> Se Esplora oggetti di SQL Server è aperto in Visual Studio, la stored procedure pubblicata verrà visualizzata anche nella cartella **Programmabilità > Stored procedure** del database. È anche possibile eseguirla da Esplora oggetti facendo clic con il pulsante destro del mouse e selezionando **Esegui procedura**, o chiamandola in modo interattivo da una finestra Query `.sql`.

