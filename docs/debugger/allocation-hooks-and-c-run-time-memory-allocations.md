---
title: "Hook di allocazione e allocazioni di memoria di runtime C | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "hook di allocazione"
  - "debug [C++], funzioni hook"
  - "hook, allocazione"
  - "allocazione di memoria, risoluzione dei problemi degli hook di allocazione"
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Hook di allocazione e allocazioni di memoria di runtime C
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una restrizione molto importante che riguarda le funzioni hook di allocazione è che esse devono esplicitamente ignorare i blocchi `_CRT_BLOCK` \(le allocazioni di memoria effettuate internamente dalle funzioni dalla libreria di runtime del linguaggio C\) se tali blocchi effettuano chiamate a funzioni della libreria di runtime del linguaggio C che allocano memoria interna.  È possibile far sì che i blocchi `_CRT_BLOCK` vengano ignorati includendo, all'inizio della funzione hook di allocazione, un codice del seguente tipo:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Se la funzione hook di allocazione non ignora i blocchi `_CRT_BLOCK`, qualsiasi funzione della libreria di runtime del linguaggio C chiamata nella funzione hook rischia di intrappolare il programma in un ciclo senza termine.  Ad esempio, `printf` crea un'allocazione interna.  Se il codice hook chiama `printf`, l'allocazione effettuata farà sì che la funzione hook venga nuovamente chiamata ed essa chiamerà a sua volta nuovamente **printf** e così via fino all'overflow dello stack.  Se è necessario segnalare le operazioni di allocazione `_CRT_BLOCK`, un modo per ovviare a questa limitazione consiste nell'utilizzare funzioni API Windows, anziché funzioni di runtime del linguaggio C, per la formattazione e l'output.  Dal momento che le API Windows non utilizzano l'heap della libreria di runtime del linguaggio C, esse non bloccheranno la funzione hook di allocazione in un ciclo senza termine.  
  
 Se si esaminano i file di origine della libreria di runtime, si noterà che la funzione hook di allocazione predefinita, **CrtDefaultAllocHook** \(che restituisce semplicemente **TRUE**\) si trova in un file separato, DBGHOOK.C.  Se si desidera che l'hook di allocazione venga chiamato anche per le allocazioni effettuate dal codice di avvio di runtime, che viene eseguito prima della funzione **main** dell'applicazione, è possibile sostituire questa funzione predefinita con una personalizzata, anziché utilizzare [\_CrtSetAllocHook](/visual-cpp/c-runtime-library/reference/crtsetallochook).  
  
## Vedere anche  
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/it-it/21e1346a-6a17-4f57-b275-c76813089167)