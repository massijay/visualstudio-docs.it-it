---
title: "IDebugEngine2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::Attach"
helpviewer_keywords: 
  - "IDebugEngine2::Attach"
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Associa un modulo di \(DE\) debug a un programma o ai programmi.  Chiamato dall'amministratore di debug della sessione \(SDM\) quando il DE è in corso in esecuzione a SDM.  
  
## Sintassi  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```c#  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### Parametri  
 `pProgram`  
 \[in\]  Una matrice [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) di oggetti che rappresentano i programmi da associare.  Questi sono programmi della porta.  
  
 `rgpProgramNodes`  
 \[in\]  Una matrice [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) di oggetti che rappresentano i nodi di programma, una per ogni programma.  I nodi del programma in questa matrice rappresentano gli stessi programmi di in `pProgram`.  I nodi di programma vengono forniti in modo da poter identificare il DE i programmi per connettere.  
  
 `celtPrograms`  
 \[in\]  Numero di programmi e\/o dei nodi del programma in matrici di `rgpProgramNodes` e di `pProgram` .  
  
 `pCallback`  
 \[in\]  [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Oggetto da utilizzare per inviare gli eventi di debug a SDM.  
  
 `dwReason`  
 \[in\]  Un valore [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) dell'enumerazione che specifica il motivo per connettere tali programmi.  Per ulteriori informazioni, vedere la sezione "Note".  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Esistono tre motivi per connettersi a un programma, come segue:  
  
-   `ATTACH_REASON_LAUNCH` indica che il DE si sta connettendo al programma in quanto l'utente ha avviato il processo che lo contiene.  
  
-   `ATTACH_REASON_USER` indica che l'utente in modo esplicito ha richiesto il DE per connettersi a un programma o al processo che contiene un programma\).  
  
-   `ATTACH_REASON_AUTO` indica che il DE si sta connettendo a un programma particolare quanto esegue il debug di altri programmi di un determinato processo.  Ciò viene chiamata auto\-attaccatura.  
  
 Quando questo metodo viene chiamato, il DE necessario inviare in questi eventi:  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) \(se non è già stata inviata per una determinata istanza del motore di debug\)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 Inoltre, se il motivo per connettere è `ATTACH_REASON_LAUNCH`, il DE necessario inviare [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) l'evento.  
  
 Una volta che il DE ottiene [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) l'oggetto che corrisponde al programma sottoposto a debug, è possibile eseguire query per qualsiasi interfaccia privata.  
  
 Prima di chiamare i metodi di nodo del programma della matrice fornita da `pProgram` o da `rgpProgramNodes`, la rappresentazione, se necessario, deve essere abilitata sull'interfaccia di `IDebugProgram2` che rappresenta il nodo del programma.  In genere, tuttavia, questo passaggio non è necessario.  Per ulteriori informazioni, vedere [Problemi relativi alla sicurezza](../../../extensibility/debugger/security-issues.md).  
  
## Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)