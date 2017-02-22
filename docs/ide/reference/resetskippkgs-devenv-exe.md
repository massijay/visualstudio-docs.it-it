---
title: "/ResetSkipPkgs (devenv.exe) | Microsoft Docs"
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
  - "/ResetSkipPkgs (opzione devenv)"
  - "devenv, /ResetSkipPkgs (opzione)"
  - "ResetSkipPkgs (opzione)"
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Deseleziona tutte le opzioni per evitare i carichi aggiunti ai package VS da utenti che desiderano evitare di caricare package VS, quindi avvia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintassi  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## Note  
 La presenza di un tag SkipLoading disabilita il caricamento di Package VS; cancellando il tag, viene riabilitato il caricamento di Package VS.  
  
## Esempio  
 Nel seguente esempio vengono cancellati i tag SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)