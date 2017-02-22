---
title: "IDebugClassField::EnumConstructors | Microsoft Docs"
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
  - "IDebugClassField::EnumConstructors"
helpviewer_keywords: 
  - "Metodo IDebugClassField::EnumConstructors"
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumeratore per i costruttori per la classe.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parametri  
 `cMatch`  
 \[in\]  Un valore [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) dell'enumerazione che specifica il tipo di costruttori di enumerazione.  
  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) un oggetto che rappresenta l'elenco dei costruttori.  Restituisce un valore null se non esistono costruttori.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK o restituisce S\_FALSE se non esistono costruttori.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Ogni elemento dell'enumerazione è [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) un oggetto che descrive un metodo del costruttore.  
  
 L'elenco dei costruttori in genere non include i costruttori predefiniti forniti da un compilatore.  
  
## Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)