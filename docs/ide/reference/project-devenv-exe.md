---
title: "/Project (devenv.exe) | Microsoft Docs"
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
  - "/project (opzione devenv)"
  - "progetti di distribuzione, specifica"
  - "devenv, /project (opzione)"
  - "/project (opzione devenv)"
  - "progetti [Visual Studio], compilazione"
  - "progetti [Visual Studio], pulizia"
  - "progetti [Visual Studio], ricompilazione"
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Project (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Identifica un singolo progetto all'interno della configurazione di soluzione specificata da compilare, pulire, ricompilare o distribuire.  
  
## Sintassi  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## Argomenti  
 \/build  
 Compila il progetto specificato da `/project` `ProjName`.  
  
 \/clean  
 Pulisce tutti i file intermedi e le directory di output creati durante una compilazione.  
  
 \/rebuild  
 Pulisce e ricompila il progetto specificato da `/project` `ProjName`.  
  
 \/deploy  
 Specifica che il progetto deve essere distribuito dopo una compilazione o una ricompilazione.  
  
 `SolnConfigName`  
 Obbligatorio.  Il nome della configurazione di soluzione da applicare alla soluzione indicata in `SolutionName`.  
  
 `SolutionName`  
 Obbligatorio.  Il percorso completo e il nome del file della soluzione.  
  
 \/project `ProjName`  
 Parametro facoltativo.  Il percorso e il nome del file di progetto nella soluzione.  È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName`, il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.  
  
 \/projectconfig `ProjConfigName`  
 Parametro facoltativo.  Il nome della configurazione della build di un progetto da applicare al `/project` denominato.  
  
## Note  
  
-   Deve essere utilizzata parte di un comando `devenv /build`, \/`clean`, `/rebuild` o `/deploy`.  
  
-   Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
-   Le informazioni di riepilogo per le compilazioni, compresi gli errori, vengono visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## Esempio  
 In questo esempio viene compilato il progetto `CSharpConsoleApp`, utilizzando la configurazione della build del progetto `Debug` all'interno della configurazione di soluzione `Debug` di `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)