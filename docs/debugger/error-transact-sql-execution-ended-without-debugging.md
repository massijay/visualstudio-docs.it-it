---
title: "Errore: esecuzione Transact-SQL terminata senza debug | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_sql_executed_but_not_debugged"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "SQL"
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: esecuzione Transact-SQL terminata senza debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo errore si verifica quando si tenta di eseguire il debug di una routine Transact\-SQL o SQLCLR e il debugger non riceve messaggi di debug da SQL Server.  
  
 L'errore può essere dovuto a problemi di rete o a problemi su SQL Server, ma con maggiore probabilità è dovuto a un problema di autorizzazioni.  
  
 Questo problema riguarda due account:  
  
-   L'account dell'applicazione è l'account utente utilizzato per l'esecuzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   L'account di connessione è l'identità utilizzata per effettuare la connessione a SQL Server.  Nel caso di una connessione con autenticazione SQL, questo account non corrisponde necessariamente all'identità utilizzata per l'esecuzione di Visual Studio.  
  
 Per il debug SQL è necessario che l'account dell'applicazione corrisponda a quello di connessione oppure che sia sysadmin.  
  
 Se si utilizza un account di accesso SQL quale sa, l'account dell'applicazione deve essere configurato su SQL Server come sysadmin.  Per impostazione predefinita, gli amministratori del computer sul quale è in esecuzione SQL Server sono configurati come account sysadmin.  
  
 Per correggere questo errore, è possibile:  
  
-   Verificare le impostazioni delle autorizzazioni.  Per ulteriori informazioni, vedere [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/it-it/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Assicurarsi che il debug SQL sia configurato correttamente.  
  
-   Consultare l'amministratore della rete o del database.  
  
## Vedere anche  
 [Setting Up SQL Debugging](http://msdn.microsoft.com/it-it/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/it-it/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)   
 [Debug remoto](../debugger/remote-debugging.md)