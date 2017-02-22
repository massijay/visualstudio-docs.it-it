---
title: "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTypeFromTypeDef"
  - "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef"
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un tipo fornito il relativo token.  
  
## Sintassi  
  
```cpp#  
HRESULT GetTypeFromTypeDef(  
   ULONG32       ulAppDomainID,  
   GUID          guidModule,  
   _mdToken      tokClass,  
   IDebugField** ppType  
);  
```  
  
```c#  
int GetTypeFromTypeDef(  
   uint            ulAppDomainID,  
   Guid            guidModule,  
   int             tokClass,  
   out IDebugField ppType  
);  
```  
  
#### Parametri  
 `ulAppDomainID`  
 \[in\]  Identificatore del dominio applicazione.  
  
 `guidModule`  
 \[in\]  Identificatore univoco del modulo.  
  
 `tokClass`  
 \[in\]  token che rappresenta il tipo.  
  
 `ppType`  
 \[out\]  Restituisce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) un oggetto contenente il tipo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)