---
title: "Classe marker_series | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series (classe)"
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Classe marker_series
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Rappresenta un canale seriale di eventi generati da un singolo provider.  
  
## Sintassi  
  
```  
class marker_series;  
```  
  
## Membri  
  
### Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Costruttore marker\_series::marker\_series](../profiling/marker-series-marker-series-constructor.md)|Inizializza una nuova istanza della classe `marker_series`.|  
|[Distruttore marker\_series::~marker\_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Eliminare l'oggetto marker\_series e rilasciare tutte le risorse allocate.|  
  
### Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo marker\_series::is\_enabled](../profiling/marker-series-is-enabled-method.md)|Determina se una sessione ha abilitato il provider.|  
|[Metodo marker\_series::write\_alert](../profiling/marker-series-write-alert-method.md)|Scrive un avviso nel file di traccia del Visualizzatore di concorrenza.|  
|[Metodo marker\_series::write\_flag](../profiling/marker-series-write-flag-method.md)|Scrive un flag nel file di traccia del Visualizzatore di concorrenza.|  
|[Metodo marker\_series::write\_message](../profiling/marker-series-write-message-method.md)|Scrive un messaggio nel file di traccia del Visualizzatore di concorrenza.|  
  
## Gerarchia di ereditarietà  
 `marker_series`  
  
## Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concorrenza::diagnostica  
  
## Vedere anche  
 [Spazio dei nomi diagnostic](../profiling/diagnostic-namespace.md)