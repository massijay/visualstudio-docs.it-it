---
title: "IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback::ReadExecutableAtRVA (metodo)"
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legge il numero di byte che iniziano all'indirizzo virtuale relativo specificato \(RVA\) nel file eseguibile.  
  
## Sintassi  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parametri  
 `relativeVirtualAddress`  
 \[in\]  Il gli indirizzi RVA nel file eseguibile da avviare lettura.  
  
 `cbData`  
 \[in\]  Numero di byte da leggere.  
  
 `pcbData`  
 \[out\]  Restituisce il numero di byte letti.  
  
 `data[]`  
 \[in, out\]  Una matrice che viene soddisfatta di byte ha indicato dal file.  
  
## Note  
 Questo metodo viene chiamato dal codice di supporto di diametro per caricare i byte di dati da un eseguibile utilizzando un indirizzo virtuale relativo.  Questo metodo viene chiamato a supporto di [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
## Vedere anche  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)