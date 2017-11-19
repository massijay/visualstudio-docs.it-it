---
title: 'Errore: Utente potrebbe non eseguire la Stored Procedure sp_enable_sql_debug | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.sqlde_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ab29925b12bfb14ba8f37d371c30aa6f312ea15
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Errore: l'utente non può eseguire la stored procedure sp_enable_sql_debug
Non è possibile eseguire la stored procedure sp_enable_sql_debug sul server. Questo errore può essere causato da:  
  
-   Un problema di connessione. È necessario disporre di una connessione stabile al server.  
  
-   Mancanza delle autorizzazioni necessarie sul server. Per eseguire il debug in SQL Server 2005, sia l'account con cui viene eseguito Visual Studio che quello utilizzato per la connessione a SQL Server devono essere membri del ruolo sysadmin. L'account utilizzato per la connessione a SQL Server può essere l'account utente di Windows, se si utilizza l'autenticazione di Windows, oppure un account con ID utente e password, se si utilizza l'autenticazione SQL.  
  
 Per ulteriori informazioni, vedere [procedura: impostare autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: impostare autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Impostazione del debug SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)