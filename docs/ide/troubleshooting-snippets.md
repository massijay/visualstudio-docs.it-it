---
title: "Risoluzione dei problemi relativi ai frammenti di codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "frammenti di codice IntelliSense, risoluzione dei problemi"
  - "risoluzione dei problemi dei frammenti di codice IntelliSense"
  - "risoluzione dei problemi in Visual Basic, frammenti di codice IntelliSense"
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Risoluzione dei problemi relativi ai frammenti di codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I problemi relativi ai frammenti di codice IntelliSense sono in genere causati da due fattori: un file frammento danneggiato o contenuto non valido nel file frammento.  
  
## Problemi comuni  
  
### Il frammento non può essere trascinato da Esplora file in un file di origine Visual Studio  
  
-   È possibile che l'XML nel file frammento sia danneggiato.  L'**Editor XML** di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di individuare i problemi nella struttura XML.  
  
-   È possibile che il file frammento non sia conforme allo schema del frammento.  L'**Editor XML** di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di individuare i problemi nella struttura XML.  
  
### Il codice contiene errori del compilatore non evidenziati  
  
-   È possibile che manchi un riferimento al progetto.  Esaminare la documentazione relativa al frammento.  Se il riferimento non si trova sul computer, sarà necessario installarlo.  Inserendo un frammento, verranno aggiunti al progetto tutti i riferimenti necessari.  L'eventuale mancanza delle informazioni di riferimento nel frammento può essere segnalata come errore al creatore del frammento.  
  
-   È possibile che una variabile non sia definita.  Le variabili non definite in un frammento dovrebbero essere evidenziate.  In caso contrario, è possibile segnalarlo come errore al creatore del frammento.  
  
## Vedere anche  
 [Frammenti di codice](../ide/code-snippets.md)