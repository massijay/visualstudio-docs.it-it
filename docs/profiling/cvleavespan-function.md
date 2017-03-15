---
title: "Funzione CvLeaveSpan | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvLeaveSpan"
helpviewer_keywords: 
  - "CvLeaveSpan (metodo)"
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione CvLeaveSpan
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contrassegna la fine dell'intervallo.  
  
## Sintassi  
  
```  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### Parametri  
 `pSpan`  
 Oggetto Span restituito dalla chiamata precedente a CvEnterSpan\*.  Non può essere NULL.  
  
## Valore restituito  
 S\_OK quando il messaggio è scritto correttamente.  Codice di errore nel caso siano alcuni errori.  Utilizzare le macro SUCCEEDED\/FAILED per verificare la condizione di errore.  
  
## Requisiti  
 **Intestazione:** cvmarkers.h  
  
## Vedere anche  
 [riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)