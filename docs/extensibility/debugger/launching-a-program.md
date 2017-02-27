---
title: "Avviare un programma | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motori di debug, l'avvio"
  - "programmi, l'avvio"
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Avviare un programma
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli utenti che desiderano eseguire il debug di un programma possono premere F5 per eseguire il debugger IDE.  Verrà avviata una serie di eventi che a generano gli idi che connettono al modulo di debug \(DE\), che a sua volta è connesso, oppure allegato, il programma come segue:  
  
1.  Le prime chiamate dell'IDE il pacchetto di progetto per le impostazioni di debug del progetto della soluzione.  Le impostazioni includono la directory di avvio, le variabili di ambiente, la porta in cui il programma procederà e il DE da utilizzare per creare il programma, se si specifica.  Queste impostazioni vengono passate al pacchetto di debug.  
  
2.  Se un DE viene specificato, il DE chiama il sistema operativo per l'avvio del programma.  Come conseguenza di avviare il programma, l'ambiente di esecuzione del programma viene caricato.  Ad esempio, se un programma è scritto in codice MSIL, Common Language Runtime verrà richiamato per eseguire il programma.  
  
     In alternativa  
  
     Se un DE non è specificato, la porta chiama il sistema operativo per l'avvio del programma, a causa dell'ambiente di runtime del programma venga caricato.  
  
    > [!NOTE]
    >  Se un DE viene utilizzato per avviare un programma, è probabile che lo stesso DE verrà allegato al programma.  
  
3.  A seconda che il DE o la porta ha avviato il programma, il DE o dell'ambiente di runtime crea una descrizione del programma, il nodo o e indica alla porta che il programma.  
  
    > [!NOTE]
    >  Si consiglia dell'ambiente di runtime crea il nodo del programma, poiché il nodo del programma è una rappresentazione semplice di un programma che può essere eseguito il debug.  Non è necessario caricare solo su un intero DE per creare e registrare un nodo di programma.  Se il DE è progettato per essere eseguito nel corso dell'IDE di, ma nessun IDE in realtà è in esecuzione, deve essere un componente che può aggiungere un nodo di programma alla porta.  
  
 Il programma appena creato, con tutti gli altri programmi, correlati o indipendenti, avviati o allegati dallo stesso IDE, costituisce una sessione di debug.  
  
 A livello di codice, quando l'utente innanzitutto premere **F5**, il pacchetto di debug di vsprvs chiama il pacchetto di progetto \(associato al tipo di programma avviato\) con il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> , che a sua volta compila una struttura di<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> di impostazioni di debug del progetto della soluzione.  Questa struttura viene passata al pacchetto di debug con una chiamata al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> .  Il pacchetto di debug quindi creare un'istanza l'amministratore \(SDM\) di debug della sessione, che viene avviato il programma di cui viene eseguito il debug e tutti i motori di debug associati.  
  
 Uno degli argomenti passati a SDM è il GUID di DE da utilizzare per l'avvio del programma.  
  
 Se il DE GUID non è `GUID_NULL`, lo SDM viene creato il DE quindi chiama il [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metodo per l'avvio del programma.  Ad esempio, se un programma è scritto in codice nativo, verrà `IDebugEngineLaunch2::LaunchSuspended` probabilmente chiamerà `CreateProcess` e `ResumeThread` \(funzioni Win32\) per eseguire il programma.  
  
 Come conseguenza di avviare il programma, l'ambiente di esecuzione del programma viene caricato.  Il DE o l'ambiente del runtime crea [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) un'interfaccia per descrivere il programma e passa questa interfaccia [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) per notificare alla porta che il programma.  
  
 Se `GUID_NULL` viene passato, la porta vara il programma.  Il programma viene eseguito una sola volta, l'ambiente di runtime crea un'interfaccia di `IDebugProgramNode2` per descrivere il programma e passa a `IDebugPortNotify2::AddProgramNode`.  Rende la porta che il programma.  Quindi lo SDM connette il motore di debug del programma in esecuzione.  
  
## Argomenti della sezione  
 [La porta di notifica](../../extensibility/debugger/notifying-the-port.md)  
 Gli spieghi cosa si verifica dopo un programma viene avviato e la porta viene trasmessa.  
  
 [Dopo il lancio di un collegamento](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documenti quando la sessione di debug è pronta per connettere il DE il programma.  
  
## Sezioni correlate  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Vengono forniti collegamenti alle varie attività di debug, come avviare un programma e valutazione delle espressioni.