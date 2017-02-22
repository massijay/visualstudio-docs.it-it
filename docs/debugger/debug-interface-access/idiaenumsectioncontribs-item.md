---
title: "IDiaEnumSectionContribs::Item | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Item (metodo)"
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera i contributi della sezione per l'utilizzo di un indice.  
  
## Sintassi  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### Parametri  
 indice  
 \[in\]  Index [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) oggetto da recuperare.  L'indice è compreso tra 0 e `count`\-1, dove  `count` viene restituito da  [IDiaEnumSectionContribs::get\_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) metodo.  
  
 sezione  
 \[out\]  restituisce [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) oggetto che rappresenta il supporto previsto della sezione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaEnumSectionContribs::get\_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)