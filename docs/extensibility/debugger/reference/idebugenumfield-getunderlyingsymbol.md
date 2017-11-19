---
title: IDebugEnumField::GetUnderlyingSymbol | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords: IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fdfec41092d974be90f1b376089fa4a66c45c955
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Questo metodo restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il nome dell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppField`  
 [out] Restituisce il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive il nome di questa enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il nome dell'enumerazione contiene anche il tipo di enumerazione, che è associato a una posizione di memoria mediante [associare](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md)