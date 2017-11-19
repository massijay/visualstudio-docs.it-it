---
title: IDiaSession::findInlineeLinesByAddr | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f93d9d04f83b2f23a3ae4e84e60b2b397bbd0c42
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Recupera un'enumerazione che consente a un client scorrere le informazioni di numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo padre specificato e è contenuta all'interno dell'intervallo di indirizzi specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `parent`  
 [in] Un `IDiaSymbol` oggetto che rappresenta l'elemento padre.  
  
 `isect`  
 [in] Specifica il componente di sezione dell'indirizzo.  
  
 `offset`  
 [in] Specifica il componente di offset dell'indirizzo.  
  
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