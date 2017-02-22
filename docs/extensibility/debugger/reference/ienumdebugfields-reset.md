---
title: "IEnumDebugFields::Reset | Microsoft Docs"
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
  - "IEnumDebugFields::Reset"
helpviewer_keywords: 
  - "Metodo IEnumDebugFields::Reset"
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo consente di reimpostare l'enumerazione al primo elemento.  
  
## Sintassi  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
#### Parametri  
 Nessuno  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Dopo che questo metodo viene chiamato, la successiva [Successivo](../../../extensibility/debugger/reference/ienumdebugfields-next.md) chiamata a restituisce il primo elemento dell'enumerazione.  
  
## Vedere anche  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [Successivo](../../../extensibility/debugger/reference/ienumdebugfields-next.md)