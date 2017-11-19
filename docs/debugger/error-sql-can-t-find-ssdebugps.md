---
title: "Errore: SQL può &#39; t trova SSDEBUGPS | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a437cfc4be1c9168b16e4b9d1a46e2eadcb2e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Errore: SQL può &#39; t trova SSDEBUGPS
SSDEBUGPS.dll è il componente host di SQL Server per il debug.  
  
 Questo errore si verifica quando si tenta di avviare il debug e indica che il file specificato non è presente sul computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. È possibile che la funzionalità per il debug remoto non sia mai stata installata oppure che il file sia stato eliminato accidentalmente.  
  
 Esistono due modi per risolvere questo errore: eseguendo nuovamente il programma di installazione di debug remoto e copiare il file nel [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] macchina.  
  
 Eseguire nuovamente l'installazione del debug remoto, seguire le istruzioni in [il debug remoto](../debugger/remote-debugging.md).  
  
 Se non è possibile individuare una copia di ssdebugps.dll, è possibile copiarlo nel [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] macchina. Se presente, il file si trova nella directory \Programmi\File comuni\Microsoft Shared\SQL Debugging. È possibile trovarlo in un altro [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] computer o in un computer dotato di [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] installato.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Per copiare SSDEBUGPS.dll nel computer SQL Server 2005  
  
1.  Copiare il file nella directory con lo stesso nome e percorso sul [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] macchina.  
  
2.  Effettuare la registrazione aprendo una **prompt dei comandi**ed eseguire il comando seguente:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```