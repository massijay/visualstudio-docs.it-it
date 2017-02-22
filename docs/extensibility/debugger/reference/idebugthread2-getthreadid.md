---
title: "IDebugThread2::GetThreadId | Microsoft Docs"
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
  - "IDebugThread2::GetThreadId"
helpviewer_keywords: 
  - "IDebugThread2::GetThreadId"
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::GetThreadId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene l'identificatore di thread di sistema.  
  
## Sintassi  
  
```cpp#  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```c#  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### Parametri  
 `pdwThreadId`  
 \[out\]  Restituisce l'identificatore di thread di sistema.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Un ID del thread viene utilizzato per identificare un thread tra tutti gli altri thread in un processo.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto semplice di `CProgram` che implementa [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) l'interfaccia.  
  
```cpp#  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)