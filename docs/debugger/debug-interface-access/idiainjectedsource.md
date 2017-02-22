---
title: "IDiaInjectedSource | Microsoft Docs"
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
  - "IDiaInjectedSource (interfaccia)"
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli accessi hanno inserito il codice sorgente archiviato nell'origine dati di diametro.  
  
## Sintassi  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaInjectedSource`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaInjectedSource::get\_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Recupera un controllo a \(CRC\) ridondanza ciclica calcolato dai byte del codice sorgente.|  
|[IDiaInjectedSource::get\_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Recupera il numero di byte del codice.|  
|[IDiaInjectedSource::get\_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|recupera il nome file per il database di origine.|  
|[IDiaInjectedSource::get\_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Recupera il nome file dell'oggetto a cui l'origine è stato compilato.|  
|[IDiaInjectedSource::get\_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Recupera il nome assegnato al codice sorgente non di file, ovvero il codice che è stato inserito.|  
|[IDiaInjectedSource::get\_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Recupera l'indicatore della compressione di origine utilizzata.|  
|[IDiaInjectedSource::get\_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Recupera i byte del codice sorgente.|  
  
## Note  
 Il database di origine inserito è testo che viene inserito durante la compilazione.  ciò non significa il preprocessore `#include` utilizzato in C\+\+.  
  
## Note per i chiamanti  
 Leggi questa interfaccia chiamando [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) o  [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) metodi.  vedere [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfaccia per un esempio di verifica  `IDiaInjectedSource` interfaccia.  
  
## Esempio  
 In questo esempio vengono visualizzati i dati disponibili da `IDiaInjectedSource` interfaccia.  Per un metodo alternativo utilizzando il [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) l'interfaccia, vedere l'esempio in  [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfaccia.  
  
```cpp#  
void PrintInjectedSource(IDiaInjectedSource* pSource)  
{  
    ULONGLONG codeLength      = 0;  
    DWORD     crc             = 0;  
    DWORD     compressionType = 0;  
    BSTR      sourceFilename  = NULL;  
    BSTR      objectFilename  = NULL;  
    BSTR      virtualFilename = NULL;  
  
    std::cout << "Injected Source:" << std::endl;  
    if (pSource != NULL)  
    {  
        if (pSource->get_crc(&crc) == S_OK &&  
            pSource->get_sourceCompression(&compressionType) == S_OK &&  
            pSource->get_length(&codeLength) == S_OK)  
        {  
            wprintf(L"  crc = %lu\n", crc);  
            wprintf(L"  code length = %I64u\n",codeLength);  
            wprintf(L"  compression type code = %lu\n", compressionType);  
        }  
  
        wprintf(L"  source filename: ");  
        if (pSource->get_filename(&sourceFilename) == S_OK)  
        {  
            wprintf(L"%s", sourceFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  object filename: ");  
        if (pSource->get_filename(&objectFilename) == S_OK)  
        {  
            wprintf(L"%s", objectFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  virtual filename: ");  
        if (pSource->get_filename(&virtualFilename) == S_OK)  
        {  
            wprintf(L"%s", virtualFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        SysFreeString(sourceFilename);  
        SysFreeString(objectFilename);  
        SysFreeString(virtualFilename);  
    }  
}  
```  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)