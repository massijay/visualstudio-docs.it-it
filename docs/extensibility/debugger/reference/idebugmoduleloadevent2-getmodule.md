---
title: IDebugModuleLoadEvent2::GetModule | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModuleLoadEvent2::GetModule
helpviewer_keywords: IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4bd5ebf74bb3818aff06e01b7c6d181760510f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Ottiene il modulo che viene caricato o scaricato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pModule`  
 [out] Restituisce un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) oggetto che rappresenta il modulo durante il caricamento o scaricamento.  
  
 `pbstrDebugMessage`  
 [in, out] Restituisce un messaggio facoltativo che descrive l'evento. Se questo parametro è un valore null, non è richiesto alcun messaggio.  
  
 `pbLoad`  
 [in, out] Diverso da zero (`TRUE`) se il modulo è il caricamento e zero (`FALSE`) se il modulo di scaricamento. Se questo parametro è un valore null, non è richiesto alcun lo stato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)