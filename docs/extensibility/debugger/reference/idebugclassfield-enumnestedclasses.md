---
title: "IDebugClassField::EnumNestedClasses | Microsoft Docs"
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
  - "IDebugClassField::EnumNestedClasses"
helpviewer_keywords: 
  - "Metodo IDebugClassField::EnumNestedClasses"
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crea un enumeratore per le classi annidate in questa classe.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parametri  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) un oggetto che rappresenta l'elenco delle classi annidate.  Restituisce un valore null se non sono disponibili classi annidate.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK o restituisce S\_FALSE se non sono disponibili classi annidate.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Ogni elemento dell'enumerazione è [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) un oggetto che descrive una classe annidata.  
  
 Una classe annidata è una classe definita in un'altra classe.  Di seguito è riportato un esempio:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) L'enumerazione contiene un oggetto che rappresenta la classe di `NestedClass` .  
  
## Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)