---
title: "Enumerazione marker_importance | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_importance"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_importance (enumerazione)"
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Enumerazione marker_importance
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Rappresenta il livello di importanza del marcatore Visualizzatore di concorrenza.  
  
## Sintassi  
  
```  
enum marker_importance;  
```  
  
## Membri  
  
### Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`critical_importance`|Specifica che il marcatore è di importanza critica.|  
|`high_importance`|Specifica che il marcatore è di elevata importanza.|  
|`low_importance`|Specifica che il marcatore è di scarsa importanza.|  
|`normal_importance`|Specifica che il marcatore è di normale importanza.|  
  
## Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concorrenza::diagnostica  
  
## Vedere anche  
 [Spazio dei nomi diagnostic](../profiling/diagnostic-namespace.md)