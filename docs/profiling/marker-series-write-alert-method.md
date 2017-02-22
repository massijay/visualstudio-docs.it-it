---
title: "Metodo marker_series::write_alert | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert"
helpviewer_keywords: 
  - "Concurrency::diagnostic:marker_series::write_alert (metodo)"
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Metodo marker_series::write_alert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Scrive un avviso nel file di traccia del Visualizzatore di concorrenza.  
  
## Sintassi  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Parametri  
 `_Format`  
 Una Stringa di formato composta, contiene testo combinato con zero o più elementi di formato che corrispondono agli oggetti nella lista degli argomenti.  
  
## Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concorrenza::diagnostica  
  
## Vedere anche  
 [Classe marker\_series](../profiling/marker-series-class.md)