---
title: Terminare un programma | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef92896ebdb847dd16e00911dc49b53d9ceb5877
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="terminating-a-program"></a>Terminare un programma
Di seguito è una descrizione della chiusura di un programma con un thread singolo.  
  
## <a name="termination-process"></a>Processo di terminazione  
  
1.  Invia il DE un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un valore valido [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  Invia il DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un valore valido [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 L'IDE passa alla modalità progettazione. Il motore di debug o di un ambiente di runtime chiama [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) per rimuovere il programma dalla porta.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)