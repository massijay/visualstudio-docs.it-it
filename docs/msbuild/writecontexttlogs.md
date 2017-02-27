---
title: "WriteContextTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteContextTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteContextTLogs"
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteContextTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Scrive file dei log per il contesto corrente.  
  
## Sintassi  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
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
 [WriteAllTLogs](../msbuild/writealltlogs.md)