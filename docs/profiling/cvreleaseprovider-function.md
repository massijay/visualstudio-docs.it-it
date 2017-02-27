---
title: "Funzione CvReleaseProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseProvider"
helpviewer_keywords: 
  - "CvReleaseProvider (metodo)"
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione CvReleaseProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Rilascia il provider del marcatore.  Il rilascio del provider del marcatore non influirà, sulla serie precedentemente creata, del marcatore di questo provider.  Le serie del marcatore devono essere rilasciate separatamente dalla chiamata del CvReleaseMarkerSeries.  L'errore nel rilascio del provider causa una perdita di memoria.  
  
## Sintassi  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### Parametri  
 `pProvider`  
 Contesto del provider.  Non può essere NULL.  
  
## Valore restituito  
 S\_OK quando il provider rilascia correttamente oppure un codice di errore nel caso si siano verificati degli errori.  Utilizzare le macro SUCCEEDED\/FAILED per verificare la condizione di errore.  
  
## Requisiti  
 **Intestazione:** cvmarkers.h  
  
## Vedere anche  
 [riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)