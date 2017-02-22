---
title: "Funzione CvReleaseMarkerSeries | Microsoft Docs"
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
  - "cvmarkers/CvReleaseMarkerSeries"
helpviewer_keywords: 
  - "CvReleaseMarkerSeries (metodo)"
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funzione CvReleaseMarkerSeries
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Rilascia la serie di marcatori.  Non utilizzare oggetto serie di marcatori dopo il rilascio in caso contrario l'applicazione potrebbe arrestarsi in modo anomalo.  La mancata riuscita del rilascio della stringa del marcatore causa una perdita di memoria.  
  
## Sintassi  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### Parametri  
 `pMarkerSeries`  
 L'indirizzo della variabile dell'oggetto provider.  L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.  
  
## Valore restituito  
 S\_OK quando la serie di marcatori viene rilasciata correttamente o codice di errore nel caso ci siano degli errori.  Utilizzare le macro SUCCEEDED\/FAILED per verificare la condizione di errore.  
  
## Requisiti  
 **Intestazione:** cvmarkers.h  
  
## Vedere anche  
 [riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)