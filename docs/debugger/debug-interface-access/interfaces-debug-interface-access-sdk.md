---
title: "Interfacce (Debug Interface Access SDK) | Microsoft Docs"
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
  - "interfacce [DIA SDK]"
  - "DIA SDK, interfacce"
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Interfacce (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

I metodi sono elencati in ordine alfabetico in ogni interfaccia nel sommario e nella pagina dell'interfaccia nell'ordine di Riferimento.  
  
## In questa sezione  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Fornisce il controllo su come il DIA SDK calcola gli indirizzi virtuali virtuali e relativi per gli oggetti di debug.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Gli avviati l'accesso a un database di origine di simboli di debug.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Fornisce l'accesso ai record in un flusso di dati di debug.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Enumera i diversi flussi di debug contenuti nell'origine dati.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Enumera i vari elementi dati del frame contenuti nell'origine dati.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Enumerare vari database di origine inseriti contenuti nell'origine dati.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Enumera i vari numeri di riga contenuti nell'origine dati.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Enumera i vari contributi della sezione contenuti nell'origine dati.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Enumera i vari segmenti contenuti nell'origine dati.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Enumera i vari file di origine contenuti nell'origine dati.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Enumera i vari stack frame disponibili.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Enumera i vari simboli contenuti nell'origine dati.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Enumera l'indirizzo che i vari simboli contenuto nell'origine dati.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Enumera le diverse tabelle contenute nell'origine dati.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 espone i dettagli di uno stack frame.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Espone i dettagli relativi agli offset di base di memoria e sulla posizione del modulo o dell'immagine.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 L'accesso al codice sorgente del programma archiviato nell'origine dati di diametro.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Accede alle informazioni che descrivono il processo di mapping da un blocco di byte di testo immagine a un numero di riga del file di origine.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Riceve i callback dal simbolo di diametro che individua la routine, quindi abilitando un'interfaccia utente per segnalare lo stato di avanzamento del tentativo di posizione.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Riceve i callback dal simbolo di diametro che individua la routine, consentendo le restrizioni per imporre al processo un'eccezione.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Consente di leggere le proprietà permanente di un set di proprietà di diametro.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Consente a un'applicazione client fornire i byte di un file eseguibile come specificato dalla posizione del file.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Consente a un'applicazione client fornire i byte di un file eseguibile come specificato da un indirizzo virtuale relativo.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Recupera i dati che descrivono un supporto della sezione, ovvero, un blocco di memoria contiguo contribuito all'immagine da un modulo.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Dati di mapping del numero di sezione ai segmenti di spazio degli indirizzi.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 fornisce un contesto di query per i simboli di debug.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 rappresenta un file di origine.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 espone le proprietà di uno stack frame.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Fornisce metodi per fare un percorso chiamate nello stack utilizzando il file PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Gestisce il contesto dello stack tra le chiamate di [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) metodo.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Facilitates che verifica il percorso chiamate nello stack utilizzando il file di database di debug del programma \(PDB\).  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Vengono descritte le proprietà di un'istanza del simbolo.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Enumera una tabella di origine dati di diametro.  
  
## Sezioni correlate  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Vengono descritte le enumerazioni e le strutture utilizzate da varie interfacce di DIA SDK.  
  
 [Costanti \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Vengono descritte le costanti disponibili nel DIA SDK.  
  
## Vedere anche  
 [Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)