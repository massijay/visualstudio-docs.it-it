---
title: IDiaSession::findInlineeLinesByRVA | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5210616573d2d1e0248c189095c8f10e192eab80
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Recupera un'enumerazione che consente a un client scorrere le informazioni di numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo padre specificato e è contenuta all'interno di indirizzo virtuale relativo specificato (RVA).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findInlineeLinesByRVA (   
   IDiaSymbol*           parent,  
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `parent`  
 [in] Un `IDiaSymbol` oggetto che rappresenta l'elemento padre.  
  
 `rva`  
 [in] Specifica l'indirizzo come un RVA.  
  
 `length`  
 [in] Specifica l'intervallo di indirizzi, in numero di byte, per coprire la query.  
  
 `ppResult`  
 [out] Contiene un `IDiaEnumLineNumbers` oggetto che contiene l'elenco di numeri di riga recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)