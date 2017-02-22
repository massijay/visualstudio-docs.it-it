---
title: "/Edit (devenv.exe) | Microsoft Docs"
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
  - "/Edit (opzione devenv)"
  - "devenv, opzione /edit"
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Apre il file specificato nell'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintassi  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## Argomenti  
 `file1`  
 Parametro facoltativo.  Il file da aprire nell'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Se non esiste alcuna istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], viene creata una nuova istanza con un layout di finestra semplificato e viene aperto `file1` nella nuova istanza.  
  
 `file2`  
 Parametro facoltativo.  Uno o più file aggiuntivi da aprire nell'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Note  
 Se non è specificato alcun file ed esiste un'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] riceve lo stato attivo.  Se non è specificato alcun file e non esiste alcuna istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], viene creata una nuova istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con un layout di finestra semplificato.  
  
 Se l'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è in uno stato modale, ad esempio se è aperta la [finestra di dialogo Opzioni](../../ide/reference/options-dialog-box-visual-studio.md) il file verrà aperto nell'istanza esistente quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esce dallo stato modale.  
  
## Esempio  
 In questo esempio il file `MyFile.cs` viene aperto in un'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oppure in una nuova istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se non ne esiste ancora una.  
  
```  
devenv /edit MyFile.cs  
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)