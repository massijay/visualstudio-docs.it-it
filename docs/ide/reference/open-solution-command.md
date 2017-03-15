---
title: "Comando Apri soluzione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.opensolution"
helpviewer_keywords: 
  - "File.OpenSolution (comando)"
  - "Apri soluzione (comando)"
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Comando Apri soluzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Apre una soluzione esistente, chiudendo le altre soluzioni eventualmente aperte.  
  
## Sintassi  
  
```  
File.OpenSolution filename  
```  
  
## Argomenti  
 `Filename`  
 Obbligatorio.  Il percorso completo e il nome di file della soluzione da aprire.  
  
 La sintassi dell'argomento `filename` richiede che i percorsi contenenti spazi siano racchiusi tra virgolette.  
  
## Note  
 La funzionalità di completamento automatico tenta di individuare il percorso e il nome di file corretti durante la digitazione.  
  
## Esempio  
 Nell'esempio riportato di seguito viene aperta la soluzione Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)