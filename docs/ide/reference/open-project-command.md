---
title: "Comando Apri progetto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openproject"
helpviewer_keywords: 
  - "File.OpenProject (comando)"
  - "op (comando)"
  - "Apri progetto (comando)"
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Apri progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Consente di aprire un progetto esistente.  
  
## Sintassi  
  
```  
File.OpenProject filename  
```  
  
## Argomenti  
 `filename`  
 Obbligatorio.  Il percorso completo e il nome di file del progetto da aprire.  
  
 La sintassi dell'argomento `filename` richiede che i percorsi contenenti spazi siano racchiusi tra virgolette.  
  
## Note  
 La funzionalità di completamento automatico tenta di individuare il percorso e il nome di file corretti durante la digitazione.  
  
 Questo comando non è disponibile durante l'esecuzione del debug.  
  
## Esempio  
 In questo esempio viene aperto il progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] denominato Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)