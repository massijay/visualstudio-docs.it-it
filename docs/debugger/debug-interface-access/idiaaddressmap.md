---
title: "IDiaAddressMap | Microsoft Docs"
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
  - "IDiaAddressMap (interfaccia)"
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fornisce il controllo su come il DIA SDK calcola gli indirizzi virtuali virtuali e relativi per gli oggetti di debug.  
  
## Sintassi  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaAddressMap`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaAddressMap::get\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|indica se un mapping di indirizzo è stato stabilito per una sessione particolare.|  
|[IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Specifica se il mapping di indirizzo deve essere utilizzato per convertire gli indirizzi del simbolo.|  
|[IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica se il calcolo e l'utilizzo degli indirizzi virtuali relativi è abilitato.|  
|[IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Consente al client viene abilitata o disabilitata nel calcolo degli indirizzi virtuali relativi.|  
|[IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|recupera l'allineamento corrente di immagine.|  
|[IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Viene impostato l'allineamento di immagine.|  
|[IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Imposta le intestazioni di immagini per abilitare la conversione degli indirizzi virtuali relativi.|  
|[IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Fornisce un mapping di indirizzo le conversioni del layout dell'immagine di supporto.|  
  
## Note  
 Il controllo fornito da questa interfaccia è incapsulato in due set di dati fornito: intestazioni di immagine e mapping dell'indirizzo.  La maggior parte dei client utilizzano [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) il metodo per trovare le informazioni di debug appropriate per un'immagine e il metodo generalmente possono individuare tutti intestazioni e dati di mapping necessari stessa.  Tuttavia l'utilizzo di alcuni client specializzato l'elaborazione e la ricerca dei dati.  tali client utilizzano i metodi di `IDiaAddressMap` interfaccia per fornire il DIA SDK con i risultati della ricerca.  
  
## Note per i chiamanti  
 Questa interfaccia è disponibile dall'oggetto session di diametro.  il client chiama `QueryInterface` metodo sull'interfaccia dell'oggetto session di diametro, equivalente in genere  [IDiaSession](../../debugger/debug-interface-access/idiasession.md), per recuperare  `IDiaAddressMap` interfaccia.  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)