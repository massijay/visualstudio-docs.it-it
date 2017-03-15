---
title: Thread | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6faced71ba03bcf1c4bf1849515bdf7b4fe455f8
ms.lasthandoff: 02/22/2017

---
# <a name="threads"></a>Thread
In termini di architettura debugger, un **thread**:  
  
-   È l'unità fondamentale di calcolo. Un thread esegue in sequenza le istruzioni all'interno del contesto di uno stack di chiamate singolo, spostamento dal contesto di un codice a quella successiva.  
  
-   Consente di identificare se stesso e il programma è in esecuzione e può essere denominato, sospensione e ripresa. Un thread può enumerare frame dello stack associato e, in alcune condizioni, può essere spostato in un altro stack frame. Dato il contesto di uno stack frame, un thread può restituire relativo thread logici associati, se presente. Un thread dispone di proprietà, ad esempio un conteggio di sospensione, che possono essere visualizzati nella finestra thread dell'IDE.  
  
-   È rappresentato da un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaccia, in genere creata da un motore di debug (DE) o una macchina virtuale come conseguenza l'esecuzione di un programma.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Il motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Gestione sessione di Debug](../../extensibility/debugger/session-debug-manager.md)
