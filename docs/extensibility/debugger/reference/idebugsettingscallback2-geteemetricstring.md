---
title: "IDebugSettingsCallback2::GetEEMetricString | Microsoft Docs"
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
  - "IDebugSettingsCallback2::GetEEMetricString"
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::GetEEMetricString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera la stringa di un valore della metrica dell'analizzatore di espressioni in base al nome.  
  
## Sintassi  
  
```cpp#  
HRESULT GetEEMetricString(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetEEMetricString(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### Parametri  
 `guidLang`  
 \[in\]  Identificatore univoco del linguaggio di programmazione.  
  
 `guidVendor`  
 \[in\]  Identificatore univoco del fornitore.  
  
 `pszMetric`  
 \[in\]  Nome della metrica.  
  
 `pbstrValue`  
 \[out\]  Restituisce la stringa metriche di valore.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)