---
title: "IDiaAddressMap::put_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::put_imageAlign (metodo)"
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Viene impostato l'allineamento di immagine.  
  
## Sintassi  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### Parametri  
 NewVal  
 \[in\]  Il nuovo valore di allineamento di immagini per l'eseguibile.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Immagini \(eseguibili caricati\) sono allineati ai limiti specificati di memoria.  Questo allineamento può essere influenzato dall'architettura di sistema corrente e da compilare e le opzioni in fase di collegamento.  L'allineamento delle immagini è sempre sui limiti di byte.  I seguenti valori di allineamento di immagine validi: 1, 2, 4, 8, 16, 32 e 64 limiti di byte.  
  
 L'allineamento corrente immagine può essere recuperato tramite una chiamata a [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) metodo.  
  
> [!NOTE]
>  L'immagine è già stata caricata prima che questo metodo può essere chiamato.  `put_imageAlign` il metodo viene utilizzato in genere quando l'immagine è stata spostata o modificato stata e un nuovo allineamento è obbligatorio.  
  
## Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)