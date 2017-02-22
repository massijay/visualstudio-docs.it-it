---
title: "IDebugSettingsCallback2::GetEEMetricGuid | Microsoft Docs"
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
  - "IDebugSettingsCallback2::GetEEMetricGuid"
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::GetEEMetricGuid
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera l'identificatore univoco per metrica dell'analizzatore di espressioni in base al nome.  
  
## Sintassi  
  
```cpp#  
HRESULT GetEEMetricGuid(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```c#  
HRESULT GetEEMetricGuid(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### Parametri  
 `guidLang`  
 \[in\]  Identificatore univoco del linguaggio di programmazione.  
  
 `guidVendor`  
 \[in\]  Identificatore univoco del fornitore.  
  
 `pszMetric`  
 \[in\]  Nome della metrica.  
  
 `pguidValue`  
 \[out\]  Restituisce l'identificatore univoco della metrica.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)