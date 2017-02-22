---
title: "IDebugEngine2::SetLocale | Microsoft Docs"
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
  - "IDebugEngine2::SetLocale"
helpviewer_keywords: 
  - "IDebugEngine2::SetLocale"
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta le impostazioni locali del motore di \(DE\) debug.  
  
## Sintassi  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### Parametri  
 `wLangID`  
 \[in\]  Specifica le impostazioni locali della lingua.  Ad esempio, 1033 per la lingua inglese.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene chiamato dall'amministratore di debug della sessione \(SDM\) per propagare le impostazioni locali dell'IDE in modo da localizzare le stringhe restituite da DE correttamente.  
  
## Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)