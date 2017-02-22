---
title: "IEnumDebugPropertyInfo2::Reset | Microsoft Docs"
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
  - "IEnumDebugPropertyInfo2::Reset"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2::Reset"
ms.assetid: fa4201c1-4633-4596-93aa-bd415c4ed71a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPropertyInfo2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Reimposta l'enumerazione al primo elemento.  
  
## Sintassi  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Dopo che questo metodo viene chiamato, la successiva [Successivo](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) chiamata al metodo restituisce il primo elemento dell'enumerazione.  
  
## Vedere anche  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)