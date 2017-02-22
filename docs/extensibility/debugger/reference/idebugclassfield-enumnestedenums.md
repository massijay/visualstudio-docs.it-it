---
title: "IDebugClassField::EnumNestedEnums | Microsoft Docs"
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
  - "IDebugClassField::EnumNestedEnums"
helpviewer_keywords: 
  - "Metodo IDebugClassField::EnumNestedEnums"
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumeratore per gli enumeratori annidati di questa classe.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parametri  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) un oggetto che rappresenta l'elenco delle enumerazioni annidate.  Restituisce un valore null se non esistono enumerazioni annidate.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK o restituisce S\_FALSE se non esistono enumeratori annidati.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Ogni elemento dell'enumerazione è [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) un oggetto che descrive un'enumerazione annidata.  
  
 All'interno di una classe dichiarata un'enumerazione è considerata un'enumerazione annidata.  Ad esempio, dato il codice:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 Il metodo di `EnumNestedEnums` restituisce [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) un oggetto contenente un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) oggetto che rappresenta l'enumerazione di `NestedEnum` .  
  
## Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)