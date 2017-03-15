---
title: "Security of Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, security"
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# Security of Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Di seguito sono elencati i problemi di sicurezza associati all'utilizzo dei modelli di testo:  
  
-   I modelli di testo sono vulnerabili agli inserimenti di codice arbitrario.  
  
-   Se il meccanismo utilizzato dall'host per trovare un processore di direttiva non è sicuro, potrebbe essere eseguito un processore di direttiva dannoso.  
  
## Codice arbitrario  
 Quando si scrive un modello, è possibile inserire qualsiasi codice all'interno dei tag \< \#\#\>.  Questo consente l'esecuzione di codice arbitrario dall'interno di un modello di testo.  
  
 È importante assicurarsi di ottenere modelli da fonti attendibili.  Assicurarsi di avvertire gli utenti finali dell'applicazione di non eseguire modelli che non provengono da fonti attendibili.  
  
## Processore di direttiva dannoso  
 Il motore del modello di testo interagisce con un host di trasformazione e uno o più processori di direttiva per trasformare il testo del modello in un file di output.  Per ulteriori informazioni, vedere [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).  
  
 Se il meccanismo utilizzato dall'host per trovare un processore di direttiva non è sicuro, si corre il rischio che venga eseguito un processore di direttiva dannoso.  Il processore di direttiva dannoso potrebbe fornire codice che viene eseguito nella modalità `FullTrust` quando viene eseguito il modello.  Se si crea un host di trasformazione del modello di testo personalizzato, è necessario utilizzare un meccanismo sicuro, quale il Registro di sistema, per consentire al motore di individuare dei processori di direttiva.