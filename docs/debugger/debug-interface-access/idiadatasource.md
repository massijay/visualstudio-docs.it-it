---
title: "IDiaDataSource | Microsoft Docs"
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
  - "IDiaDataSource (interfaccia)"
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli avviati l'accesso a un database di origine di simboli di debug.  
  
## Sintassi  
  
```  
IDiaDataSource : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaDataSource`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaDataSource::get\_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera il nome file per ultimo errore di caricamento.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Verrà aperto e scrive un file di database di programma \(PDB\) come origine dati di debug.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Verrà aperto e verifica che il file di database di programma \(PDB\) corrisponda a informazioni sulla firma fornite; scrittura del file con estensione pdb come origine dati di debug.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Verrà aperto e scrive i dati di debug associati al file di .exe\/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Scrive i dati di debug archiviate in un file di database di programma \(PDB\) accede mediante un flusso di dati in memoria.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Apre una sessione per eseguire una query sui simboli.|  
  
## Note  
 Una chiamata a uno dei metodi di caricamento `IDiaDataSource` l'interfaccia apre l'origine del simbolo.  Una corrispondenza chiamata a [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) il metodo restituisce  [IDiaSession](../../debugger/debug-interface-access/idiasession.md) collegare che supporta che interroga l'origine dati.  Se il metodo di caricamento restituisce un errore file\-correlato quindi [IDiaDataSource::get\_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) il valore restituito del metodo contiene il nome file associato all'errore.  
  
## Note per i chiamanti  
 Questa interfaccia è ottenuto chiamando `CoCreateInstance` funzione con l'identificatore di classe  `CLSID_DiaSource` e l'ID dell'interfaccia di  `IID_IDiaDataSource`.  Nell'esempio viene illustrata questa interfaccia viene ottenuta.  
  
## Esempio  
  
```cpp#  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)