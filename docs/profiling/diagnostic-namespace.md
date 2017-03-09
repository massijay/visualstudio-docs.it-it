---
title: "Spazio dei nomi diagnostic | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic"
helpviewer_keywords: 
  - "Concurrency::diagnostic (spazio dei nomi)"
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Spazio dei nomi diagnostic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il `diagnostics` dello spazio dei nomi fornisce funzionalità per l'emissione dei marcatori del Visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="classes"></a>Classi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Classe marker_series](../profiling/marker-series-class.md)|Rappresenta un canale seriale degli eventi generati da un unico provider.|  
|[span (classe)](../profiling/span-class.md)|Definisce una fase dell'applicazione.|  
  
### <a name="enumerations"></a>Enumerazioni  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Enumerazione marker_importance](../profiling/marker-importance-enumeration.md)|Rappresenta il livello di importanza di un marcatore di Visualizzatore di concorrenza.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concurrency  
  
## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi Concurrency (Visualizzatore di concorrenza)](../profiling/concurrency-namespace-concurrency-visualizer.md)