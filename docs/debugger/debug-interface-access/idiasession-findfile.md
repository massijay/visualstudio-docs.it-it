---
title: IDiaSession::findFile | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef230d1b82992f769011e0cb1d9d4ff11145b82d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Recupera i file di origine dal modulo e il nome.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCompiland`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il modulo da utilizzare come contesto per la ricerca. Impostare questo parametro su `NULL` per trovare i file di origine in tutti i moduli.  
  
 `name`  
 [in] Specifica il nome del file di origine da recuperare. Impostare questo parametro su `NULL` per tutti i file di origine da recuperare.  
  
 `option`  
 [in] Specifica le opzioni di confronto applicate alla ricerca di nome. I valori di [NameSearchOptions (enumerazione)](../../debugger/debug-interface-access/namesearchoptions.md) enumerazione può essere utilizzato da solo o in combinazione.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) recuperare l'oggetto che contiene un elenco dei file di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions (enumerazione)](../../debugger/debug-interface-access/namesearchoptions.md)