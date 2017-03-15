---
title: "/DebugExe (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/DebugExe [devenv.exe]"
  - "DebugExe (opzione)"
  - "devenv, /DebugExe (opzione)"
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Consente di aprire il file eseguibile specificato di cui eseguire il debug.  
  
## Sintassi  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## Argomenti  
 `ExecutableFile`  
 Obbligatorio.  Il percorso e il nome di un file .exe.  
  
 Se il file con estensione exe non viene trovato o non esiste, non viene visualizzato alcun avviso o errore e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene avviato normalmente.  
  
## Note  
 Tutte le stringhe aggiunte dopo il parametro `ExecutableFile` vengono inviate al file come argomenti.  
  
## Esempio  
 Nel seguente esempio viene aperto il file `MyApplication.exe` per eseguire il debug.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)