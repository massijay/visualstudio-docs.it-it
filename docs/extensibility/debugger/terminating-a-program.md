---
title: "Terminare un programma | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programmi, gli eventi di chiusura"
  - "debug [Debugging SDK], terminare un programma"
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Terminare un programma
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Di seguito viene riportata una descrizione della chiusura di un unico programma con un thread.  
  
## processo di chiusura  
  
1.  Il DE invia [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)valido.  
  
2.  Il DE invia [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)valido.  
  
 L'ide entra in modalità progettazione.  Le chiamate [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) l'ambiente di runtime o del modulo di debug per rimuovere il programma dalla porta.  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)