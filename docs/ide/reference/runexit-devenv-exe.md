---
title: "/Runexit (devenv.exe) | Microsoft Docs"
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
  - "/runexit (opzione devenv)"
  - "devenv, /runexit (opzione)"
  - "runexit (opzione devenv)"
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compila ed esegue il progetto o la soluzione specificati, quindi chiude l'ambiente di sviluppo integrato \(IDE\).  
  
## Sintassi  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## Argomenti  
 `SolutionName`  
 Obbligatorio.  Il percorso completo e il nome di un file della soluzione.  
  
 `ProjectName`  
 Obbligatorio.  Il percorso completo e il nome di un file di progetto.  
  
## Note  
 Compila ed esegue il progetto o la soluzione in base alle impostazioni specificate per la configurazione della soluzione attiva.  Specificando questa opzione, l'IDE viene ridotto a icona durante l'esecuzione del progetto o della soluzione e viene chiuso al termine dell'esecuzione del progetto o della soluzione.  
  
-   Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
-   Le informazioni di riepilogo, compresi gli errori, vengono visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene eseguita la soluzione `MySolution` nell'IDE ridotto a icona utilizzando la configurazione di distribuzione attiva, quindi viene chiuso l'IDE.  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)