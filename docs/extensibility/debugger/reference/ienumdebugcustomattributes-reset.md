---
title: "IEnumDebugCustomAttributes::Reset | Microsoft Docs"
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
  - "IEnumCustomAttributes::Reset"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::Reset"
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Riporta all'inizio la sequenza di enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Dopo che questo metodo viene chiamato, la successiva [Successivo](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) chiamata al metodo restituisce il primo elemento dell'enumerazione.  
  
## Vedere anche  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Successivo](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)