---
title: "IDebugSettingsCallback2::GetEELocalObject | Microsoft Docs"
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
  - "IDebugSettingsCallback2::GetEELocalObject"
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::GetEELocalObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un oggetto locale dell'analizzatore di espressioni fornito il nome ".  
  
## Sintassi  
  
```cpp#  
HRESULT GetEELocalObject(  
   REFGUID     guidLang,  
   REFGUID     guidVendor,  
   LPCWSTR     pszMetric,  
   IUnknown ** ppUnk  
);  
```  
  
```c#  
private int GetEELocalObject(  
   ref Guid          guidLang,  
   ref Guid          guidVendor,  
   string            pszMetric,  
   out System.Object ppUnk  
);  
```  
  
#### Parametri  
 `guidLang`  
 \[in\]  Identificatore univoco del linguaggio di programmazione.  
  
 `guidVendor`  
 \[in\]  Identificatore univoco del fornitore.  
  
 `pszMetric`  
 \[in\]  Nome della metrica.  
  
 `ppUnk`  
 \[out\]  Restituisce l'oggetto locale dell'analizzatore di espressioni.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)