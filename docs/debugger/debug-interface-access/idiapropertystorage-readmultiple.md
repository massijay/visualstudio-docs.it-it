---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Reads specificato le proprietà dalla raccolta di proprietà corrente.  
  
## Sintassi  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### Parametri  
 `cpspec`  
 \[in\]  Conteggio delle proprietà specificate in `rgpspec` matrice.  se zero, il metodo non restituisce proprietà ma restituisce `S_OK` come codice di esito positivo.  
  
 `rgpspec`  
 \[in\]  Una matrice di proprietà da leggere.  Le proprietà possono essere specificate da una proprietà ID o da un nome di stringa facoltativa.  Non è necessario specificare le proprietà in un ordine specifico nella matrice.  La matrice può contenere proprietà doppie, con conseguente valori di proprietà duplicati per tornare alle proprietà semplici.  le proprietà Non semplici devono restituire accesso negato su un tentativo di aprirli una seconda volta.  La matrice può contenere una combinazione degli ID di proprietà e stringa che gli ID.  questa matrice deve avere almeno `cpspec` numero di valori di proprietà.  
  
 `rgvar`  
 \[in, out\]  una matrice di `PROPVARIANT` strutture \(nello spazio dei nomi Microsoft.VisualStudio.OLE.Interop\) da riempire di valori per ciascuna proprietà.  la matrice deve essere almeno `cpspec` elementi nella dimensione.  Il chiamante non deve inizializzare i valori nella matrice.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se uno o più delle proprietà non vengano trovati.  In caso contrario restituisce un codice di errore.  
  
## Note  
 Se una proprietà non è stata trovata, la voce corrispondente in `rgvar` la matrice contiene un oggetto  `VARIANT` con il tipo di  `VT_EMPTY`.  
  
## Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)