---
title: "/Run (devenv.exe) | Microsoft Docs"
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
  - "/r (opzione devenv)"
  - "/run (devenv)"
  - "applicazioni [Visual Studio], esecuzione"
  - "devenv, /run (opzione)"
  - "/r (opzione devenv)"
  - "run (opzione devenv)"
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Run (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compila ed esegue il progetto o la soluzione specificati.  
  
## Sintassi  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## Argomenti  
 `SolutionName`  
 Obbligatorio.  Il percorso completo e il nome di un file della soluzione.  
  
 `ProjectName`  
 Obbligatorio.  Il percorso completo e il nome di un file di progetto.  
  
## Note  
 Compila ed esegue il progetto o la soluzione in base alle impostazioni specificate per la configurazione della soluzione attiva.  Questa opzione avvia l'ambiente di sviluppo integrato \(IDE\) e lo mantiene attivo fino al completamento dell'esecuzione del progetto o della soluzione.  
  
-   Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
-   Le informazioni di riepilogo, compresi gli errori, vengono visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene eseguita la soluzione `MySolution` utilizzando la configurazione di distribuzione attiva.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Runexit](../../ide/reference/runexit-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)