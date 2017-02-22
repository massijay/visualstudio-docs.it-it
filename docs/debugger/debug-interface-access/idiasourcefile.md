---
title: "IDiaSourceFile | Microsoft Docs"
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
  - "IDiaSourceFile (interfaccia)"
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

rappresenta un file di origine.  
  
## Sintassi  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaSourceFile`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaSourceFile::get\_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Recupera il valore della chiave numeri interi semplice che sono univoci per questa immagine.|  
|[IDiaSourceFile::get\_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|recupera il nome file di origine.|  
|[IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|recupera il tipo di checksum.|  
|[IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Recupera un enumeratore dei moduli con i numeri di riga che fa riferimento a questo file.|  
|[IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|recupera i byte di checksum.|  
  
## Note  
  
## Note per i chiamanti  
 Leggi questa interfaccia chiamando [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) o  [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) metodi.  Vedere l'esempio relativo ai dettagli.  
  
## Esempio  
 Questa funzione visualizzare i nomi di tutti i file di origine che contribuiscono alla tabella specificata.  
  
```cpp#  
void ShowSourceFiles(IDiaTable *pTable)  
{  
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSourceFiles ),  
                               (void**)&pSourceFiles )  
                  )  
       )  
    {  
        CComPtr<IDiaSourceFile> pSourceFile;  
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR fileName;  
            if ( pSourceFile->get_fileName( &fileName) == S_OK )  
            {  
                printf( "file name: %ws\n", fileName );  
            }  
            pSourceFile = NULL;  
        }  
    }  
}  
```  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [IDiaLineNumber::get\_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)   
 [IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)