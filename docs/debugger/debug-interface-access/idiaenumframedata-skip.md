---
title: "IDiaEnumFrameData::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumFrameData::Skip (metodo)"
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumFrameData::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ignora un numero specificato di elementi dati del frame in una sequenza di enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Parametri  
 celta  
 \[in\]  Il numero di elementi dati del frame nella sequenza di enumerazione da ignorare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` se non sono presenti più record da ignorare.  
  
## Vedere anche  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)