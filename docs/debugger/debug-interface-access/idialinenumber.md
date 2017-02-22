---
title: "IDiaLineNumber | Microsoft Docs"
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
  - "IDiaLineNumber (interfaccia)"
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLineNumber
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Accede alle informazioni che descrivono il processo di mapping da un blocco di byte di testo immagine a un numero di riga del file di origine.  
  
## Sintassi  
  
```  
IDiaLineNumber : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaLineNumber`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaLineNumber::get\_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|Recupera un riferimento al simbolo per il modulo che ha fornito i byte del testo di immagine.|  
|[IDiaLineNumber::get\_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)|Recupera un riferimento all'oggetto del file di origine.|  
|[IDiaLineNumber::get\_lineNumber](../../debugger/debug-interface-access/idialinenumber-get-linenumber.md)|Recupera il numero di riga nel file di origine.|  
|[IDiaLineNumber::get\_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|Recupera il numero di riga di origine in base uno in cui l'istruzione o l'espressione termina.|  
|[IDiaLineNumber::get\_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|Recupera il numero di colonne in cui l'espressione o l'istruzione verrà avviato.|  
|[IDiaLineNumber::get\_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|Recupera il numero di colonne in cui l'espressione o un'istruzione termina.|  
|[IDiaLineNumber::get\_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|Recupera la parte della sezione indirizzo di memoria in cui un blocco avvia.|  
|[IDiaLineNumber::get\_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|Recupera la parte dell'offset indirizzo di memoria in cui un blocco avvia.|  
|[IDiaLineNumber::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|Recupera indirizzo \(RVA\) virtuale di immagine di un blocco.|  
|[IDiaLineNumber::get\_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|Recupera indirizzo \(VA\) virtuale di un blocco.|  
|[IDiaLineNumber::get\_length](../../debugger/debug-interface-access/idialinenumber-get-length.md)|Recupera il numero di byte in un blocco.|  
|[IDiaLineNumber::get\_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|Recupera un identificatore di file di origine univoco per il file di origine che ha contribuito questa riga.|  
|[IDiaLineNumber::get\_statement](../../debugger/debug-interface-access/idialinenumber-get-statement.md)|Recupera un flag che indica che queste informazioni sulla riga descrivono l'inizio di un'istruzione nell'origine del programma.|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Recupera l'identificatore univoco per il modulo che ha contribuito questa riga.|  
  
## Note  
  
## Note per i chiamanti  
 Leggi questa interfaccia chiamando [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) o  [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) metodi.  
  
## Esempio  
 La funzione seguente per visualizzare i numeri di riga utilizzati in una funzione \(rappresentata da `pSymbol`\).  
  
```cpp#  
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )  
{  
    ULONGLONG length = 0;  
    DWORD     isect  = 0;  
    DWORD     offset = 0;  
  
    pSymbol->get_addressSection( &isect );  
    pSymbol->get_addressOffset( &offset );  
    pSymbol->get_length( &length );  
    if ( isect != 0 && length > 0 )  
    {  
        CComPtr< IDiaEnumLineNumbers > pLines;  
        if ( SUCCEEDED( pSession->findLinesByAddr(  
                                      isect,  
                                      offset,  
                                      static_cast<DWORD>( length ),  
                                      &pLines)  
                      )  
           )  
        {  
            CComPtr< IDiaLineNumber > pLine;  
            DWORD celt      = 0;  
            bool  firstLine = true;  
  
            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&  
                    celt == 1 )  
            {  
                DWORD offset;  
                DWORD seg;  
                DWORD linenum;  
                CComPtr< IDiaSymbol >     pComp;  
                CComPtr< IDiaSourceFile > pSrc;  
  
                pLine->get_compiland( &pComp );  
                pLine->get_sourceFile( &pSrc );  
                pLine->get_addressSection( &seg );  
                pLine->get_addressOffset( &offset );  
                pLine->get_lineNumber( &linenum );  
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );  
                pLine = NULL;  
                if ( firstLine )  
                {  
                    // sanity check  
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;  
                    if ( SUCCEEDED( pSession->findLinesByLinenum(  
                                                  pComp,  
                                                  pSrc,  
                                                  linenum,  
                                                  0,  
                                                  &pLinesByLineNum)  
                                  )  
                       )  
                    {  
                        CComPtr< IDiaLineNumber > pLine;  
                        DWORD celt;  
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&  
                                celt == 1 )  
                        {  
                            DWORD offset;  
                            DWORD seg;  
                            DWORD linenum;  
  
                            pLine->get_addressSection( &seg );  
                            pLine->get_addressOffset( &offset );  
                            pLine->get_lineNumber( &linenum );  
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );  
                            pLine = NULL;  
                       }  
                    }  
                    firstLine = false;  
                }  
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
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)   
 [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)