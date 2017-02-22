---
title: "IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs"
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
  - "IDebugExceptionEvent2::CanPassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina se il motore di \(DE\) debug supporta la possibilità di passare questa eccezione al programma in corso il debug quando l'esecuzione riprende.  
  
## Sintassi  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```c#  
int CanPassToDebuggee();  
```  
  
## Valore restituito  
 Restituisce `S_OK` \(l'eccezione può essere passata al programma\) o `S_FALSE` \(l'eccezione non può essere passata in\).  
  
## Note  
 Il DE necessario disporre di un'azione predefinita per il passaggio all'oggetto del debug.  L'ide possa ricevere [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) l'evento e chiamare [Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md) il metodo senza chiamare il metodo di `CanPassToDebuggee` .  Di conseguenza, il DE necessario disporre di un argomento denominato per passare l'eccezione attiva o meno.  
  
## Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md)