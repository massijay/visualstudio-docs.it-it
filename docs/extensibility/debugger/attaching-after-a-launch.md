---
title: "Dopo il lancio di un collegamento | Microsoft Docs"
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
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Dopo il lancio di un collegamento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dopo che un programma è stato avviato, la sessione di debug è pronta per associare il motore \(DE\) di debug del programma autonoma.  
  
## decisioni di progettazione  
 Poiché la comunicazione risulta più semplice all'interno di uno spazio degli indirizzi condiviso, è necessario decidere se è opportuno semplificare la comunicazione tra la sessione di debug e il DE, o tra il DE e il programma.  Scegliere tra i seguenti:  
  
-   Se è opportuno semplificare la comunicazione tra la sessione di debug e il DE, la sessione di debug viene creato il DE e chiede al DE per connettere il programma.  Ciò consente alla sessione di debug e il DE in uno spazio degli indirizzi e l'ambiente di runtime e pianifica raccolta in un altro.  
  
-   Se è opportuno semplificare la comunicazione tra il DE e il programma, nell'ambiente di runtime viene creato il DE.  Ciò permette a SDM in uno spazio degli indirizzi e il DE, ambiente di runtime e pianifica raccolta in un altro.  Si tratta di una tipica di un DE distribuito con un interprete per eseguire i linguaggi basati su script.  
  
    > [!NOTE]
    >  Come si connette di DE al programma è implementazione\-dipendenti.  La comunicazione tra DE e il programma è anche implementazione\-dipendente.  
  
## Implementazione  
 A livello di codice, quando l'amministratore \(SDM\) di debug della sessione in primo luogo [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) viene rilasciato l'oggetto che rappresenta il programma venga avviata, chiama [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) il metodo, passando [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) un oggetto, che successivamente viene utilizzato per passare gli eventi di debug di nuovo a SDM.  Successivamente, il metodo `IDebugProgram2::Attach` chiama il metodo [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md).  per ulteriori informazioni su come lo SDM riceve l'interfaccia di `IDebugProgram2` , vedere [La porta di notifica](../../extensibility/debugger/notifying-the-port.md).  
  
 Se il DE necessario eseguire nello stesso spazio degli indirizzi del programma sottoposto a debug, in genere perché il DE fa parte di un interprete che esegue uno script, il metodo di `IDebugProgramNodeAttach2::OnAttach` restituisce `S_FALSE`, indicando che ha eseguito il processo di connessione.  
  
 Se, invece, il DE viene eseguito nello spazio degli indirizzi di SDM, il metodo di `IDebugProgramNodeAttach2::OnAttach` restituisce `S_OK` o [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) l'interfaccia non è implementata qualsiasi [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto associato al programma sottoposto a debug.  In questo caso, [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) il metodo viene infine viene chiamato per completare l'operazione di connessione.  
  
 Nel secondo caso, è necessario chiamare [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) il metodo sull'oggetto di `IDebugProgram2` passato al metodo di `IDebugEngine2::Attach` , archivia `GUID` nell'oggetto locale del programma e restituisce il `GUID` quando il metodo di `IDebugProgram2::GetProgramId` seguito viene chiamato il metodo su questo oggetto.  `GUID` viene utilizzato per identificare il programma in modo univoco tra i vari componenti di debug.  
  
 Si noti che nel caso del metodo di `IDebugProgramNodeAttach2::OnAttach` che restituisce `S_FALSE`, `GUID` da utilizzare per il programma viene passato al metodo ed è il metodo di `IDebugProgramNodeAttach2::OnAttach` che imposta `GUID` sull'oggetto locale del programma.  
  
 Il DE è ora associato al programma e pronto per inviare tutti gli eventi di avvio.  
  
## Vedere anche  
 [La connessione direttamente a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [La porta di notifica](../../extensibility/debugger/notifying-the-port.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)