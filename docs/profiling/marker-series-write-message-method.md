---
title: "Metodo marker_series::write_message | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::write_message"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_message (metodo)"
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Metodo marker_series::write_message
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Scrive un messaggio nel file di traccia del Visualizzatore di concorrenza.  
  
## Sintassi  
  
```  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Parametri  
 `_Format`  
 Una Stringa di formato composta, contiene testo combinato con zero o più elementi di formato che corrispondono agli oggetti nella lista degli argomenti.  
  
 `_Importance`  
 Livello di importanza.  
  
 `_Category`  
 Livello di Category.Importance.  
  
## Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concorrenza::diagnostica  
  
## Vedere anche  
 [Classe marker\_series](../profiling/marker-series-class.md)