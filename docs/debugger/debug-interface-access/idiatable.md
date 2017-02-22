---
title: "IDiaTable | Microsoft Docs"
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
  - "IDiaTable (interfaccia)"
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaTable
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enumera una tabella di origine dati di diametro.  
  
## Sintassi  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaTable`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaTable::get\_\_NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|recupera [interfaccia di IEnumVARIANT](http://msdn.microsoft.com/it-it/139e3c93-faef-4003-9079-e0e94494db3e) versione di questo enumeratore.|  
|[IDiaTable::get\_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Recupera il nome della tabella.|  
|[IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera il numero di elementi della tabella.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Recupera un riferimento a un particolare indice della voce.|  
  
## Note  
 questa interfaccia implementa `IEnumUnknown` metodi di enumerazione nello spazio dei nomi Microsoft.VisualStudio.OLE.Interop.  `IEnumUnknown` l'interfaccia di enumerazione è molto più efficiente per la ripetizione sul contenuto della tabella che  [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md) e  [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md) metodi.  
  
 L'interpretazione di `IUnknown` interfaccia restituito dall'una o l'altra  `IDiaTable::Item` metodo o  `Next` il metodo \(nello spazio dei nomi Microsoft.VisualStudio.OLE.Interop\) dipende dal tipo di tabella.  Ad esempio, se `IDiaTable` l'interfaccia rappresenta un elenco di database di origine inseriti,  `IUnknown` l'interfaccia deve essere eseguire una query per  [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) interfaccia.  
  
## Note per i chiamanti  
 Leggi questa interfaccia chiamando [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) o  [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md) metodi.  
  
 Le seguenti interfacce implementate con `IDiaTable` interfaccia \(ovvero è possibile eseguire una query  `IDiaTable` interfaccia per una delle interfacce\):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## Esempio  
 la prima funzione, `ShowTableNames`, visualizza i nomi di tutte le tabelle nella sessione.  la seconda funzione, `GetTable`, esamina tutte le tabelle per una tabella che implementa un'interfaccia specificata.  la terza funzione, `UseTable`, viene illustrato come utilizzare  `GetTable` funzione.  
  
> [!NOTE]
>  `CDiaBSTR` è una classe che esegue il wrapping di un oggetto  `BSTR` e posizionano gli handle che liberano la stringa durante la creazione di istanze esce dall'ambito.  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)