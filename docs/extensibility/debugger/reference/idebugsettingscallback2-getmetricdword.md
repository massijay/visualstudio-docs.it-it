---
title: "IDebugSettingsCallback2::GetMetricDword | Microsoft Docs"
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
  - "IDebugSettingsCallback2::GetMetricDword"
ms.assetid: 831a5a1a-c4af-4520-9fdf-3a731aeff85c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::GetMetricDword
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera il valore di una metrica in base al nome.  
  
## Sintassi  
  
```cpp#  
HRESULT GetMetricDword(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```c#  
private int GetMetricDword(  
   string   pszType,  
   ref Guid guidSection,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### Parametri  
 `pszType`  
 \[in\]  Tipo di metrica.  
  
 `guidSection`  
 \[in\]  Identificatore univoco della sezione.  
  
 `pszMetric`  
 \[in\]  Nome della metrica.  
  
 `pdwValue`  
 \[out\]  Restituisce il valore della metrica.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)