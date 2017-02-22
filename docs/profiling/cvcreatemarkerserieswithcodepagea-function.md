---
title: "Funzione CvCreateMarkerSeriesWithCodePageA | Microsoft Docs"
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
  - "cvmakers/CvCreateMarkerSeriesWithCodePageA"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesWithCodePageA (metodo)"
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funzione CvCreateMarkerSeriesWithCodePageA
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crea una serie di marcatori per un provider specificato e una tabella codici specificata.  Questa funzione può essere utilizzata per specificare la tabella codici in modo esplicito per il testo scritto da funzioni ANSI del marcatore API.  Impostare la tabella codici può essere utile nel caso in cui la traccia dello stack venga acquisita e quindi analizzata su computer con diversi linguaggi\/impostazioni locali.  Per impostazione predefinita viene utilizzata la tabella codici restituita dalla funzione GetACP\(\).  
  
## Sintassi  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Parametri  
 `pProvider`  
 Oggetto provider già inizializzato da CvInitProvider.  Non può essere NULL.  
  
 `pSeriesName`  
 Nome della stringa del marcatore .  Non può essere NULL ma è consentita la stringa vuota.  
  
 `nTextCodePage`  
 Tabella codici valida.  
  
 `ppMarkerSeries`  
 L'indirizzo di una variabile di output che memorizzerà il contesto della stringa del marcatore.  Non può essere NULL.  
  
## Valore restituito  
 S\_OK quando la stringa del marcatore viene creata correttamente o codice di errore nel caso vi siano alcuni errori.  Utilizzare le macro SUCCEEDED\/FAILED per verificare la condizione di errore.  
  
## Requisiti  
 **Intestazione:** cvmarkers.h  
  
## Vedere anche  
 [riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)