---
title: IDiaEnumSegments::get__NewEnum | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSegments::get__NewEnum method
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0a6d5bb8ccf491b2492d8152b56305781dd082b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsegmentsgetnewenum"></a>IDiaEnumSegments::get__NewEnum
Recupera il <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione di questo enumeratore.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce il `IUnknown` interfaccia che rappresenta il <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione di questo enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)