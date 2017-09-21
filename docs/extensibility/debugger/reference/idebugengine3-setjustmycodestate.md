---
title: "IDebugEngine3::SetJustMyCodeState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo consente al motore di debug relative alle informazioni sullo stato di JustMyCode.  
  
## Sintassi  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### Parametri  
 `fUpdate`  
 \[in\]  Diverso da zero \(`TRUE`\) per aggiornare informazioni correnti, zero \(`FALSE`\) per reimpostare le informazioni \(che ignorano qualsiasi elemento era impostato\).  
  
 `dwModules`  
 \[in\]  Numero delle strutture di informazioni in `rgJMCSpec.`  
  
 `rgJMCSpec`  
 \[in\]  Matrice [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) di strutture da utilizzare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Note  
 JustMyCode è il concetto di eseguire il debug solo il codice appartenente a un utente e ignorare tutto il codice intermedio come sistema codice\-uguale se il codice sorgente è disponibile per il codice di sistema.  
  
## Vedere anche  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)