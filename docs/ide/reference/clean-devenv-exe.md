---
title: "/Clean (devenv.exe) | Microsoft Docs"
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
  - "/clean (opzione devenv)"
  - "compilazioni [Team System], pulizia di file"
  - "clean (opzione devenv)"
  - "devenv, /clean (opzione)"
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Pulisce tutti i file intermedi e le directory di output.  
  
## Sintassi  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## Argomenti  
 `FileName`  
 Obbligatorio.  Percorso completo e nome del file di soluzione o file di progetto.  
  
 \/project `ProjName`  
 Parametro facoltativo.  Il percorso e il nome del file di progetto nella soluzione.  È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName`, il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.  
  
 \/projectconfig `ProjConfigName`  
 Parametro facoltativo.  Il nome della configurazione della build di un progetto da utilizzare per la pulizia del `/project` denominato.  
  
## Note  
 Questa opzione esegue la stessa funzione del comando di menu **Pulisci soluzione** nell'ambiente di sviluppo integrato \(IDE\).  
  
 Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
 Le informazioni di riepilogo per le pulizie e le compilazioni, compresi gli errori, vengono visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## Esempio  
 Nel primo esempio, la soluzione `MySolution` viene pulita utilizzando la configurazione predefinita specificata nel file di soluzione.  
  
 Nel secondo esempio, il progetto `CSharpConsoleApp` viene pulito utilizzando la configurazione di compilazione del progetto `Debug` all'interno della configurazione di soluzione `Debug` di `MySolution`.  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)