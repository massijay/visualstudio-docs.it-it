---
title: "Collegamento al programma | Microsoft Docs"
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
  - "motori di debug, connessione a programmi"
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Collegamento al programma
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dopo aver registrato programmi con la porta appropriata, è necessario connettere il debugger a un programma che si desidera eseguire il debug.  
  
## Scegliendo la connessione  
 Esistono tre modalità in cui l'amministratore \(SDM\) di debug della sessione tenta di connettersi al programma sottoposto a debug.  
  
1.  Per programmi che vengono avviati dal motore di debug dal [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metodo \(tipico dei linguaggi interpretati, ad esempio, lo SDM ottiene [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) l'interfaccia [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) dall'oggetto associato al programma collegato a.  Se lo SDM possibile ottenere l'interfaccia di `IDebugProgramNodeAttach2` , lo SDM quindi chiama [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) il metodo.  Il metodo di `IDebugProgramNodeAttach2::OnAttach` restituisce `S_OK` per indicare che non è collegato il programma e che altri tentativi possono essere eseguiti per connettere il programma.  
  
2.  Se lo SDM possibile ottenere [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) l'interfaccia dal programma collegato a, lo SDM chiama [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) il metodo.  Questo approccio consiste in genere nei programmi che sono stati avviati in modalità remota dal fornitore di porte.  
  
3.  Se il programma non può essere collegato con i metodi di `IDebugProgramEx2::Attach` o di `IDebugProgramNodeAttach2::OnAttach` , i caricamenti di SDM il motore di debug \(se non è già caricato\) chiamando la funzione di `CoCreateInstance` quindi chiama [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) il metodo.  Questo approccio consiste in genere nei programmi avviati in locale da un fornitore di porte.  
  
     È inoltre possibile che un fornitore di porte personalizzato chiama il metodo di `IDebugEngine2::Attach` nell'implementazione personalizzata del fornitore di porte del metodo di `IDebugProgramEx2::Attach` .  In genere in questo caso, il fornitore di porte personalizzato avvia il modulo di debug nel computer remoto.  
  
 Allegato si ottiene quando l'amministratore \(SDM\) di debug della sessione chiama [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) il metodo.  
  
 Se si esegue il DE nello stesso processo dell'applicazione di cui eseguire il debug, sarà necessario implementare i metodi riportati di [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)seguito:  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Dopo che il metodo di `IDebugEngine2::Attach` viene chiamato, attenersi ai passaggi riportati nell'implementazione del metodo di `IDebugEngine2::Attach` :  
  
1.  Inviare [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) un oggetto evento a SDM.  Per ulteriori informazioni, vedere [L'invio di eventi](../../extensibility/debugger/sending-events.md).  
  
2.  Chiamare [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) il metodo [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) sull'oggetto passato al metodo di `IDebugEngine2::Attach` .  
  
     Viene restituito `GUID` utilizzata per identificare il programma.  `GUID` deve essere archiviato nell'oggetto che rappresenta il programma locale a DE e deve essere restituito quando il metodo di `IDebugProgram2::GetProgramId` viene chiamato sull'interfaccia di `IDebugProgram2` .  
  
    > [!NOTE]
    >  Se si implementa l'interfaccia di `IDebugProgramNodeAttach2` , `GUID` del programma viene passato al metodo di `IDebugProgramNodeAttach2::OnAttach` .  Questo `GUID` viene utilizzato per `GUID` del programma restituito dal metodo di `IDebugProgram2::GetProgramId` .  
  
3.  Inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) un oggetto evento per notificare lo SDM che l'oggetto locale di `IDebugProgram2` è stato creato per rappresentare il programma a DE.  Per informazioni dettagliate, vedere [L'invio di eventi](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Si tratta dello stesso oggetto di `IDebugProgram2` che sia passato nel metodo di `IDebugEngine2::Attach` .  L'oggetto in precedenza positivo `IDebugProgram2` è riconosciuto dalla porta solo ed è un oggetto separato.  
  
## Vedere anche  
 [Basato su avvio allegato](../../extensibility/debugger/launch-based-attachment.md)   
 [L'invio di eventi](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)