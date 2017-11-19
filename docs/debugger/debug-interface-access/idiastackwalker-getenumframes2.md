---
title: IDiaStackWalker::getEnumFrames2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fac3dc85542ecf5f86eb40be111533ee5e5a4211
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Recupera un enumeratore di frame dello stack per un tipo di piattaforma specifica.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cpuid`  
 [in] Un valore di [CV_CPU_TYPE_e (enumerazione)](../../debugger/debug-interface-access/cv-cpu-type-e.md) enumerazione che specifica il tipo di piattaforma.  
  
 `pHelper`  
 [in] L'helper [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) oggetto.  
  
 `ppEnum`  
 [out] Restituisce un [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) oggetto contenente un elenco di [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) oggetti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Per ottenere un elenco di frame dello stack per appena x86 piattaforma, chiamare il [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV_CPU_TYPE_e (enumerazione)](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)