---
title: "IDebugPortEx2::GetPortProcessId | Microsoft Docs"
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
  - "IDebugPortEx2::GetPortProcessId"
helpviewer_keywords: 
  - "IDebugPortEx2::GetPortProcessId"
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2::GetPortProcessId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene l'ID processo di porta stesso.  
  
## Sintassi  
  
```cpp#  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```c#  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### Parametri  
 `pdwProcessId`  
 \[out\]  Restituisce l'ID processo fisico della porta stesso.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Nel runtime Win32 ad esempio, questo metodo chiama in genere la funzione Win32 `GetCurrentProcessId` per ottenere l'id processo fisica  
  
## Vedere anche  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)