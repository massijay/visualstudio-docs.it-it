---
title: "/Out (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/out (opzione devenv)"
  - "compilazioni [Visual Studio], errori"
  - "compilazioni [Visual Studio], file di log"
  - "devenv, /out (opzione)"
  - "log degli errori [Visual Studio]"
  - "log degli errori [Visual Studio], errori durante la compilazione riga di comando"
  - "errori [Visual Studio], compilazioni"
  - "out (opzione devenv)"
  - "file di output, errori di compilazione"
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Out (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Specifica un file da archiviare e visualizza messaggi di errore quando si esegue, compila, ricompila o distribuisce una soluzione.  
  
## Sintassi  
  
```  
devenv /out FileName  
```  
  
## Argomenti  
 `FileName`  
 Obbligatorio.  Il percorso e il nome del file in cui memorizzare gli errori durante la compilazione di un eseguibile.  
  
## Note  
 Se viene specificato il nome di un file che non esiste, il file viene creato automaticamente.  Se il file esiste già, i risultati vengono aggiunti ai contenuti esistenti del file.  
  
 Gli errori di compilazione della riga di comando vengono visualizzati nella finestra di **comando** e nella visualizzazione Compilatore di soluzioni della finestra di **output**.  Questa opzione risulta utile quando si eseguono compilazioni in modalità automatica e occorre vedere i risultati.  
  
## Esempio  
 Questo esempio esegue `MySolution` e scrive gli errori nel file `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)