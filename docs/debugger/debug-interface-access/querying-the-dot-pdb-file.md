---
title: "Ricerche nel file PDB | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "PDB (file)"
  - "PDB (file), ricerca"
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ricerche nel file PDB
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un file di database di programma \(estensione pdb\) è un file binario che contiene il tipo e le informazioni di debug sui simboli raccolti nel corso della compilazione e di collegare il progetto.  Un file PDB viene creato quando si compila il programma c C\+\+ con \/C **\/ZI** o  **\/Zi** oppure  [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)],  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], o  [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] programma con  **\/debug** opzione.  I file oggetti contengono riferimenti nel file con estensione pdb per le informazioni di debug.  Per ulteriori informazioni sui file PDB, vedere [File PDB](http://msdn.microsoft.com/it-it/1761c84e-8c2c-4632-9649-b5f99964ed3f).  Un'applicazione di diametro possibile utilizzare i seguenti passaggi generali per ottenere dettagli sui vari simboli, oggetti e dati elementari all'interno di un'immagine eseguibile.  
  
### Per eseguire una query sul file pdb  
  
1.  Acquisire un'origine dati creando [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) interfaccia.  
  
    ```cpp#  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2.  chiamata [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) o  [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) per caricare le informazioni di debug.  
  
    ```cpp#  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3.  chiamata [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) per aprire  [IDiaSession](../../debugger/debug-interface-access/idiasession.md) per accedere alle informazioni di debug.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Utilizzare i metodi in `IDiaSession` per eseguire una query per i simboli nell'origine dati.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  utilizzare `IDiaEnum*` interfacce da enumerare e analizzare dai simboli o altri elementi di informazioni di debug.  
  
    ```cpp#  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)