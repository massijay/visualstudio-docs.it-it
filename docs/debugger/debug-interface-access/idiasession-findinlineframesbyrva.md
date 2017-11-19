---
title: IDiaSession::findInlineFramesByRVA | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2fedaeed12ddc818bd3260cb46b0ef88a95ef24
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineframesbyrva"></a>IDiaSession::findInlineFramesByRVA
Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un indirizzo virtuale relativo specificato (RVA).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findInlineFramesByRVA (   
   IDiaSymbol*       parent,   DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `parent`  
 [in] Un `IDiaSymbol` oggetto che rappresenta l'elemento padre.  
  
 `rva`  
 [in] Specifica l'indirizzo come un RVA.  
  
 `ppResult`  
 [out] Contiene un `IDiaEnumSymbols` oggetto che contiene l'elenco di frame che vengono recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)