---
title: "IDebugProgramNode2::Attach_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::Attach"
helpviewer_keywords: 
  - "IDebugProgramNode2::Attach_V7"
  - "IDebugProgramNode2::Attach"
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

DEPRECATO.  NOT UTILIZZARE.  
  
## Sintassi  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```c#  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### Parametri  
 `pMDMProgram`  
 \[in\]  [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) L'interfaccia che rappresenta il programma per allegare.  
  
 `pCallback`  
 \[in\]  [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) L'interfaccia da utilizzare per inviare gli eventi di debug a SDM.  
  
 `dwReason`  
 \[in\]  Un valore [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) dell'enumerazione che specifica il motivo per allegare.  
  
## Valore restituito  
 L'implementazione di deve restituire sempre `E_NOTIMPL`.  
  
## Note  
  
> [!WARNING]
>  A partire da [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], questo metodo viene più utilizzato e non deve sempre restituire `E_NOTIMPL`.  Vedere [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) l'interfaccia per un'alternativa se il nodo del programma deve indicare che non può essere collegato a o se il nodo del programma sta impostando semplicemente il programma `GUID`. In caso contrario, implementare [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) il metodo.  
  
## prima di Visual Studio 2005  
 Questo metodo deve essere implementato solo se il DE viene eseguito nello spazio degli indirizzi del programma sottoposto a debug.  In caso contrario, questo metodo deve restituire `S_FALSE`.  
  
 Quando questo metodo viene chiamato, il DE necessario inviare [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) l'oggetto evento, se non è stato inviato per questa istanza [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) dell'interfaccia come pure [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) gli oggetti evento.  [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) L'oggetto evento viene quindi inviato se il parametro di `dwReason` è `ATTACH_REASON_LAUNCH`.  
  
 Il DE necessario chiamare [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) il metodo [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) sull'oggetto fornito [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) dall'oggetto evento e deve archiviare che il GUID del programma nei dati di istanza per l'oggetto di `IDebugProgram2` implementato da DE.  
  
## Vedere anche  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)