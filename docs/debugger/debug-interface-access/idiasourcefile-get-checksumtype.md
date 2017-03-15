---
title: "IDiaSourceFile::get_checksumType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSourceFile::get_checksumType (metodo)"
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera il tipo di checksum.  
  
## Sintassi  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce il tipo di checksum.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il tipo di checksum è un valore che può essere associata a un algoritmo di checksum.  Ad esempio, il formato di file standard PDB può in genere essere uno dei seguenti valori:  
  
|tipo di checksum|etichetta di CryptoAPI|Descrizione|  
|----------------------|----------------------------|-----------------|  
|0|\<nessuno\>|Non presente in checksum.|  
|1|`CALG_MD5`|checksum generato con algoritmo hash MD5.|  
|2|`CALG_SHA1`|checksum generato con algoritmo hash SHA1.|  
  
 `CryptoAPI` le etichette hanno origine da  `ALG_ID` enumerazione.  Per ulteriori informazioni sugli algoritmi di hash, vedere `CryptoAPI` sezione di Microsoft  [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Per ottenere i byte di checksum per il file di origine, chiamare [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) metodo.  
  
## Vedere anche  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)