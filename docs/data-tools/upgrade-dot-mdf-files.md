---
title: "Procedura: eseguire l&#39;aggiornamento a LocalDB o continuare con SQL Server Express | Microsoft Docs"
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
  - "LocalDB"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQLEXPRESS"
  - "aggiornamento di SQLExpress a SQLExpress"
  - "aggiornamento a LocalDB"
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 33
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: eseguire l&#39;aggiornamento a LocalDB o continuare con SQL Server Express
In questo argomento vengono descritte le opzioni per il miglioramento del file di database \(mdf\) dopo l'installazione [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] e include istruzioni per le attività seguenti:  
  
-   Migliori un file di database per utilizzare LocalDB  
  
-   Migliori un file di database per utilizzare una versione più recente di SQL Server Express  
  
-   Il lavoro con un file di database in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ma conserva la compatibilità con [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]  
  
-   Impostare su SQL Server Express il motore di database predefinito  
  
 È possibile utilizzare [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] per aprire un progetto che contiene un file di database \(mdf\) creato in una versione precedente di SQL Server Express.  Tuttavia, per continuare a sviluppare il progetto in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], è necessario uno che tale versione di SQL Server Express installato nello stesso computer di Visual Studio, oppure è necessario aggiornare il file di database per utilizzare SQL Server Express LocalDB.  Se si aggiorna il file di database, non sarà possibile accedervi con le versioni precedenti di SQL Server Express.  
  
 È inoltre possibile che venga richiesto di aggiornare un file di database creato tramite [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)] la versione di file non è compatibile con l'istanza di SQL Server Express attualmente installata.  Per risolvere il problema, verrà richiesto di aggiornare il file alla versione più recente di SQL Server Express.  
  
> [!IMPORTANT]
>  È consigliabile si esegue il backup del file di database prima di aggiornare.  
  
 Prima di aggiornare un database, è opportuno considerare i seguenti criteri:  
  
-   Non migliori se si desidera lavorare al progetto sia in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] che in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
-   Non aggiornare se l'applicazione verrà utilizzata negli ambienti che utilizzano SQL Server Express anziché LocalDB.  
  
-   Non aggiornare se l'applicazione utilizza le connessioni remote perché non LocalDB le accetta.  
  
-   Non aggiornare se l'applicazione si basa su Internet Information Services \(IIS\).  
  
-   Si consiglia di aggiornare se si desidera limitare le applicazioni di database di test in un ambiente del sandbox ma non si desidera amministrare un database.  
  
### Per aggiornare un file di database per utilizzare LocalDB  
  
1.  In **Esplora server**, scegliere il pulsante **Connetti al database**.  
  
2.  Nella finestra di dialogo **Aggiungi connessione**, specificare le seguenti informazioni:  
  
    -   **origine dati:** Microsoft SQL Server \(SqlClient\)  
  
    -   **Nome del server:** \) \\ V11.0 \(LocalDB  
  
    -   **Allegare un file di database:** *percorso*, dove *percorso* è il percorso fisico del file primario mdf.  
  
    -   **nome logico:** *Nome* *Nome*, dove è il nome che si desidera utilizzare con il file.  
  
3.  Scegliere il pulsante **Scegliere OK**.  
  
4.  Quando richiesto, selezionare il pulsante **Sì** per aggiornare il file.  
  
 Il database viene aggiornato, connesso al motore di database di LocalDB e più compatibile con [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)].  
  
 È inoltre possibile modificare la connessione di SQLExpress per utilizzare LocalDB aprendo il menu di scelta rapida per la connessione e scegliendo **Modifica connessione**.  In **Modifica connessione** finestra di dialogo, cambiano nome del server a\) \\ v11.0 \(LocalDB.  Nella finestra di dialogo **Proprietà avanzate**, assicurarsi che **Istanza utente** sia impostata su False.  
  
### Per eseguire l'aggiornamento a una versione più recente di SQL Server Express  
  
1.  Nel menu di scelta rapida per la connessione al database, scegliere **Modifica connessione**.  
  
2.  Nella finestra di dialogo **Modifica connessione**, scegliere il pulsante **Avanzate**.  
  
3.  Nella finestra di dialogo **Proprietà avanzate**, scegliere il pulsante **Scegliere OK** senza modificare il nome del server.  
  
 Il file di database viene aggiornato in base alla versione corrente [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)].  
  
### Per utilizzare il database in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ma mantenere la compatibilità con [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]  
  
1.  In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], aprire il progetto senza aggiornarla.  
  
    -   Per eseguire il progetto, scegliere il tasto F5.  
  
    -   Per modificare il database, aprire il file con estensione mdf in **Esplora soluzioni**ed espandere il nodo in **Esplora server** per utilizzare il database come apportate in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
### Per rendere SQL Server Express il motore di database predefinito  
  
1.  Sulla barra dei menu, scegliere **Strumenti**, **Opzioni**.  
  
2.  Nella finestra di dialogo **Opzioni**, espandere le opzioni **strumenti di dati** quindi selezionare il nodo **Connessioni dati**.  
  
3.  Nella casella di testo **Nome dell'istanza di SQL Server**, specificare il nome dell'istanza di SQL Server Express che si desidera utilizzare.  Se l'istanza non è denominata, specificare `. \ SQLEXPRESS`.  
  
4.  Scegliere il pulsante **Scegliere OK**.  
  
 SQL Server Express sarà il motore di database predefinito per le applicazioni.  
  
## Vedere anche  
 [Cenni preliminari sui dati locali](../data-tools/local-data-overview.md)   
 [Procedura dettagliata: connessione ai dati in un file di database lodale \(Windows Form\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)