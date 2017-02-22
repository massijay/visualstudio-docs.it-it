---
title: "Funzione CvIsEnabled | Microsoft Docs"
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
  - "cvmarkers/CvIsEnabledEx"
  - "cvmarkers/CvIsEnabled"
helpviewer_keywords: 
  - "CvIsEnabled (metodo)"
  - "CvIsEnabledEx (metodo)"
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funzione CvIsEnabled
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina se una sessione ha attivato lo specifico provider ETW.  
  
## Sintassi  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### Parametri  
 `category`  
 Categoria.  
  
 `level`  
 Livello di importanza.  
  
 `pProvider`  
 Oggetto provider valido.  Non può essere NULL.  
  
## Valore restituito  
 S\_OK se il provider è attualmente abilitato.  S\_FALSE se il provider è attualmente disabilitato.  Codice di errore nel caso siano alcuni errori.  Utilizzare la macro FAILED per controllare la condizione di errore e quindi per controllare S\_OK\/S\_FALSE.  
  
## Requisiti  
 **Intestazione:** cvmarkers.h  
  
## Vedere anche  
 [riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)