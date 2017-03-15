---
title: "Metodo marker_series::is_enabled | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::is_enabled (metodo)"
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo marker_series::is_enabled
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina se una sessione abilita il provider.  
  
## Sintassi  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### Parametri  
 `_Importance`  
 Livello di importanza.  
  
 `_Category`  
 Categoria  
  
## Valore restituito  
  
## Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concorrenza::diagnostica  
  
## Vedere anche  
 [Classe marker\_series](../profiling/marker-series-class.md)