---
title: IDebugObject::SetReferenceValue | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::SetReferenceValue
helpviewer_keywords: IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e001e747279ad64c97c500079adc9c4574d1d33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Imposta il valore di riferimento di questo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pObject`  
 [in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto che rappresenta il nuovo valore di riferimento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo rende questa [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) un riferimento al valore dell'oggetto specificato nell'oggetto di `pObject` parametro, generando un'eccezione qualsiasi riferimento precedente. Si noti che questo `IDebugObject` oggetto deve essere già un tipo di riferimento.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)