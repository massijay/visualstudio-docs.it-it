---
title: "Funzione CvInitProvider | Microsoft Docs"
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
  - "cvmarkers/CvInitProvider"
helpviewer_keywords: 
  - "CvInitProvider (metodo)"
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funzione CvInitProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inizializza il provider del marcatore.  Deve essere chiamato prima di tutte le altre funzioni del Visualizzatore di concorrenze SDK.  
  
## Sintassi  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### Parametri  
 `pGuid`  
 GUID del provider.  Non può essere NULL.  
  
 `ppProvider`  
 Indirizzo di una variabile di output che memorizzerà il contesto del provider.  Non può essere NULL.  
  
## Valore restituito  
 S\_OK quando il provider viene inizializzato con successo o codice di errore nel caso siano degli errori.  Utilizzare le macro SUCCEEDED\/FAILED per verificare la condizione di errore.  
  
## Requisiti  
 **Intestazione:** cvmarkers.h  
  
## Vedere anche  
 [riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)