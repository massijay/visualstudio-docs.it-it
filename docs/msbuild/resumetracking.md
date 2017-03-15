---
title: "ResumeTracking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ResumeTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "ResumeTracking"
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# ResumeTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Riprende il rilevamento nel contesto corrente.  
  
## Sintassi  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## Valore restituito  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con il bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) impostato se il contesto di rilevamento è stato riattivato.  [E\_FAIL](assetId:///E_FAIL?qualifyHint=False&autoUpgrade=True) viene restituito se non è possibile riprendere il rilevamento perché il contesto non è disponibile.  
  
## Requisiti  
 **Header:** FileTracker.h  
  
## Vedere anche  
 [SuspendTracking](../msbuild/suspendtracking.md)