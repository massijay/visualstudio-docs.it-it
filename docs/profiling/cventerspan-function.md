---
title: "Funzione CvEnterSpan | Microsoft Docs"
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
  - "cvmarkers/CvEnterSpanVA"
  - "cvmarkers/CvEnterSpanW"
  - "cvmarkers/CvEnterSpanExW"
  - "cvmarkers/CvEnterSpanA"
  - "cvmarkers/CvEnterSpanExVW"
  - "cvmarkers/CvEnterSpanExA"
  - "cvmarkers/CvEnterSpanVW"
helpviewer_keywords: 
  - "CvEnterSpanVW (metodo)"
  - "CvEnterSpanVA (metodo)"
  - "CvEnterSpanExA (metodo)"
  - "CvEnterSpanW (metodo)"
  - "CvEnterSpanA (metodo)"
  - "CvEnterSpanExVW (metodo)"
  - "CvEnterSpanExW (metodo)"
ms.assetid: 91689e9c-6733-44b9-b36a-8b9b2eef7d1d
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funzione CvEnterSpan
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contrassegna l'inizio del contesto di una nuova sezione.  
  
## Sintassi  
  
```  
  
HRESULT CvEnterSpanW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,  
    ...   
    );   
  
HRESULT CvEnterSpanA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    ...   
    );   
  
HRESULT CvEnterSpanVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,  
    _In_ va_list argList  
    );   
  
HRESULT CvEnterSpanVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    _In_ va_list argList  
    );   
  
HRESULT CvEnterSpanExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,   
    ...   
    );   
  
HRESULT CvEnterSpanExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    ...   
    );   
  
HRESULT CvEnterSpanExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,   
    _In_ va_list argList);   
  
HRESULT CvEnterSpanExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    _In_ va_list argList);  
  
```  
  
#### Parametri  
 `argList`  
 Elenco di argomenti.  
  
 `category`  
 Categoria dell'intervallo  
  
 `level`  
 Livello di importanza dell'intervallo.  
  
 `pMarkerSeries`  
 Contesto di una serie di marcatori validi.  Non può essere NULL.  
  
 `pMessage`  
 Stringa di formato del messaggio.  Non può essere NULL.  
  
 `ppSpan`  
 L'indirizzo di una variabile che conterrà l'oggetto risultante.  L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.  
  
## Valore restituito  
 S\_OK quando il messaggio è scritto correttamente.  Codice di errore nel caso siano alcuni errori.  Utilizzare le macro SUCCEEDED\/FAILED per verificare la condizione di errore.  
  
## Requisiti  
 **Intestazione:** cvmarkers.h  
  
 **Unicode:** CvEnterSpanW, CvEnterSpanVW, CvEnterSpanExW, CvEnterSpanExVW  
  
 **ANSI:** CvEnterSpanA, CvEnterSpanVA, CvEnterSpanExA, CvEnterSpanExVW  
  
## Vedere anche  
 [riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)