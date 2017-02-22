---
title: "IDebugProgramNodeAttach2::OnAttach | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Si connette al programma associato o ripianificare il processo di connessione [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) al metodo.  
  
## Sintassi  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```c#  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### Parametri  
 `guidProgramId`  
 \[in\]  `GUID` da assegnare al programma associato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) viene chiamato il metodo.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene chiamato durante il processo di connessione, prima che [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) venga chiamato il metodo.  Il metodo di `OnAttach` possibile eseguire il processo stesso della connessione \(in questo caso, questo metodo restituisce `S_FALSE`\) o rinviare il processo di connessione al metodo di `IDebugEngine2::Attach` \(il metodo di `OnAttach` restituisce `S_OK`\).  In qualsiasi evento, il metodo di `OnAttach` possibile impostare `GUID` del programma sottoposto a debug a `GUID`specificato.  
  
## Vedere anche  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)