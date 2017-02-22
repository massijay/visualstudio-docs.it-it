---
title: "Eccezioni (Visual Studio SDK) | Microsoft Docs"
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
  - "debug delle eccezioni [debug SDK]"
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Eccezioni (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio seguente viene descritto il processo che si verifica quando vengono generate eccezioni.  
  
## Processo di gestione delle eccezioni  
  
1.  Quando viene primo generato, ma prima che venga gestita dal gestore di eccezioni nel programma sottoposto a debug, il motore \(DE\) di debug invia [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) gestione \(SDM\) di debug della sessione come evento bloccato.  `IDebugExceptionEvent2` viene inviato solo se le impostazioni dell'eccezione \(specificata nella finestra di dialogo eccezioni nel pacchetto di debug\) specificano che desidera arrestare sulle notifiche di eccezioni first\-chance.  
  
2.  Lo SDM chiama [IDebugExceptionEvent2:: GetException](../Topic/IDebugExceptionEvent2::GetException.md) per ottenere la proprietà dell'eccezione.  
  
3.  Il pacchetto di debug chiama [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni presentare all'utente.  
  
4.  Il pacchetto di debug richiesto all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezioni first\-chance.  
  
5.  Se l'utente sceglie di continuare, lo SDM chiama [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   se il metodo restituisce S\_OK, chiama [IDebugExceptionEvent2:: PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         In alternativa  
  
         Se il metodo restituisce S\_FALSE, il programma di cui viene eseguito il debug viene fornita una seconda vendita potrebbe di gestire l'eccezione.  
  
6.  Se il programma sottoposto a debug non ha gestori per un'eccezione second\-chance, il DE invia `IDebugExceptionEvent2` a SDM come **EVENT\_SYNCHRONIZATION\_STOP**.  
  
7.  Il pacchetto di debug richiesto all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezioni first\-chance.  
  
8.  Il pacchetto di debug chiama [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni presentare all'utente.  
  
9. Il pacchetto di debug richiesto all'utente come gestire l'eccezione aprendo una finestra di dialogo second\-chance di eccezione.  
  
10. se il metodo restituisce S\_OK, chiama `IDebugExceptionEvent2::PassToDebuggee`.  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)