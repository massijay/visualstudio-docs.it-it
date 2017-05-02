---
title: "Variabili di compilazione condizionale (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "compilazione condizionale, variabili"
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Variabili di compilazione condizionale (JavaScript)
Di seguito sono riportate le variabili predefinite disponibili per la compilazione condizionale.  Se la variabile non è **true**, non è definita e si comporta come `NaN` quando vi si accede.  
  
> [!WARNING]
>  La compilazione condizionale è supportata in tutte le versioni di Internet Explorer precedenti a Internet Explorer 11.  A partire dalla modalità standard di Internet Explorer 11 e nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] la compilazione condizionale non è supportata.  
  
## Variabili  
  
|Variabile|Descrizione|  
|---------------|-----------------|  
|@\_win32|True se in esecuzione in un sistema Win32.|  
|@\_win16|True se in esecuzione in un sistema Win16.|  
|@\_mac|True se in esecuzione in un sistema Apple Macintosh.|  
|@\_alpha|True se in esecuzione in un processore DEC Alpha.|  
|@\_x86|True se in esecuzione in un processore Intel.|  
|@\_mc680x0|True se in esecuzione in un processore Motorola 680x0.|  
|@\_PowerPC|True se in esecuzione in un processore Motorola PowerPC.|  
|@\_jscript|Sempre true.|  
|@\_jscript\_build|Contiene il numero di build del motore di script di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
|@\_jscript\_version|Contiene il numero di versione di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] in formato maggiore.minore.|