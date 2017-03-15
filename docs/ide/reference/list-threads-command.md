---
title: "Comando Elenca thread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listthreads"
helpviewer_keywords: 
  - "Debug.ListThreads (comando)"
  - "Elenca thread (comando)"
  - "ListThreads (comando)"
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Comando Elenca thread
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visualizza un elenco dei thread del programma corrente.  
  
## Sintassi  
  
```  
Debug.ListThreads [index]  
```  
  
## Argomenti  
 `index`  
 Parametro facoltativo.  Seleziona un thread in base al relativo indice da impostare come thread corrente.  
  
## Note  
 Se specificato, l'argomento `index` contrassegna il thread indicato come thread corrente.  Il thread corrente viene indicato nell'elenco con un asterisco \(\*\).  
  
## Esempio  
  
```  
>Debug.ListThreads   
```  
  
## Vedere anche  
 [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)   
 [Comando Elenca disassembly](../../ide/reference/list-disassembly-command.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)