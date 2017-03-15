---
title: "IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadPropertyNames"
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera i nomi delle stringhe corrispondenti per gli identificatori di proprietà specificati.  
  
## Sintassi  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### Parametri  
 `cpropid`  
 \[in\]  Numero ID della proprietà in `rgpropid`.  
  
 `rgpropid`  
 \[in\]  Matrice l'id della proprietà per il quale ottenere i nomi \(`PROPID` viene definito in WTypes.h ad esempio  `ULONG`\).  
  
 `rglpwstrName`  
 \[in, out\]  Matrice dei nomi proprietà per l'ID specificato della proprietà.  La matrice deve essere preallocata per utilizzare il numero richiesto dei nomi proprietà e deve essere in grado di utilizzare almeno `cpropid``BSTR` stringhe.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  
  
## Note  
 I nomi delle proprietà restituiti devono essere liberati \(chiamando `SysFreeString` funzione\) quando non sono più necessari.  
  
## Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)