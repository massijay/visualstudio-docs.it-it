---
title: "Propriet&#224; speciali degli errori restituiti da metodi asincroni di Windows Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; speciali degli errori restituiti da metodi asincroni di Windows Runtime
Può essere difficile eseguire il debug dei metodi asincroni di Windows Runtime in JavaScript, in quanto l'errore può essere generato in profondità nello stack di chiamate.  L'oggetto JavaScript `Error` dispone di proprietà aggiuntive disponibili solo quando l'errore viene generato da un metodo asincrono di Windows Runtime quando l'applicazione è in esecuzione in modalità debug.  
  
## Proprietà speciali degli errori  
 Un oggetto errore risultante da un'operazione asincrona di Windows Runtime non riuscita in modalità di debug ha le seguenti proprietà speciali:  
  
-   `asyncOpSource` \(oggetto\) Ottiene informazioni sulla posizione originale in cui la chiamata che ha generato un errore è stata eseguita.  La proprietà `asyncOpSource.originatingCall` \(stringa\) visualizza la posizione nel codice dell'utente che ha originato l'operazione asincrona.  
  
-   asyncOpType \(stringa\) Ottiene il nome del tipo di operazione asincrona che ha generato l'errore.  
  
 Per ulteriori informazioni sugli errori con le operazioni asincrone, vedere:  
  
-   [How to handle errors with promises](http://msdn.microsoft.com/it-it/01d5a901-c4ea-46f6-8005-6d39c32203eb)  
  
-   [Risoluzione degli errori di Windows Runtime](http://msdn.microsoft.com/it-it/1ef7d7df-82ac-441d-8ad0-54ab1318de64)