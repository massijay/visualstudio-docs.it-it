---
title: "IDebugSettingsCallback2::GetMetricGuid | Microsoft Docs"
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
  - "IDebugSettingsCallback2::GetMetricGuid"
ms.assetid: 91092763-3362-4857-adf0-231bc1254206
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::GetMetricGuid
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera l'identificatore univoco di metrica in base al nome.  
  
## Sintassi  
  
```cpp#  
HRESULT GetMetricGuid(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```c#  
private int GetMetricGuid(  
   string   pszType,  
   ref Guid guidSection,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### Parametri  
 `pszType`  
 \[in\]  Tipo di metrica.  
  
 `guidSection`  
 \[in\]  Identificatore univoco della sezione.  
  
 `pszMetric`  
 \[in\]  Nome della metrica.  
  
 `pguidValue`  
 \[out\]  Restituisce l'identificatore univoco della metrica.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)