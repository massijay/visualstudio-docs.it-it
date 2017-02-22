---
title: "IDiaDataSource::loadDataForExe | Microsoft Docs"
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
  - "IDiaDataSource::loadDataForExe (metodo)"
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verrà aperto e scrive i dati di debug associati al file di .exe\/.dll.  
  
## Sintassi  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### Parametri  
 executable  
 \[in\]  Percorso del file exe o al file DLL.  
  
 searchPath  
 \[in\]  Percorso alternativo per trovare i dati di debug.  
  
 pCallback  
 \[in\]   `IUnknown` interfaccia per un oggetto che supporta un'interfaccia di callback di debug, ad esempio  [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md),  [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md),  [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)e\/o  [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfacce.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Nella seguente tabella vengono illustrati alcuni dei codici di errore possibili di questo metodo.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|E\_PDB\_NOT\_FOUND|Non riuscire aprire il file, il file o ha un formato non valido.|  
|E\_PDB\_FORMAT|Ha tentato di accedere a un file con un formato obsoleto.|  
|E\_PDB\_INVALID\_SIG|La firma non corrisponde.|  
|E\_PDB\_INVALID\_AGE|L'età non corrisponde.|  
|E\_INVALIDARG|parametro non valido.|  
|E\_UNEXPECTED|L'origine dati è già stata preparare.|  
  
## Note  
 L'intestazione di debug dei nomi file di .exe\/.dll la posizione associata di dati di debug.  
  
 Questo metodo legge l'intestazione di debug e quindi cerca e scrive i dati di debug.  Lo stato di avanzamento della ricerca può, facoltativamente, essere denominato e archiviato con i callback.  Ad esempio, [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) viene richiamato quando  `IDiaDataSource::loadDataForExe` individuare i processi di metodo una directory debug.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) e  [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) le interfacce consentono l'applicazione client forniscono metodi alternativi per la lettura dei dati del file eseguibile quando il file non è possibile accedervi direttamente con l'I\/O di file standard.  
  
 Per caricare un file con estensione pdb senza convalida, utilizzare [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodo.  
  
 Per convalidare il file pdb in base a criteri specifici, utilizzare [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metodo.  
  
 Per caricare un file con estensione pdb direttamente dalla memoria, utilizzare [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metodo.  
  
## Esempio  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)