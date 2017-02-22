---
title: "Funzioni hook del blocco client | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtSetDumpClient (funzione)"
  - "blocchi client, funzioni hook"
  - "blocchi client, convalida e segnalazione di dati"
  - "debug [C++], funzioni hook"
  - "hook, blocco client"
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funzioni hook del blocco client
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si desidera convalidare o inserire in report il contenuto dei dati memorizzati in blocchi `_CLIENT_BLOCK`, sarà possibile scrivere una funzione specificamente per tale scopo.  Tale funzione dovrà avere un prototipo analogo al seguente, come definito in CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 In altri termini, la funzione hook dovrà accettare un puntatore **void** all'inizio dell'argomento del blocco di allocazione, insieme a un valore di tipo **size\_t** che indica la dimensione dell'allocazione, e restituire un valore `void`.  Non esistono altre limitazioni al contenuto.  
  
 Dopo aver installato la funzione hook mediante [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient), essa verrà chiamata ogni volta che viene effettuato il dump di un blocco `_CLIENT_BLOCK`.  Sarà quindi possibile utilizzare [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) per ottenere informazioni sul tipo o sul sottotipo dei blocchi di cui è stato effettuato il dump.  
  
 Il puntatore alla funzione che viene passato a `_CrtSetDumpClient` è del tipo **\_CRT\_DUMP\_CLIENT**, come definito in CRTDBG.H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## Vedere anche  
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/it-it/21e1346a-6a17-4f57-b275-c76813089167)   
 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)