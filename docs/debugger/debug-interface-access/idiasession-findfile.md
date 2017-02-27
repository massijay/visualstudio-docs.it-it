---
title: "IDiaSession::findFile | Microsoft Docs"
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
  - "IDiaSession::findFile (metodo)"
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera i file di origine da modulo e dal nome.  
  
## Sintassi  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### Parametri  
 `pCompiland`  
 \[in\] un oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il modulo da utilizzare come contesto per la ricerca.  Impostare questo parametro su `NULL` trovare i file di origine in tutti i moduli.  
  
 `name`  
 \[in\] specifica il nome del file di origine da recuperare.  Impostare questo parametro su `NULL` per tutti i file di origine vengano recuperati.  
  
 `option`  
 \[in\] specifica le opzioni di confronto applicate per denominare la ricerca.  I valori dall'enumerazione [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) possono essere utilizzati da solo o in combinazione.  
  
 `ppResult`  
 \[out\] restituisce un oggetto [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) contenente un elenco di file di origine recuperati.  
  
## Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## Esempio  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## Vedere anche  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)