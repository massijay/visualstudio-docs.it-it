---
title: "Costruttore marker_series::marker_series | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series (costruttore)"
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Costruttore marker_series::marker_series
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inizializza una nuova istanza della classe `marker_series`.  
  
## Sintassi  
  
```  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### Parametri  
 `_SeriesName`  
 Nome delle serie da creare.  
  
 `_ProviderGuid`  
 Il GUID del provider di serie.  
  
## Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concorrenza::diagnostica  
  
## Vedere anche  
 [Classe marker\_series](../profiling/marker-series-class.md)