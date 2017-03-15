---
title: "/SafeMode (devenv.exe) | Microsoft Docs"
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
  - "/SafeMode (opzione devenv)"
  - "devenv, /SafeMode (opzione)"
  - "SafeMode (opzione)"
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Avvia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modalità sicura, caricando soltanto l'ambiente e i servizi predefiniti.  
  
## Sintassi  
  
```  
devenv /SafeMode   
```  
  
## Note  
 Questa opzione consente di evitare di caricare i package VS di altri produttori quando viene avviato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], garantendo quindi un'esecuzione stabile.  
  
## Descrizione  
 In questo esempio viene avviato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modalità sicura.  
  
## Codice  
  
```  
Devenv.exe /SafeMode  
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)