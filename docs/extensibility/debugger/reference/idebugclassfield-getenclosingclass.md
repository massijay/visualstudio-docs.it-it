---
title: "IDebugClassField::GetEnclosingClass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetEnclosingClass"
helpviewer_keywords: 
  - "Metodo IDebugClassField::GetEnclosingClass"
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene la classe che racchiude questa classe.  
  
## Sintassi  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```c#  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### Parametri  
 `ppClassField`  
 \[out\]  restituisce [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) un oggetto che rappresenta la classe interna.  Restituisce un valore null se non c " è una classe interna.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Se la classe rappresentata da questo [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto è una classe annidata, il parametro di `ppClassField` restituisce un oggetto di `IDebugClassField` che rappresenta la classe interna.  Ad esempio, specificata la definizione della classe:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Chiamando il metodo di `GetEnclosingClass` l'oggetto di `IDebugClassField` che rappresenta la classe di `NestedClass` restituisce un oggetto di `IDebugClassField` che rappresenta la classe `RootClass`.  
  
## Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)