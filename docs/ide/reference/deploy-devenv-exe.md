---
title: "/Deploy (devenv.exe) | Microsoft Docs"
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
  - "/deploy (opzione devenv)"
  - "deploy (opzione devenv)"
  - "distribuzione di applicazioni [Visual Studio], dopo la compilazione"
  - "devenv, /deploy (opzione)"
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Distribuisce una soluzione dopo una compilazione o una ricompilazione.  Si applica solo ai progetti di codice gestito.  
  
## Sintassi  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## Argomenti  
 `SolnConfigName`  
 Obbligatorio.  Il nome della configurazione di soluzione da utilizzare per compilare la soluzione indicata in `SolutionName`.  
  
 `SolutionName`  
 Obbligatorio.  Il percorso completo e il nome del file della soluzione.  
  
 \/project `ProjName`  
 Parametro facoltativo.  Il percorso e il nome del file di progetto nella soluzione.  È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName`, il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.  
  
 \/projectconfig `ProjConfigName`  
 Parametro facoltativo.  Il nome della configurazione della build di un progetto da utilizzare per la compilazione del `/project` denominato.  
  
## Note  
 Il progetto specificato deve essere un progetto di distribuzione.  Se il progetto specificato non è un progetto di distribuzione, quando il progetto compilato viene passato per essere distribuito viene generato un errore.  
  
 Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
 Le informazioni di riepilogo per le compilazioni, compresi gli errori, vengono visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## Esempio  
 In questo esempio viene distribuito il progetto `CSharpConsoleApp`, utilizzando la configurazione della build del progetto `Release` all'interno della configurazione di soluzione `Release` di `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)