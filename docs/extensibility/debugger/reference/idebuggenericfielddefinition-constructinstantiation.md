---
title: "IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ConstructInstantiation"
  - "IDebugGenericFieldDefinition::ConstructInstantiation"
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Costruisce un'istanza del campo fornita una matrice di argomenti di tipo.  
  
## Sintassi  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```c#  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### Parametri  
 `cArgs`  
 \[in\]  Numero di argomenti nella matrice di `ppArgs` .  
  
 `ppArgs`  
 \[in\]  Allineare contenente gli argomenti di tipo.  gli argomenti di tipo devono essere tipi chiusi \(non generici o generics completamente creare un'istanza\).  
  
 `ppConstructedField`  
 \[out\]  restituisce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) l'interfaccia che rappresenta il nuovo campo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 I vincoli non sono archiviati.  
  
## Vedere anche  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)