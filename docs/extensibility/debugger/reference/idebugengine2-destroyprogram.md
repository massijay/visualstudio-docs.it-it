---
title: "IDebugEngine2::DestroyProgram | Microsoft Docs"
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
  - "IDebugEngine2::DestroyProgram"
helpviewer_keywords: 
  - "IDebugEngine2::DestroyProgram"
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Notifica al modulo \(DE\) di debug che il programma specificato in modo che atipica è stato interrotto e che il DE necessario eliminare tutti i riferimenti al programma e inviare un programma eliminato l'evento.  
  
## Sintassi  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### Parametri  
 `pProgram`  
 \[in\]  [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Un oggetto che rappresenta il programma a meno che atipica è stato terminato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Dopo che questo metodo viene chiamato, il DE successivamente inviato [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) un evento di nuovo all'amministratore di debug della sessione \(SDM\).  
  
 Questo metodo non è implementato \(restituisce `E_NOTIMPL`\) se il DE viene eseguito nello stesso processo del programma sottoposto a debug.  Questo metodo viene implementato solo se il DE viene eseguito nello stesso processo di SDM.  
  
## Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)