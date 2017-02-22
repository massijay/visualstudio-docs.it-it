---
title: "/Rebuild (devenv.exe) | Microsoft Docs"
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
  - "/rebuild (opzione devenv)"
  - "applicazioni [Visual Studio], ricompilazione"
  - "devenv, /rebuild (opzione)"
  - "progetti [Visual Studio], ricompilazione"
  - "/rebuild (opzione devenv)"
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Elimina e ricompila la configurazione della soluzione specificata.  
  
## Sintassi  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## Argomenti  
 `SolnConfigName`  
 Necessario.  Il nome della configurazione di soluzione da utilizzare per ricompilare la soluzione indicata in `SolutionName`.  
  
 `SolutionName`  
 Necessario.  Il percorso completo e il nome del file della soluzione.  
  
 \/project `ProjName`  
 Opzionale.  Il percorso e il nome del file di progetto nella soluzione.  È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName`, il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.  
  
 \/projectconfig `ProjConfigName`  
 Opzionale.  Il nome della configurazione della build di un progetto da utilizzare per la ricompilazione del `/project` denominato.  
  
## Note  
  
-   Questa opzione esegue la stessa funzione del comando di menu **Ricompila soluzione** nell'ambiente di sviluppo integrato \(IDE\).  
  
-   Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
-   Le informazioni di riepilogo per le pulizie e le compilazioni, compresi gli errori, vengono visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## Esempio  
 In questo esempio viene pulito e ricompilato il progetto `CSharpWinApp`, utilizzando la configurazione della build del progetto `Debug` all'interno della configurazione di soluzione `Debug` di `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)