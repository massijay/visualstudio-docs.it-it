---
title: "DiaAddressMapEntry | Microsoft Docs"
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
  - "DiaAddressMapEntry (enumerazione)"
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Viene descritta una voce in una mappa di indirizzo.  
  
## Sintassi  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## Elementi  
 `rva`  
 Un indirizzo virtuale dell'\(RVA\) immagine A.  
  
 `rvaTo`  
 Indirizzo virtuale relativo `rva` viene eseguito il mapping nell'immagine B.  
  
## Note  
 Un mapping di indirizzo fornisce una conversione da un layout dell'immagine \(\) a un altro \(B\).  una matrice di `DiaAddressMapEntry` strutture ordinate da  `rva` definisce un mapping address.  
  
 Per convertire un indirizzo, `addrA`, nell'immagine A un indirizzo,  `addrB`nell'immagine, B, effettuare i passaggi seguenti:  
  
1.  Trovare il mapping della voce, `e`, al massimo  `rva` minore o uguale a  `addrA`.  
  
2.  set `delta = addrA – e.rva`.  
  
3.  set `addrB = e.rvaTo + delta`.  
  
 una matrice di `DiaAddressMapEntry` le strutture viene passata a  [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metodo.  
  
## Requisiti  
 intestazione: dia2.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)