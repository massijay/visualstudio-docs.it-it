---
title: "IDebugWindowsComputerPort2::GetComputerInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetComputerInfo"
  - "IDebugWindowsComputerPort2::GetComputerInfo"
ms.assetid: 654910b2-c239-44c8-92fc-317680a5672f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugWindowsComputerPort2::GetComputerInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera le informazioni relative al computer in cui il debugger in esecuzione.  
  
## Sintassi  
  
```cpp#  
HRESULT GetComputerInfo(  
   COMPUTER_INFO * pInfo  
);  
```  
  
```c#  
public int GetComputerInfo(  
   out COMPUTER_INFO[] pInfo  
);  
```  
  
#### Parametri  
 `pInfo`  
 \[out\]  Riferimento a una struttura contenente le informazioni del computer.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)   
 [COMPUTER\_INFO](../../../extensibility/debugger/reference/computer-info.md)