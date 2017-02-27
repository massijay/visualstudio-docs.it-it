---
title: "IDebugObject2::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetICorDebugValue"
helpviewer_keywords: 
  - "Metodo IDebugObject2::GetICorDebugValue"
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugObject2::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene un oggetto di codice gestito che rappresenta il valore associato all'oggetto.  
  
## Sintassi  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### Parametri  
 `ppUnk`  
 \[out\]  interfaccia di `IUnknown` che rappresenta tale alias.  Questa interfaccia è possibile eseguire una query per l'interfaccia di `ICorDebugValue` .  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 l'oggetto di `ICorDebugValue` è un'interfaccia di Common Language Runtime che rappresenta un valore.  
  
## Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)