---
title: "Errore: l&#39;utente non pu&#242; eseguire la stored procedure sp_enable_sql_debug | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_accessdenied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Errore: l&#39;utente non pu&#242; eseguire la stored procedure sp_enable_sql_debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Non è possibile eseguire la stored procedure sp\_enable\_sql\_debug sul server.  Questo errore può essere causato da:  
  
-   Un problema di connessione.  È necessario disporre di una connessione stabile al server.  
  
-   Mancanza delle autorizzazioni necessarie sul server.  Per eseguire il debug in SQL Server 2005, sia l'account con cui viene eseguito Visual Studio che quello utilizzato per la connessione a SQL Server devono essere membri del ruolo sysadmin.  L'account utilizzato per la connessione a SQL Server può essere l'account utente di Windows, se si utilizza l'autenticazione di Windows, oppure un account con ID utente e password, se si utilizza l'autenticazione SQL.  
  
 Per ulteriori informazioni, vedere [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/it-it/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## Vedere anche  
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/it-it/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Setting Up SQL Debugging](http://msdn.microsoft.com/it-it/3db09e68-edcc-42de-9c22-4e97cfd55ab3)