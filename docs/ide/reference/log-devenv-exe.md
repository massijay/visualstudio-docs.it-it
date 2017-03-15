---
title: "/Log (devenv.exe) | Microsoft Docs"
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
  - "/Log (opzione devenv)"
  - "devenv, /Log (opzione)"
  - "Log (opzione) [devenv.exe]"
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Log (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Registra tutte le attività nel file di log per la risoluzione dei problemi.  Il file verrà visualizzato dopo aver chiamato `devenv /log` almeno una volta.  Per impostazione predefinita, il file di log è:  
  
 *%APPDATA%*\\Microsoft\\VisualStudio\\*Versione*\\ActivityLog.xml  
  
 dove *Versione* indica la versione di Visual Studio.  È tuttavia possibile specificare un percorso e un nome di file diversi.  
  
## Sintassi  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## Note  
 Questa opzione deve apparire alla fine della riga di comando, dopo tutte le altre opzioni.  
  
 Il log viene scritto per tutte le istanze di Visual Studio richiamate con l'opzione \/log.  Non vengono registrate le istanze di Visual Studio richiamate senza l'opzione \/log.  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)