---
title: "SetThreadCount | Microsoft Docs"
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
  - "SetThreadCount"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SetThreadCount"
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SetThreadCount
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Imposta il conteggio di thread globale e assegna tale conteggio al thread corrente.  
  
## Sintassi  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### Parametri  
 \[in\] `threadCount`  
 Numero di thread da utilizzare.  
  
## Valore restituito  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con il bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) impostato se il conteggio del thread è stato aggiornato.  
  
## Requisiti  
 **Header:** FileTracker.h