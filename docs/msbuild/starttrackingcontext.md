---
title: "StartTrackingContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContext"
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# StartTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Avviare un contesto di rilevamento.  
  
## Sintassi  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### Parametri  
 \[in\] `intermediateDirectory`  
 Directory in cui archiviare il log di rilevamento.  
  
 \[in\] `taskName`  
 Identifica il contesto di rilevamento.  Questo nome viene utilizzato per creare il nome file di log.  
  
## Valore restituito  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con il bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) impostato se il contesto di rilevamento è stato creato.  
  
## Requisiti  
 **Header:** FileTracker.h