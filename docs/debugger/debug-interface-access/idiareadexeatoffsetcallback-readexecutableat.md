---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs"
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
  - "IDiaReadExeAtOffsetCallback::ReadExecutableAt (metodo)"
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legge il numero di byte che iniziano all'offset specificato da un file eseguibile.  
  
## Sintassi  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### Parametri  
 fileOffset  
 \[in\]  L'offset nel file eseguibile alla lettura di inizio.  
  
 cbData  
 \[in\]  Numero di byte da leggere.  
  
 pcbData  
 \[out\]  Restituisce il numero di byte letti.  
  
 dati \[\]  
 \[in, out\]  Una matrice che viene soddisfatta di byte ha indicato dal file.  
  
## Note  
 Questo metodo viene chiamato dal codice di supporto di diametro per caricare i byte di dati da un eseguibile utilizzando un offset del file assoluto.  Questo metodo viene chiamato a supporto di [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
## Vedere anche  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)