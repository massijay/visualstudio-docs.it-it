---
title: "EndTrackingContext | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "EndTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "EndTrackingContext"
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# EndTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Termina il contesto di rilevamento corrente.  
  
## Sintassi  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## Valore restituito  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con il bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) impostato se il contesto di rilevamento è terminato.  
  
## Requisiti  
 **Header:** FileTracker.h  
  
## Vedere anche  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)