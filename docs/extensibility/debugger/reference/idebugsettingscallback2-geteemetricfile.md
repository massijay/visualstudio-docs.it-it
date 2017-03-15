---
title: "IDebugSettingsCallback2::GetEEMetricFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricFile"
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetEEMetricFile
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera il file metrica dell'analizzatore di espressioni fornito il nome o la metrica.  
  
## Sintassi  
  
```cpp#  
HRESULT GetEEMetricFile(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetEEMetricFile(  
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
 \[out\]  Restituisce il contenuto del file metrica come stringa.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)