---
title: "IDebugReference2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::Compare"
helpviewer_keywords: 
  - "IDebugReference2::Compare"
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Confronta un riferimento a un altro.  Riservato per un utilizzo futuro.  
  
## Sintassi  
  
```cpp#  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```c#  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### Parametri  
 `dwCompare`  
 \[in\]  Un valore [REFERENCE\_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) dell'enumerazione che specifica l'operazione di confronto, ad esempio, uguale, minore di, o maggiore di.  
  
 `pReference`  
 \[in\]  [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Un oggetto che rappresenta il riferimento da confrontare su.  
  
## Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE\_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)