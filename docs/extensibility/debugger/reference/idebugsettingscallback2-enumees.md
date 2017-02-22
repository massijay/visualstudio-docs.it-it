---
title: "IDebugSettingsCallback2::EnumEEs | Microsoft Docs"
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
  - "IDebugSettingsCallback2::EnumEEs"
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::EnumEEs
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enumera gli analizzatori di espressioni disponibili forniti identificatori del produttore e di linguaggio.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```c#  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### Parametri  
 `celtBuffer`  
 \[in\]  Numero di elementi nel buffer di `pceltEEs` .  
  
 `rgguidLang`  
 \[in, out\]  identificatore univoco per il linguaggio di programmazione.  
  
 `rgguidVendor`  
 \[in, out\]  identificatore univoco per il fornitore.  
  
 `pceltEEs`  
 \[in, out\]  Matrice degli analizzatori di espressioni.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)