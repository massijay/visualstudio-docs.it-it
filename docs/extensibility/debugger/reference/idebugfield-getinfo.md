---
title: "IDebugField::GetInfo | Microsoft Docs"
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
  - "IDebugField::GetInfo"
helpviewer_keywords: 
  - "Metodo IDebugField::GetInfo"
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo recupera le informazioni visualizzabile sul campo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### Parametri  
 `dwFields`  
 \[in\]  Una combinazione [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) di costanti che seleziona le informazioni da visualizzare.  Se il campo rappresenta un simbolo, questo corrisponde in genere al nome e il tipo del simbolo.  
  
 `pFieldInfo`  
 \[out\]  Restituisce le informazioni nella struttura fornita [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) .  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)