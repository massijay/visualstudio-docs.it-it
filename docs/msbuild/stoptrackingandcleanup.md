---
title: "StopTrackingAndCleanup | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StopTrackingAndCleanup"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StopTrackingAndCleanup"
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Interrompe tutto il rilevamento e libera qualsiasi memoria utilizzata dalla sessione di rilevamento.  
  
## Sintassi  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## Valore restituito  
 Restituisce [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con il bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) impostato se il rilevamento è stato interrotto.  
  
## Requisiti  
 **Header:** FileTracker.h  
  
## Vedere anche  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)