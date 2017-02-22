---
title: "Funzione CvCreateMarkerSeries | Microsoft Docs"
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
  - "cvmarkers/CvCreateMarkerSeriesA"
  - "cvmarkers/CvCreateMarkerSeriesW"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesA (metodo)"
  - "CvCreateMarkerSeriesW (metodo)"
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funzione CvCreateMarkerSeries
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crea una serie di marcatori per un dato provider.  
  
## Sintassi  
  
```  
_Check_return_ HRESULT CvCreateMarkerSeriesW(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCWSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
  
_Check_return_ HRESULT CvCreateMarkerSeriesA(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
```  
  
#### Parametri  
 `pProvider`  
 Oggetto provider già inizializzato da CvInitProvider.  Non può essere NULL.  
  
 `pSeriesName`  
 Nome della stringa del marcatore .  Non può essere NULL ma è consentita la stringa vuota.  
  
 `ppMarkerSeries`  
 L'indirizzo di una variabile di output che memorizzerà il contesto della stringa del marcatore.  Non può essere NULL.  
  
## Valore restituito  
 S\_OK quando la stringa del marcatore viene creata correttamente o codice di errore nel caso vi siano alcuni errori.  Utilizzare le macro SUCCEEDED\/FAILED per verificare la condizione di errore.  
  
## Requisiti  
 **Intestazione:** cvmarkers.h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## Vedere anche  
 [riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)