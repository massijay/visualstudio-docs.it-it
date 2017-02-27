---
title: "IDebugProcess2::CanDetach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::CanDetach"
helpviewer_keywords: 
  - "IDebugProcess2::CanDetach"
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::CanDetach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina se l'amministratore \(SDM\) di debug della sessione può rimuovere il processo.  
  
## Sintassi  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```c#  
int CanDetach();  
```  
  
## Valore restituito  
 Se l'operazione riesce, il `S_OK.` restituisce `S_FALSE` se il debugger non può rimuovere dal processo.  In caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [CanDetach](../Topic/IDebugProgram2::CanDetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)