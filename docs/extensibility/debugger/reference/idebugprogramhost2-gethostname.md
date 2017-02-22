---
title: "IDebugProgramHost2::GetHostName | Microsoft Docs"
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
  - "IDebugProgramHost2::GetHostName"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostName"
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il titolo, il nome descrittivo, o il nome file del processo di hosting di questo programma.  
  
## Sintassi  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```c#  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### Parametri  
 `dwType`  
 \[in\]  Un valore [GETHOSTNAME\_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) dell'enumerazione.  
  
 `pbstrHostName`  
 \[out\]  Restituisce il nome richiesto del processo di hosting.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 In una tipica implementazione del metodo, il parametro di `dwType` viene ignorato e un nome descrittivo del computer host viene restituito.  Un'altra implementazione possibile consiste nel passare il parametro di `dwType` a una chiamata [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) al metodo per ottenere il nome.  
  
## Vedere anche  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)