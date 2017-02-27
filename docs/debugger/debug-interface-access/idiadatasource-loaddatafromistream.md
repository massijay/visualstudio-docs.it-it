---
title: "IDiaDataSource::loadDataFromIStream | Microsoft Docs"
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
  - "IDiaDataSource::loadDataFromIStream (metodo)"
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Scrive i dati di debug archiviate in un file di database di programma \(PDB\) accede mediante un flusso di dati in memoria.  
  
## Sintassi  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### Parametri  
 pIStream  
 \[in\]   <xref:IStream> oggetto che rappresenta il flusso di dati da utilizzare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Nella tabella seguente vengono illustrati i valori restituiti possibili di questo metodo.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|E\_PDB\_FORMAT|Ha tentato di accedere a un file con un formato obsoleto.|  
|E\_INVALIDARG|Invalidparameter.|  
|E\_UNEXPECTED|L'origine dati è già stata preparare.|  
  
## Note  
 Questo metodo consente l'utilizzo dei dati di debug per un eseguibile sia ottenuto dalla memoria con <xref:IStream> oggetto.  
  
 Per caricare un file con estensione pdb senza convalida, utilizzare [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodo.  
  
 Per convalidare il file pdb in base a criteri specifici, utilizzare [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metodo.  
  
 Per accedere al processo di caricamento dati \(tramite un meccanismo di callback, utilizzare [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
## Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)