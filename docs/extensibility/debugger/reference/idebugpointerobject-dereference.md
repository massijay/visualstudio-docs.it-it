---
title: "IDebugPointerObject::Dereference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::Dereference"
helpviewer_keywords: 
  - "Metodo IDebugPointerObject::Dereference"
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene l'oggetto fa riferimento a.  
  
## Sintassi  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### Parametri  
 `dwIndex`  
 \[in\]  Un offset di byte semplice dall'inizio dell'oggetto a cui fa riferimento a.  
  
 `ppObject`  
 \[out\]  Restituisce [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) un oggetto che rappresenta l'oggetto fa riferimento a, più offset, se disponibile.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  restituisce E\_FAIL se questo oggetto non indica un altro oggetto.  
  
## Note  
 L'oggetto fa riferimento a può essere una primitiva o un tipo più complesso come classe o struttura.  
  
## Vedere anche  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)