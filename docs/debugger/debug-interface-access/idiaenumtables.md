---
title: "IDiaEnumTables | Microsoft Docs"
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
  - "IDiaEnumTables (interfaccia)"
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enumera le diverse tabelle contenute nell'origine dati.  
  
## Sintassi  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaEnumTables`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaEnumTables::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|recupera [interfaccia di IEnumVARIANT](http://msdn.microsoft.com/it-it/139e3c93-faef-4003-9079-e0e94494db3e) versione di questo enumeratore.|  
|[IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Recupera il numero di tabelle.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Recupera una tabella per l'utilizzo di un indice o di un nome.|  
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Recupera un numero specificato delle tabelle nella sequenza di enumerazione.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Ignora un numero specificato delle tabelle in una sequenza di enumerazione.|  
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
  
## Note  
  
## Note per i chiamanti  
 Leggi questa interfaccia chiamando [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) metodo.  
  
## Esempio  
 In questo esempio viene illustrato come ottenere `IDiaEnumTables` interfaccia da una sessione.  Per un esempio più completo delle tabelle tramite, vedere [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interfaccia.  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)