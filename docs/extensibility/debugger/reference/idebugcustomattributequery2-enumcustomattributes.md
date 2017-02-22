---
title: "IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft Docs"
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
  - "IDebugCustomAttributeQuery2::EnumCustomAttributes"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery2::EnumCustomAttributes"
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttributeQuery2::EnumCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene un enumeratore per tutti gli attributi personalizzati associati a questo campo.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumCustomAttributes(   
   IEnumDebugCustomAttributes** ppEnum  
);  
```  
  
```c#  
int EnumCustomAttributes(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### Parametri  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) un oggetto che rappresenta l'elenco degli attributi personalizzati, in caso contrario, restituisce un valore null se non esistono attributi personalizzati.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK o S\_FALSE se non esistono attributi personalizzati in questo campo.  In caso contrario, restituisce un codice di errore;  
  
## Note  
 un campo può avere attributi personalizzati più.  
  
## Vedere anche  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)