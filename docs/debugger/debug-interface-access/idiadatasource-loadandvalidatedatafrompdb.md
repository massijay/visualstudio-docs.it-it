---
title: "IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs"
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
  - "IDiaDataSource::loadAndValidateDataFromPdb (metodo)"
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Apertura e verifica che il file di database di programma \(PDB\) corrisponda a informazioni sulla firma fornite e scrive il file pdb come origine dati di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### Parametri  
 `pdbPath`  
 \[in\]  Il percorso del file pdb.  
  
 `pcsig70`  
 \[in\]  La firma di GUID per verificare con la firma del file con estensione pdb.  Solo file con estensione pdb in [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e successivamente avere firme di GUID.  
  
 `sig`  
 \[in\]  La firma a 32 bit che verifica della firma del file con estensione pdb.  
  
 `age`  
 \[in\]  Valore dell'età da verificare.  L'età necessariamente non corrisponde ad alcun valore, viene utilizzata per determinare se un file con estensione pdb viene sincronizzata con un file EXE corrispondente.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Nella tabella seguente vengono illustrati i valori restituiti possibili di questo metodo.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|E\_PDB\_NOT\_FOUND|Non riuscire aprire il file, il file o ha un formato non valido.|  
|E\_PDB\_FORMAT|Ha tentato di accedere a un file con un formato obsoleto.|  
|E\_PDB\_INVALID\_SIG|La firma non corrisponde.|  
|E\_PDB\_INVALID\_AGE|L'età non corrisponde.|  
|E\_INVALIDARG|parametro non valido.|  
|E\_UNEXPECTED|L'origine dati è già stata preparare.|  
  
## Note  
 Un file PDB contiene sia la firma che i valori dell'età.  Questi valori esse vengono replicate nel file con estensione exe o dll corrispondente al file con estensione pdb.  Prima della preparazione dell'origine dati, questo metodo verifica che la firma denominata e l'intervallo di file pdb corrispondano ai valori forniti.  
  
 Per caricare un file con estensione pdb senza convalida, utilizzare [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodo.  
  
 Per accedere al processo di caricamento dati \(tramite un meccanismo di callback, utilizzare [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
 Per caricare un file con estensione pdb direttamente dalla memoria, utilizzare [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metodo.  
  
## Esempio  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)