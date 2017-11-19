---
title: Eccezioni (Visual Studio SDK) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a0d950de8e9f91232e3526064561a7508c133b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="exception-handling-visual-studio-sdk"></a>Eccezioni (Visual Studio SDK)
Di seguito viene descritto il processo che si verifica quando vengono generate eccezioni.  
  
## <a name="exception-handling-process"></a>Processo di gestione delle eccezioni  
  
1.  Quando viene innanzitutto generata un'eccezione, ma prima che viene gestita dal gestore dell'eccezione nel programma sottoposto a debug, il motore di debug (DE) invia un [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) per la gestione di debug di sessione (SDM) come un evento di arresto. Il `IDebugExceptionEvent2` viene inviato se solo le impostazioni per l'eccezione (specificato nella finestra di dialogo eccezioni nel pacchetto di debug) specificano che l'utente desidera interrompere le notifiche di eccezioni first-chance.  
  
2.  Le chiamate SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) per ottenere la proprietà dell'eccezione.  
  
3.  Le chiamate di pacchetto di debug [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni per presentare all'utente.  
  
4.  Il pacchetto di debug viene chiesto all'utente di gestire l'eccezione, aprire una finestra di dialogo eccezioni first-chance.  
  
5.  Se l'utente sceglie di continuare, chiama il SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Se il metodo restituisce S_OK, chiama [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         -oppure-  
  
         Se il metodo restituisce S_FALSE, il programma in fase di debug viene fornita una seconda possibilità di gestire l'eccezione.  
  
6.  Se il programma sottoposto a debug non dispone di alcun gestore per un'eccezione second-chance, la Germania invia un `IDebugExceptionEvent2` per il SDM come **EVENT_SYNC_STOP**.  
  
7.  Il pacchetto di debug viene chiesto all'utente di gestire l'eccezione, aprire una finestra di dialogo eccezioni first-chance.  
  
8.  Le chiamate di pacchetto di debug [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni per presentare all'utente.  
  
9. Il pacchetto di debug viene chiesto all'utente di gestire l'eccezione, aprire una finestra di dialogo eccezione second-chance.  
  
10. Se il metodo restituisce S_OK, chiama `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)