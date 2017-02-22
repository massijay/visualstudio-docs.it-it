---
title: "Modalit&#224; operative | Microsoft Docs"
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
  - "motori di debug, modalità"
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Modalit&#224; operative
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esistono tre modalità in cui l'ide possa funzionare, come segue:  
  
-   [Modalità progettazione](#vsconoperationalmodesanchor1)  
  
-   [modalità di esecuzione](#vsconoperationalmodesanchor2)  
  
-   [Modalità di interruzione](#vsconoperationalmodesanchor3)  
  
 Come le transizioni personalizzate \(DE\) del motore di debug tra queste modalità è una decisione di implementazione che è necessario conoscere i meccanismi di transizione.  Il DE può implementare direttamente queste modalità.  Queste modalità sono effettivamente modalità del pacchetto di debug che passano basato sull'azione utente o sugli eventi da DE.  Ad esempio, la transizione dalla modalità di esecuzione nella modalità di interruzione è istigata da un evento bloccato da DE.  La transizione dall'interruzione alla modalità di esecuzione o alla modalità di passaggio è istigata dall'utente che esegue le operazioni quale passaggio o esegue.  per ulteriori informazioni su DE transitions, vedere [Controllo di esecuzione](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Modalità progettazione  
 La modalità progettazione è lo stato nonrunning di debug di Visual Studio, e frattempo è possibile impostare le funzionalità di debug nell'applicazione.  
  
 Solo alcune funzionalità di debug vengono utilizzate in modalità di progettazione.  Uno sviluppatore può scegliere per impostare i punti di interruzione oppure creare espressioni espressioni di controllo.  Il DE mai viene caricato o non chiamato quando l'ide è in modalità progettazione.  L'interazione con il DE ha luogo durante l'esecuzione e le modalità di interruzione.  
  
##  <a name="vsconoperationalmodesanchor2"></a> modalità di esecuzione  
 La modalità di esecuzione si verifica quando il programma viene eseguito in una sessione di debug nell'IDE.  L'applicazione verrà eseguita fino alla chiusura, fino a raggiungere un punto di interruzione, o fino a generare un'eccezione.  Quando l'applicazione viene eseguito alla chiusura, il DE transitions in modalità progettazione.  Quando viene raggiunto un punto di interruzione o viene generata un'eccezione, il DE transitions alla modalità di interruzione.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Modalità di interruzione  
 La modalità di interruzione si verifica quando l'esecuzione del programma di debug viene sospesa.  La modalità di interruzione offre allo sviluppatore uno snapshot dell'applicazione al momento dell'interruzione e consente allo sviluppatore coprire lo stato dell'applicazione e di modificare il modo in cui l'applicazione verrà eseguita.  Lo sviluppatore può visualizzare e modifica di codice, esaminare o modificare i dati, riavviare l'applicazione, terminare l'esecuzione, o continuare l'esecuzione dallo stesso punto.  
  
 La modalità di interruzione viene inserita quando il DE invia un evento bloccato sincrono.  Gli eventi arrestare sincroni, noti anche come arrestare gli eventi, notificano l'amministratore \(SDM\) di debug della sessione e l'ide che l'applicazione di cui si esegue il debug della chiusura del codice.  [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) Le interfacce e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di eventi di arresto.  
  
 Arrestando gli eventi sono ha proseguito fino da una chiamata a uno dei metodi seguenti, che transizione il debugger dalla modalità di interruzione da eseguire o dalla modalità del passaggio:  
  
-   [Esegui](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Passaggio](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continua](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Modalità del passaggio  
 La modalità del passaggio si verifica quando i passaggi di programma alla riga successiva del codice, o in, in, o una funzione.  Un passaggio viene eseguito chiamando il metodo [Passaggio](../../extensibility/debugger/reference/idebugprocess3-step.md).  Questo metodo richiede `DWORD`oggetti che specifica [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) le enumerazioni come parametri di input.  
  
 Quando il programma correttamente viene eseguita dalla riga successiva del codice o in una funzione, funzione o al cursore o a un punto di interruzione impostato, il DE passa automaticamente alla modalità di interruzione.  
  
## Vedere anche  
 [Controllo di esecuzione](../../extensibility/debugger/control-of-execution.md)