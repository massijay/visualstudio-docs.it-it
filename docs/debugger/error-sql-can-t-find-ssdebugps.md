---
title: "Errore: SQL non trova SSDEBUGPS | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_cant_find_ssdebugps"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "SQL"
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: SQL non trova SSDEBUGPS
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

SSDEBUGPS.dll è il componente host di SQL Server per il debug.  
  
 Questo errore si verifica quando si tenta di avviare il debug e indica che il file specificato non è presente sul computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].  È possibile che la funzionalità per il debug remoto non sia mai stata installata oppure che il file sia stato eliminato accidentalmente.  
  
 Per risolvere l'errore è possibile eseguire nuovamente l'installazione della funzionalità per il debug remoto oppure copiare il file nel computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].  
  
 Per ripetere l'installazione, seguire le istruzioni riportate in [Debug remoto](../debugger/remote-debugging.md).  
  
 Se è disponibile una copia di ssdebugps.dll, è possibile copiare il file nel computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].  Se presente, il file si trova nella directory \\Programmi\\File comuni\\Microsoft Shared\\SQL Debugging.  È possibile trovarlo in un altro computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] oppure in un computer in cui è installato [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
### Per copiare SSDEBUGPS.dll nel computer SQL Server 2005  
  
1.  Copiare il file nella directory con lo stesso nome e percorso sul computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].  
  
2.  Effettuare la registrazione aprendo una finestra del **prompt dei comandi** ed eseguendo il seguente comando:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```