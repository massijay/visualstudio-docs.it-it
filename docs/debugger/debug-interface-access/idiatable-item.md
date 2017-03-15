---
title: "IDiaTable::Item | Microsoft Docs"
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
  - "IDiaTable::Item (metodo)"
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaTable::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un riferimento alla voce specificata nella tabella.  
  
## Sintassi  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### Parametri  
 `index`  
 \[in\]  L'indice della voce della tabella nell'intervallo 0 e `count`\-1, dove  `count` viene restituito da  [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)metodo.  
  
 `element`  
 \[out\]  restituisce `IUnknown` oggetto che rappresenta la voce specificata per la tabella.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Una tabella rappresenta una raccolta di oggetti.  Come gli oggetti, il parametro dell'elemento possibile eseguire il cast dell'interfaccia appropriata.  Ad esempio, se una tabella contiene [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) gli oggetti, il parametro dell'elemento è possibile eseguire il cast a  `IDiaSegment` interfaccia.  
  
 È un metodo più comune da chiamare `QueryInterface` metodo in  [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interfaccia per l'interfaccia appropriata dell'enumeratore e utilizzare i metodi specifici dell'enumeratore per accedere al contenuto.  vedere [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfaccia per un esempio.  
  
## Vedere anche  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)