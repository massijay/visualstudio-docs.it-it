---
title: "StartTrackingContextWithRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContextWithRoot"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContextWithRoot"
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Avvia un contesto di rilevamento utilizzando un file di risposta che specifica un marcatore radice.  
  
## Sintassi  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### Parametri  
 \[in\] `intermediateDirectory`  
 Directory in cui archiviare il log di rilevamento.  
  
 \[in\] `taskName`  
 Identifica il contesto di rilevamento.  Questo nome viene utilizzato per creare il nome file di log.  
  
 \[in\] `rootMarkerResponseFile`  
 Il nome percorso di un file di risposta che contiene un marcatore radice.  Il nome radice è utilizzato per raggruppare il rilevamento per un contesto tutto insieme.  
  
## Valore restituito  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con il bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) impostato se il contesto di rilevamento è stato creato.  
  
## Requisiti  
 **Header:** FileTracker.h  
  
## Vedere anche  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)