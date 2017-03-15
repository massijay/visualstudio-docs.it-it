---
title: "Creating and Managing Databases and Data-tier Applications in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing change, databases"
  - "database features of Visual Studio, managing change"
  - "databases, managing change"
  - "managing change, database servers"
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 37
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating and Managing Databases and Data-tier Applications in Visual Studio
> [!IMPORTANT]
>  I progetti di database inclusi nelle versioni precedenti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sono ora disponibili negli strumenti [!INCLUDE[sql_Denali_long](../data-tools/includes/sql_denali_long_md.md)].  Per ulteriori informazioni, vedere [Strumenti di sviluppo di SQL Server](http://go.microsoft.com/fwlink/?LinkId=228126).  
  
 È possibile utilizzare i progetti di database per creare nuovi database e nuove applicazioni del livello dati \(DAC\), oltre che per aggiornare database e applicazioni del livello dati esistenti.  Sia i progetti di database che i progetti DAC consentono di applicare tecniche di controllo della versione e di gestione dei progetti alle procedure di sviluppo dei database nello stesso modo in cui tali tecniche vengono applicate al codice gestito o nativo.  Per aiutare il team di sviluppo a gestire le modifiche apportate ai database e ai server database, è possibile creare un *progetto DAC*, un *progetto di database* o un *progetto server* e sottoporlo al controllo della versione.  I membri del team potranno quindi estrarre i file per apportare, compilare e testare modifiche in un *ambiente di sviluppo isolato*, detto anche sandbox, prima di condividerli con il team.  Per garantire la qualità del codice, il team può completare e sottoporre a test tutte le modifiche per una particolare versione del database in un ambiente di gestione temporanea prima che queste vengano implementate nella produzione.  
  
 Per un elenco delle funzionalità di database supportate dalle applicazioni livello dati, vedere [Funzionalità supportate nelle applicazioni livello dati](http://go.microsoft.com/fwlink/?LinkId=164239) il sito Web Microsoft.  Se si utilizzano funzionalità di database non supportate dalle applicazioni del livello dati, è necessario invece utilizzare un progetto di database per gestire le modifiche apportate al database.  
  
## Attività comuni di alto livello  
  
|Attività di alto livello|Contenuto di supporto|  
|------------------------------|---------------------------|  
|**Avviare lo sviluppo di un'applicazione del livello dati:** la DAC è un nuovo concetto introdotto con [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] che contiene la definizione per un database di [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] e gli oggetti istanza di supporto utilizzati da un'applicazione client\-server o in 3 livelli.  In un progetto DAC sono inclusi oggetti di database, ad esempio tabelle e visualizzazioni, insieme a entità di istanza quali gli accessi.  È possibile utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per creare un progetto DAC, compilare un file di pacchetto DAC e inviare tale file a un amministratore del database per la distribuzione in un'istanza del motore di database di [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Creazione e gestione delle applicazioni livello dati](http://go.microsoft.com/fwlink/?LinkId=160741) \(sito Web Microsoft\)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Esecuzione di uno sviluppo iterativo del database:** se si è uno sviluppatore o un tester, si estraggono parti del progetto per poi aggiornarle in un ambiente di sviluppo isolato.  Utilizzando questo tipo di ambiente, è possibile verificare le modifiche senza influire su altri membri del team.  Una volta completate le modifiche, i file vengono nuovamente archiviati nel controllo della versione, dove gli altri membri del team possono ottenere le modifiche nonché compilarle e distribuirle in un server di test.|-   [query e editor di testo \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Sito Web Microsoft\)<br />-   [Debugger Transact\-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) \(Sito Web Microsoft\)|  
|**Creazione di prototipi, verifica dei risultati dei test e modifica di script e oggetti di database:** è possibile utilizzare l'editor [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] per eseguire queste attività comuni.|-   [query e editor di testo \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Sito Web Microsoft\)|