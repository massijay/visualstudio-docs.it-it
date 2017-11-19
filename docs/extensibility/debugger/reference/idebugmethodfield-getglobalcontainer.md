---
title: IDebugMethodField::GetGlobalContainer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::GetGlobalContainer
helpviewer_keywords: IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ffeb7c7c1abe6e5a816c2d7a67ad6820e0921bc8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Ottiene il contenitore globale del metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppClass`  
 [out] Restituisce un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che rappresenta il modulo in cui è definito questo metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'oggetto restituito [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto rappresenta l'intero modulo e un oggetto artificiale, vale a dire, il modulo stesso non dispone di una classe effettiva ma può essere rappresentato da un `IDebugClassField` oggetto, che consente le varie elementi del modulo da essere enumerati e individuati.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)