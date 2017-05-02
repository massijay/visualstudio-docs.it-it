---
title: "Utilizzo di Windows Runtime in JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows Runtime"
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Utilizzo di Windows Runtime in JavaScript
Quando si scrive un'app per [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] o Windows Phone Store in JavaScript, è possibile usare le classi, i metodi e le proprietà di Windows Runtime in modo analogo all'uso di oggetti, metodi e proprietà nativi di JavaScript.  Questo argomento include informazioni introduttive e collegamenti ad argomenti esplicativi sui concetti di base dell'uso di API di Windows Runtime in JavaScript, inclusa una spiegazione del modo in cui sono rappresentati i tipi di Windows Runtime, di come usare i metodi asincroni di Windows Runtime e come rimanere in ascolto di e gestire eventi di Windows Runtime.  
  
 Per documentazione di riferimento su JavaScript, vedere [Riferimento al linguaggio JavaScript](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Le funzionalità di Windows Runtime non sono disponibili per app eseguite in Internet Explorer.  
  
## Documentazione di riferimento per Windows Runtime  
 Per documentazione di riferimento, vedere [Windows Runtime reference](http://msdn.microsoft.com/it-it/8fe97dbf-8cd4-435f-b481-9e83d0519f9e).  Esempi di codice sono disponibili in JavaScript e anche in C\+\+, C\# e Visual Basic.  
  
## Scrittura di componenti di Windows Runtime Components in C\+\+, C\# o Visual Basic  
 Per istruzioni e indicazioni sulla scrittura di componenti di Windows Runtime che possono essere usati in JavaScript, vedere [Creazione di componenti Windows Runtime](../Topic/Creating%20Windows%20Runtime%20Components.md).  
  
## Convenzioni relative alla combinazione di maiuscole e minuscole con funzionalità di Windows Runtime  
 Le convenzioni relative alla combinazione di maiuscole e minuscole per le funzionalità di Windows Runtime in JavaScript sono leggermente diverse rispetto a quelle per gli altri linguaggi:  
  
-   Gli spazi dei nomi e le classi sono definiti in base alla convezione Pascal:  
  
    ```javascript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Per i membri delle classi, inclusi i metodi e le proprietà, e i membri di strutture ed enumerazioni devono essere usati solo lettere minuscole:  
  
    ```javascript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Per i nomi degli eventi devono essere usati caratteri minuscoli:  
  
    ```javascript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## Vedere anche  
 [Considerazioni sull'utilizzo dell'API Windows Runtime](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Utilizzo di metodi asincroni di Windows Runtime](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Gestione di eventi di Windows Runtime in JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Rappresentazione JavaScript dei tipi di Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Proiezione JavaScript di DateTime e TimeSpan di Windows Runtime](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)