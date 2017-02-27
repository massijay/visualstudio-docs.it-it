---
title: "IDebugPortSupplier2::CanAddPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Verifica che un fornitore di porte possibile aggiungere nuove porte.  
  
## Sintassi  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```c#  
int CanAddPort();  
```  
  
## Valore restituito  
 Se la porta è possibile aggiungere, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` per non indicare porte possono essere aggiunti al fornitore di porte.  
  
## Note  
 Chiamare questo metodo prima di chiamare [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) il metodo poiché il metodo indietro crea la porta e aggiungendolo, in grado di eseguire un'operazione che richiede molto tempo.  
  
## Vedere anche  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)