---
title: "IDiaSectionContrib | Microsoft Docs"
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
  - "IDiaSectionContrib (interfaccia)"
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera i dati che descrivono un supporto della sezione, ovvero, un blocco di memoria contiguo contribuito all'immagine da un modulo.  
  
## Sintassi  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaSectionContrib`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaSectionContrib::get\_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Recupera un riferimento al simbolo del modulo che ha fornito in questa sezione.|  
|[IDiaSectionContrib::get\_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Recupera la parte della sezione dell'indirizzo del supporto.|  
|[IDiaSectionContrib::get\_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Recupera la parte offset dell'indirizzo del supporto.|  
|[IDiaSectionContrib::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|Recupera indirizzo \(RVA\) virtuale di immagine di supporto.|  
|[IDiaSectionContrib::get\_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Recupera indirizzo \(VA\) virtuale di supporto.|  
|[IDiaSectionContrib::get\_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Recupera il numero di byte in una sezione.|  
|[IDiaSectionContrib::get\_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Recupera un flag che indica se la sezione non può essere memoria insufficiente della riserva di paging.|  
|[IDiaSectionContrib::get\_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Recupera un flag che indica se la sezione non deve essere applicato il riempimento al limite seguente di memoria.|  
|[IDiaSectionContrib::get\_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|recupera un flag che indica se la sezione contiene il codice eseguibile.|  
|[IDiaSectionContrib::get\_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Recupera un flag che indica se la sezione contiene il codice a 16 bit.|  
|[IDiaSectionContrib::get\_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Recupera un flag che indica se la sezione contiene dati inizializzati.|  
|[IDiaSectionContrib::get\_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|Recupera un flag che indica se la sezione contiene i dati non inizializzate.|  
|[IDiaSectionContrib::get\_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Recupera un flag che indica se una sezione contiene commenti o le informazioni simili.|  
|[IDiaSectionContrib::get\_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Recupera un flag che indica se la sezione viene eliminata prima che venga prodotto a parte dell'immagine in memoria.|  
|[IDiaSectionContrib::get\_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|recupera un flag che indica se la sezione è un record di COMDAT.|  
|[IDiaSectionContrib::get\_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|recupera un flag che indica se la sezione può essere rimossa.|  
|[IDiaSectionContrib::get\_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Recupera un flag che indica se la sezione non può essere memorizzata nella cache.|  
|[IDiaSectionContrib::get\_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Recupera un flag che indica se la sezione può essere condivisa in memoria.|  
|[IDiaSectionContrib::get\_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|recupera un flag che indica se la sezione è eseguibile come codice.|  
|[IDiaSectionContrib::get\_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|recupera un flag che indica se la sezione può essere letta.|  
|[IDiaSectionContrib::get\_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Recupera un flag che indica se la sezione può essere scritta.|  
|[IDiaSectionContrib::get\_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Recupera il controllo su \(CRC\) ridondanza ciclica dei dati nella sezione.|  
|[IDiaSectionContrib::get\_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Recupera il CRC delle informazioni di rilocazione per la sezione.|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Recupera l'identificatore del modulo per la sezione.|  
  
## Note  
  
## Note per i chiamanti  
 Questa interfaccia è ottenuto chiamando [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) e  [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md) metodi.  vedere [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) interfaccia per un esempio di verifica  `IDiaSectionContrib` interfaccia.  
  
## Esempio  
 questa funzione mostra l'indirizzo di ogni sezione con tutti i simboli associati.  vedere [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) interfaccia per vedere come  `IDiaSectionContrib` l'interfaccia viene ottenuta.  
  
```cpp#  
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)  
{  
    if (pSecContrib != NULL && pSession != NULL)  
    {  
        DWORD rva;  
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )  
        {  
            printf( "\taddr: 0x%.8X", rva );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                        name != NULL ? name : L"",  
                        szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
        else  
        {  
            DWORD isect;  
            DWORD offset;  
            pSecContrib->get_addressSection( &isect );  
            pSecContrib->get_addressOffset( &offset );  
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( SUCCEEDED( psession->findSymbolByAddr(  
                                              isect,  
                                              offset,  
                                              SymTagNull,  
                                              &pSym )  
                          )  
               )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                    name != NULL ? name : L"",  
                    szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
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
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)