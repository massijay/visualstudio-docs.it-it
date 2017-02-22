---
title: "Chiusura e disconnessione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programmi, gli eventi di chiusura"
  - "motori di debug, la disconnessione da programmi"
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Chiusura e disconnessione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio seguente viene illustrata la terminazione normale.  
  
## Descrizione  
 Dopo [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) l'interfaccia continua, se non sono presenti punti di interruzione, eccezioni, errori di runtime, o cicli infiniti nell'applicazione di cui eseguire il debug, il programma sottoposto a debug verrà eseguita fino al completamento.  Si tratta di terminazione normale.  
  
 È necessario inviare [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) per implementare la terminazione normale.  È quindi necessario implementare il metodo di [IDebugProgramDestroyEvent2:: GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md) .  
  
## Vedere anche  
 [Creazione di un motore di Debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)