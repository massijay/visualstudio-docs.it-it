---
title: "Controllo di esecuzione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], controllo di esecuzione"
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Controllo di esecuzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il motore \(DE\) di debug in genere invia uno dei seguenti eventi come ultimo evento startup:  
  
-   L'evento del punto di ingresso, se connessione a un programma appena avviato  
  
-   L'evento completo di caricamento, se connessione a un programma già in esecuzione  
  
 Entrambi questi eventi sono interrompendo gli eventi, quindi attende di DE una risposta dall'utilizzo dell'IDE.  Per ulteriori informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md).  
  
## Arrestare evento  
 Quando un evento bloccato viene inviato alla sessione di debug:  
  
1.  Il programma e il thread che contengono il puntatore all'istruzione corrente possono essere ottenuti dall'interfaccia eventi.  
  
2.  L'ide determina che presentano file di codice sorgente e posizione, che visualizza evidenziato nell'editor.  
  
3.  La sessione di debug in genere risponde al primo evento bloccato chiamando il metodo di **continuare** del programma.  
  
4.  Il programma quindi viene eseguito fino a che non verrà incontrato un termine bloccato, come raggiungere un punto di interruzione, nel qual caso il DE invia un evento del punto di interruzione alla sessione di debug.  L'evento del punto di interruzione è ancora un evento bloccato e attende di DE una risposta dell'utente.  
  
5.  Se si sceglie di eseguire istruzioni in, in, o da una funzione, l'ide richiesto la sessione di debug a chiamare il metodo di `Step` del programma, passando l'unità del passaggio \(istruzione, l'istruzione, o riga\) e il tipo di passaggio\-che è, se l'esecuzione in, in, o dalla funzione.  Quando il passaggio è completo, il DE invia un evento completo del passaggio alla sessione di debug, che è un evento bloccato.  
  
     In alternativa  
  
     Se si sceglie di continuare a eseguire il puntatore all'istruzione corrente, l'ide richiesto la sessione di debug a chiamare il metodo di **di esecuzione** del programma.  Il programma verrà ripresa fino a quando incontra la condizione bloccato seguente.  
  
     In alternativa  
  
     Se la sessione di debug deve ignorare un evento bloccato particolare, la sessione di debug chiama il metodo di **continuare** del programma.  Se il programma sta eseguendo, su, o da una funzione quando ha rilevato la condizione bloccato, quindi continua il passaggio.  
  
 A livello di codice, quando il DE rileva una condizione bloccato, invia tali eventi arrestare come [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) gestione \(SDM\) di debug della sessione per implementare un'interfaccia di [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) .  Il DE passes le interfacce di [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) e di [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che rappresentano il programma e il thread che contengono il puntatore all'istruzione corrente.  Lo SDM chiama [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere lo stack frame superiore e chiama [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere il contesto del documento associato al puntatore all'istruzione corrente.  Questo contesto del documento è in genere un nome file, una riga e un numero di colonne di codice sorgente.  L'ide utilizza questi per evidenziare il codice sorgente contenente il puntatore all'istruzione corrente.  
  
 Lo SDM in genere risponde al primo evento bloccato chiamando [IDebugProgram2:: continuare](../../extensibility/debugger/reference/idebugprogram2-continue.md).  Il programma quindi viene eseguito fino a che non verrà incontrato un termine bloccato, come raggiungere un punto di interruzione, nel qual caso il DE invia [interfaccia IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a SDM.  L'evento del punto di interruzione è ancora un evento bloccato e attende di DE una risposta dell'utente.  
  
 Se si sceglie di eseguire istruzioni in, in, o da una funzione, l'ide richiesto lo SDM a chiamare [IDebugProgram2:: passaggio](../../extensibility/debugger/reference/idebugprogram2-step.md), passando [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) \(istruzione, l'istruzione, o riga\) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md), ovvero, se l'esecuzione in, in, o dalla funzione.  Quando il passaggio è completo, il DE invia un'interfaccia di [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) a SDM, che è un evento bloccato.  
  
 Se si sceglie di continuare a eseguire il puntatore all'istruzione corrente, l'ide chiede a SDM di chiamare [IDebugProgram2:: di esecuzione](../../extensibility/debugger/reference/idebugprogram2-execute.md).  Il programma verrà ripresa fino a quando incontra la condizione bloccato seguente.  
  
 Se il pacchetto di debug è di ignorare un evento bloccato particolare, il pacchetto di debug chiama lo SDM, che chiama [IDebugProgram2:: continuare](../../extensibility/debugger/reference/idebugprogram2-continue.md).  Se il programma sta eseguendo, su, o da una funzione quando ha rilevato la condizione bloccato, quindi continua il passaggio.  Ciò implica che il programma di gestire uno stato in esecuzione, in modo che sia possibile continuare.  
  
 Le chiamate che lo SDM a `Step`, **di esecuzione**e **continuare** è asincrono, ovvero lo SDM richiedere la chiamata per restituire rapidamente.  Se il DE invia lo SDM un evento bloccato sullo stesso thread prima di `Step`, di **di esecuzione**, o di restituzione di **continuare** , lo SDM il blocco.  
  
## Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)