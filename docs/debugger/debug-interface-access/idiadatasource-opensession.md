---
title: "IDiaDataSource::openSession | Microsoft Docs"
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
  - "IDiaDataSource::openSession (metodo)"
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Apre una sessione per eseguire una query sui simboli.  
  
## Sintassi  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### Parametri  
 ppSession  
 \[out\]  restituisce [IDiaSession](../../debugger/debug-interface-access/idiasession.md) oggetto che rappresenta la non pubblica.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Nella tabella seguente vengono illustrati i valori restituiti possibili di questo metodo.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|E\_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) l'oggetto non ne è già stato inizializzato con un'origine dei simboli.|  
|E\_INVALIDARG|non valido `ppSession` parametro.|  
|E\_OUTOFMEMORY|Memoria insufficiente per l'accesso.|  
  
## Note  
 Questo metodo viene aperto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) oggetto per un'origine dati.  
  
 `IDiaSession` query di utilizzo degli oggetti dell'origine dati.  Una sessione gestisce uno spazio degli indirizzi per ogni insieme di simboli di debug.  Se il file exe o dll descritto dai simboli dell'origine dati è attivo negli intervalli di indirizzi più \(ad esempio, poiché più processi lo carica\), pertanto una sessione per ogni intervallo di indirizzi deve essere utilizzata.  
  
## Esempio  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Ricerche nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)