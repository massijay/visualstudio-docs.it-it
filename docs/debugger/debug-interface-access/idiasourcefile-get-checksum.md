---
title: "IDiaSourceFile::get_checksum | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksum (metodo)"
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera i byte di checksum.  
  
## Sintassi  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parametri  
 `cbData`  
 \[in\]  Dimensione del buffer di dati, in byte.  
  
 `pcbData`  
 \[out\]  Restituisce il numero di byte di checksum.  Questo parametro non può essere `NULL`.  
  
 `data`  
 \[in, out\]  Un buffer che viene riempito con un byte di checksum.  se questo parametro è `NULL`, quindi  `pcbData` restituisce il numero di byte necessari.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Per determinare il tipo di algoritmo di checksum utilizzato per generare i byte di checksum, chiamare [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) metodo.  
  
 Il checksum in genere viene generato dall'immagine del file di origine in modo che le modifiche apportate nel file di origine riflesse nelle modifiche in byte di checksum.  Se i byte di checksum non corrispondono a un checksum generato dall'immagine caricamento del file, il file deve essere considerato danneggiato o alterato.  
  
 I checksum tipici non vengono mai più di 32 byte nella dimensione ma non si presuppone che corrisponde alla dimensione massima di un checksum.  impostare `data` parametro di  `NULL` per ottenere il numero di byte obbligatorio per recuperare il checksum.  Quindi allocare un buffer di dimensioni corrette e chiamare questo metodo nuovamente con il nuovo buffer.  
  
## Vedere anche  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)