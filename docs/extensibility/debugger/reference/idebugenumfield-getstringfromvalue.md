---
title: "IDebugEnumField::GetStringFromValue | Microsoft Docs"
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
  - "IDebugEnumField::GetStringFromValue"
helpviewer_keywords: 
  - "Metodo IDebugEnumField::GetStringFromValue"
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo ottiene il nome della costante di enumerazione assegnato il valore.  
  
## Sintassi  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```c#  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### Parametri  
 `value`  
 \[in\]  Il valore per il quale ottenere il nome della costante di enumerazione.  
  
 `pbstrValue`  
 \[out\]  Restituisce il nome della costante di enumerazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` se il valore non ha un nome associato, o restituisce un codice di errore.  
  
## Note  
 Se c " è più un nome associato allo stesso valore, il nome definito nell'enumerazione viene restituito.  
  
## Vedere anche  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)