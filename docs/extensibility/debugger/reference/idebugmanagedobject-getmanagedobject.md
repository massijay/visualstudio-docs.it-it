---
title: IDebugManagedObject::GetManagedObject | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugManagedObject::GetManagedObject
helpviewer_keywords: IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cedcd5801d37256bcb419f4b4e6fb5317f0aedbf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Restituisce un'interfaccia che rappresenta l'oggetto gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppManagedObject`  
 [out] Restituisce un'interfaccia che rappresenta l'oggetto gestito.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'interfaccia restituita da questo metodo è possibile eseguire query per qualsiasi interfaccia implementata dalla classe gestita, che consente di chiamare i relativi metodi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)