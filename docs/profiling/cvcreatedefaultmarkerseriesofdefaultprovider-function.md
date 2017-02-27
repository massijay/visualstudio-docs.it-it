---
title: "Funzione CvCreateDefaultMarkerSeriesOfDefaultProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider"
helpviewer_keywords: 
  - "CvCreateDefaultMarkerSeriesOfDefaultProvider (metodo)"
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione CvCreateDefaultMarkerSeriesOfDefaultProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crea una serie predefinita del marcatore di un provider predefinito.  
  
## Sintassi  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Parametri  
 `ppProvider`  
 L'indirizzo della variabile dell'oggetto provider.  L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.  
  
 `ppMarkerSeries`  
 L'indirizzo della variabile oggetto serie del marcatore.  L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.  
  
## Valore restituito  
 S\_OK quando sia la serie del marcatore che il provider vengono creati correttamente o codice di errore nel caso ci siano errori.  Utilizzare le macro SUCCEEDED\/FAILED per verificare la condizione di errore.  
  
## Requisiti  
 **Intestazione:** cvmarkers.h  
  
## Vedere anche  
 [riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)