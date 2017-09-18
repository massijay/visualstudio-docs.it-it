---
title: "IDebugObject2::IsEncOutdated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsEncOutdated"
helpviewer_keywords: 
  - "Metodo IDebugObject2::IsEncOutdated"
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo determina se lo stato di Modifica e continuazione dell'oggetto o del contenitore padre non aggiornato.  un analizzatore di espressioni personalizzato non implementa questo metodo e sempre non restituisce `E_NOTIMPL`.  
  
## Sintassi  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```c#  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### Parametri  
 `pfEncOutdated`  
 \[out\]  Diverso da zero \(`TRUE`\) se lo stato di Modifica e continuazione non è aggiornato, zero \(`FALSE`\) se non è.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
> [!NOTE]
>  Un analizzatore di espressioni personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)