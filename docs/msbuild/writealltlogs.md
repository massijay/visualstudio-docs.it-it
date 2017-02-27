---
title: "WriteAllTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteAllTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteAllTLogs"
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteAllTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Scrive i log di rilevamento per tutti i thread e i contesti.  
  
## Sintassi  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### Parametri  
 \[in\] `intermediateDirectory`  
 Directory in cui archiviare il log di rilevamento.  
  
 \[in\] `tlogRootName`  
 Nome radice del nome file di log.  
  
## Valore restituito  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con il bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) impostato se il contesto di rilevamento è stato creato.  
  
## Requisiti  
 **Header:** FileTracker.h  
  
## Vedere anche  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)