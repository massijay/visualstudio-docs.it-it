---
title: "IDiaSession | Microsoft Docs"
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
  - "IDiaSession (interfaccia)"
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fornisce un contesto di query per i simboli di debug.  
  
## Sintassi  
  
```  
IDiaSession : IUnknown  
```  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi `IDiaSession`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaSession::get\_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Viene recuperato l'indirizzo di caricamento del file eseguibile che corrisponde ai simboli nell'archivio simboli.  Si tratta dello stesso valore passato al metodo `put_loadAddress`.|  
|[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Imposta l'indirizzo di caricamento del file eseguibile che corrisponde ai simboli nell'archivio simboli. **Note:**  È importante chiamare questo metodo quando si ottiene un oggetto `IDiaSession` e prima di iniziare utilizzando l'oggetto.|  
|[IDiaSession::get\_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Recupera un riferimento all'ambito globale.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Recupera un enumeratore per tutte le tabelle contenute nell'archivio simboli.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Recupera un enumeratore per tutti i simboli denominati le posizioni statiche.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Recupera tutti gli elementi figlio di un identificatore padre specificato che corrispondono al nome e il tipo del simbolo.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Recupera un tipo specifico di simboli che contiene, o è il più vicino a, un indirizzo specificato.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Recupera un tipo specifico di simboli che contiene, o è il più vicino a, un indirizzo virtuale relativo specificato \(RVA\).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Recupera un tipo specifico di simboli che contiene, o è il più vicino a, un indirizzo virtuale specificato \(VA\).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Recupera il simbolo che contiene un token di metadati specificato.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Verifica se due simboli sono equivalenti.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Recupera un simbolo dal relativo identificatore univoco.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Recupera un tipo specifico di simboli che contiene, o è il più vicino a, un indirizzo virtuale e un offset di specificati.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Recupera un tipo specifico di simboli che contiene, o è il più vicino a, un indirizzo virtuale e un offset specificati.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Recupera un file di origine da modulo e dal nome.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Recupera un file di origine dall'identificatore di file di origine.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Recupera i numeri di riga all'interno di un identificatore specificato di file di origine e del modulo.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Recupera le righe in un modulo specificato contenente un indirizzo specificato.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Recupera le righe in un modulo specificato contenente un indirizzo virtuale relativo specificato.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Cercare le informazioni sul numero di riga per le righe contenute in un intervallo di indirizzi specificato.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Recupera le righe in un modulo specificato dal file di origine e il numero di riga.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Recupera un database di origine inserito nell'archivio simboli dai provider di attributo o da altri componenti del processo di compilazione.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Recupera una sequenza enumerata di flussi di dati di debug.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Recupera un'enumerazione che consente a un client ripetere da tutti i frame inline in un indirizzo specificato.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Recupera un'enumerazione che consente a un client ripetere da tutti i frame inline in un indirizzo virtuale relativo specificato \(RVA\).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Recupera un'enumerazione che consente a un client ripetere da tutti i frame inline in un indirizzo virtuale specificato \(VA\).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, dal simbolo padre specificato.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, dal simbolo padre specificato e contenuta nell'intervallo di indirizzi specificato.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, dal simbolo padre specificato e che è contenuto all'interno dell'indirizzo virtuale relativo specificato \(RVA\).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, dal simbolo padre specificato e che è contenuto all'interno dell'indirizzo virtuale specificato \(VA\).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, nel file di origine e il numero di riga specificato.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni sul numero di riga di tutte le funzioni inline che corrispondono a un nome specificato.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Restituisce un'enumerazione dei simboli per la variabile che il valore specificato di tag corrisponde alla funzione padre stub dei tasti di scelta rapida.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Dato un valore corrispondente tag, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione padre specificata di uno stub di scelta rapida a un indirizzo virtuale relativo specificato.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Restituisce un'enumerazione di simboli per i frame inline che corrispondono al nome di funzione inline specificato.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Restituisce un'enumerazione di simboli per i frame inline che corrispondono alla posizione di origine specificata.|  
  
## Note  
 È importante chiamare il metodo [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) dopo aver creato l'oggetto `IDiaSession` e il valore passato al metodo `put_loadAddress` deve essere diverso da zero a per tutte le proprietà \(VA\) di indirizzo virtuale di simboli per consentire l'accesso.  L'indirizzo del caricamento avrà da qualsiasi programma caricato l'eseguibile che viene eseguito il debug.  Ad esempio, è possibile chiamare la funzione Win32 `GetModuleInformation` per recuperare l'indirizzo di caricamento dell'eseguibile, dato un handleeseguibile.  
  
## Esempio  
 In questo esempio viene illustrato come ottenere l'interfaccia `IDiaSession` come parte di un'inizializzazione generale di esaminare SDK.  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## Requisiti  
 Intestazione: Dia2.h  
  
 Raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Ricerche nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)